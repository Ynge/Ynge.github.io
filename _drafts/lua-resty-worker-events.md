---
layout: post
title: lua-resty-worker-events学习(一)
categories: [openresty,Lua,后端,网关]
description: 文档翻译
keywords: Lua, events
---

## [lua-resty-worker-events](https://github.com/Kong/lua-resty-worker-events)

> **Nginx工作进程的进程间事件**

### 概要

```Lua
http {
    lua_package_path "/path/to/lua-resty-worker-events/lib/?.lua;;";

    # the size depends on the number of event to handle:
    lua_shared_dict process_events 1m;

    init_worker_by_lua_block {
        local ev = require "resty.worker.events"

        local handler = function(data, event, source, pid)
            print("received event; source=",source,
                  ", event=",event,
                  ", data=", tostring(data),
                  ", from process ",pid)
        end

        ev.register(handler)

        local ok, err = ev.configure {
            shm = "process_events", -- defined by "lua_shared_dict"
            timeout = 2,            -- life time of unique event data in shm
            interval = 1,           -- poll interval (seconds)

            wait_interval = 0.010,  -- wait before retry fetching event data
            wait_max = 0.5,         -- max wait time before discarding event
            shm_retries = 999,      -- retries for shm fragmentation (no memory)
        }
        if not ok then
            ngx.log(ngx.ERR, "failed to start event system: ", err)
            return
        end
    }

    server {
        ...

        # example for polling:
        location = /some/path {

            default_type text/plain;
            content_by_lua_block {
                -- manually call `poll` to stay up to date, can be used instead,
                -- or together with the timer interval. Polling is efficient,
                -- so if staying up-to-date is important, this is preferred.
                require("resty.worker.events").poll()

                -- do regular stuff here

            }
        }
    }
}
```

### 描述

这个模块提供一种在nginx服务器中向nginx工作进程发送事件的途径。通信过程是通过共享内存的方式实现，事件数据是存放在共享内存中。

可以保证所有工作进程中的事件顺序是相同的。

工作进程将设置一个计时器，在后台检查事件。该模块遵循单例模式，因此每个工作进程只运行一次。如果保持最新状态很重要，则可以将间隔(interval)设置为较小的频率，并且对收到的每个请求进行轮询以确保尽快处理所有内容。

