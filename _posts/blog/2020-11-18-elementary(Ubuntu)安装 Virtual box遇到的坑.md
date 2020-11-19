---
layout: post
title: elementary(ubuntu)安装virtual box 
categories: [虚拟机]
description: 安装virtual box
keywords: 虚拟机,linux 
---
elementary(Ubuntu)安装 Virtual box遇到的坑

<a name="JXUk9"></a>
## 安装软件
```shell
sudo apt install virtualbox 
sudo apt install virtualbox-dkms
```
<a name="Fgdik"></a>
## 启动软件创建虚拟机
发现报错
```
The VirtualBox Linux kernel driver is either not loaded or not set up correctly. Please reinstall virtualbox-dkms package and load the kernel module by executing

'modprobe vboxdrv'

as root.

If your system has EFI Secure Boot enabled you may also need to sign the kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load them. Please see your Linux system's documentation for more information.

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.
```
![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/adbcb46727f2014a331a2da8f86a20dd-1605712800474.png)<br />按照提示重装dkms
```shell
sudo apt  --reinstall install virtualbox-dkms
```

<br />执行后终端显示如下<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/acf7102666b7ee2a2c38128c54e81522-1605712800408.png)<br />确定后,进入输入密码界面,输入secure boot 密码(忘记的话把常用密码都试一下)<br />然后提示DKMS: install completed.<br />再次尝试重启虚拟机,还是报相同的错误<br />执行提示的命令`sudo modprobe vboxdrv`<br />提示`modprobe: ERROR: could not insert 'vboxdrv': Operation not permitted`<br />重启系统`reboot`<br />然后会进入一个从没见过的界面，一次按下面选择的确认，倒数第二步输入secure boot 密码，最后重启<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/18f7653b65a68fe1f9ef23b999efb2e2-1605712803445.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/ac33444ed589b0cf0d9a125c1bda02bd-1605712799924.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/fd2917156ad5bbdf877aed9199acea00-1605712800266.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/aa2b0eefc1e70372640a2f98306f3ddc-1605712800207.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/896bd6681b603fba62e316eed8d90c76-1605712800251.png)<br />之后遇到另一个问题<br />新建linux虚拟机，发现只能选择32位系统,这是由于没有开启CPU虚拟化技术，需要进入bois开启，具体步骤不再赘述。<br />最后终于可以正常新建虚拟机。<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/9e1fe30a78e7eba0acadb95c820fbdf0-1605712804581.png)<br />参考:<br />[https://blog.csdn.net/liangjiu2009/article/details/72056947](https://blog.csdn.net/liangjiu2009/article/details/72056947)<br />[https://blog.csdn.net/yongf2014/article/details/49282333](https://blog.csdn.net/yongf2014/article/details/49282333)
---
layout: post
title: template page
categories: [cate1, cate2]
description: some word here
keywords: keyword1, keyword2
---
elementary(Ubuntu)安装 Virtual box遇到的坑

<a name="JXUk9"></a>
## 安装软件
```shell
sudo apt install virtualbox 
sudo apt install virtualbox-dkms
```
<a name="Fgdik"></a>
## 启动软件创建虚拟机
发现报错
```
The VirtualBox Linux kernel driver is either not loaded or not set up correctly. Please reinstall virtualbox-dkms package and load the kernel module by executing

'modprobe vboxdrv'

as root.

If your system has EFI Secure Boot enabled you may also need to sign the kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load them. Please see your Linux system's documentation for more information.

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.
```
![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/adbcb46727f2014a331a2da8f86a20dd-1605712800474.png)<br />按照提示重装dkms
```shell
sudo apt  --reinstall install virtualbox-dkms
```

<br />执行后终端显示如下<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/acf7102666b7ee2a2c38128c54e81522-1605712800408.png)<br />确定后,进入输入密码界面,输入secure boot 密码(忘记的话把常用密码都试一下)<br />然后提示DKMS: install completed.<br />再次尝试重启虚拟机,还是报相同的错误<br />执行提示的命令`sudo modprobe vboxdrv`<br />提示`modprobe: ERROR: could not insert 'vboxdrv': Operation not permitted`<br />重启系统`reboot`<br />然后会进入一个从没见过的界面，一次按下面选择的确认，倒数第二步输入secure boot 密码，最后重启<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/18f7653b65a68fe1f9ef23b999efb2e2-1605712803445.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/ac33444ed589b0cf0d9a125c1bda02bd-1605712799924.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/fd2917156ad5bbdf877aed9199acea00-1605712800266.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/aa2b0eefc1e70372640a2f98306f3ddc-1605712800207.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/896bd6681b603fba62e316eed8d90c76-1605712800251.png)<br />之后遇到另一个问题<br />新建linux虚拟机，发现只能选择32位系统,这是由于没有开启CPU虚拟化技术，需要进入bois开启，具体步骤不再赘述。<br />最后终于可以正常新建虚拟机。<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/9e1fe30a78e7eba0acadb95c820fbdf0-1605712804581.png)<br />参考:<br />[https://blog.csdn.net/liangjiu2009/article/details/72056947](https://blog.csdn.net/liangjiu2009/article/details/72056947)<br />[https://blog.csdn.net/yongf2014/article/details/49282333](https://blog.csdn.net/yongf2014/article/details/49282333)
---
layout: post
title: template page
categories: [cate1, cate2]
description: some word here
keywords: keyword1, keyword2
---
elementary(Ubuntu)安装 Virtual box遇到的坑

<a name="JXUk9"></a>
## 安装软件
```shell
sudo apt install virtualbox 
sudo apt install virtualbox-dkms
```
<a name="Fgdik"></a>
## 启动软件创建虚拟机
发现报错
```
The VirtualBox Linux kernel driver is either not loaded or not set up correctly. Please reinstall virtualbox-dkms package and load the kernel module by executing

'modprobe vboxdrv'

as root.

If your system has EFI Secure Boot enabled you may also need to sign the kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load them. Please see your Linux system's documentation for more information.

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.
```
![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/adbcb46727f2014a331a2da8f86a20dd-1605712800474.png)<br />按照提示重装dkms
```shell
sudo apt  --reinstall install virtualbox-dkms
```

<br />执行后终端显示如下<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/acf7102666b7ee2a2c38128c54e81522-1605712800408.png)<br />确定后,进入输入密码界面,输入secure boot 密码(忘记的话把常用密码都试一下)<br />然后提示DKMS: install completed.<br />再次尝试重启虚拟机,还是报相同的错误<br />执行提示的命令`sudo modprobe vboxdrv`<br />提示`modprobe: ERROR: could not insert 'vboxdrv': Operation not permitted`<br />重启系统`reboot`<br />然后会进入一个从没见过的界面，一次按下面选择的确认，倒数第二步输入secure boot 密码，最后重启<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/18f7653b65a68fe1f9ef23b999efb2e2-1605712803445.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/ac33444ed589b0cf0d9a125c1bda02bd-1605712799924.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/fd2917156ad5bbdf877aed9199acea00-1605712800266.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/aa2b0eefc1e70372640a2f98306f3ddc-1605712800207.png)<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/896bd6681b603fba62e316eed8d90c76-1605712800251.png)<br />之后遇到另一个问题<br />新建linux虚拟机，发现只能选择32位系统,这是由于没有开启CPU虚拟化技术，需要进入bois开启，具体步骤不再赘述。<br />最后终于可以正常新建虚拟机。<br />![image.png](https://raw.githubusercontent.com/Ynge/imageDb/main/xsj/9e1fe30a78e7eba0acadb95c820fbdf0-1605712804581.png)<br />参考:<br />[https://blog.csdn.net/liangjiu2009/article/details/72056947](https://blog.csdn.net/liangjiu2009/article/details/72056947)<br />[https://blog.csdn.net/yongf2014/article/details/49282333](https://blog.csdn.net/yongf2014/article/details/49282333)