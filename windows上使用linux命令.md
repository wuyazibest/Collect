[DOS 和 Linux 常用命令的对比](https://www.huihoo.org/gnu_linux/ch-doslinux.html)

# windows dir改成ls
习惯了linux下的ls命令，windows的dir用的很不习惯，又不想装cygwin, bash，就想把dir重命名为ls，发现dos下有个命令doskey可以完成该功能。
在命令提示符下敲:
```shell
>doskey ls=dir
```
doskey 只能临时修改  关闭窗口命令即生效

# 创建bat文件 永久有效：
## 实现  ls = dir
新建 ls.bat 文件 放到 C:\Windows 下
内容为 
```shell
@echo off
dir
```
即可

同样可实现
clear = cls 等
