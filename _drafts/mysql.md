---
layout: post
title: mysql批量修改字段
categories: [后端,mysql]
description: mysql
keywords: mysql
---
//去掉字段中的
//空格
//char(9) 水平制表符
//char(10)   换行
//char(13)   回车
UPDATE b_project_subsection_content  SET  code  = REPLACE(REPLACE(REPLACE(REPLACE(code, CHAR(10), ''), CHAR(13), ''), CHAR(9), ''),' ','')
//批量修改字段
SELECT CONCAT('alter table ',TABLE_NAME,' modify ',COLUMN_NAME,' varchar(100) ;')
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_SCHEMA='pcbs' AND COLUMN_NAME IN ('create_by','update_by') and column_type <> 'varchar(100)'
