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


![image](https://user-images.githubusercontent.com/39460149/107839596-d9918e00-6de7-11eb-8cfe-9536722aa367.png)


# tree

power shell 的tree命令实现  
tree 命令格式和参数：  
TREE [drive:][path] [/F] [/A]  
/F 显示每个文件夹中文件的名称。（带扩展名）  
/A 使用 ASCII 字符，而不使用扩展字符。(如果要显示中文，例如 tree /f /A >tree.txt)  

或者用git bash 工具 使用tree命令  
安装Tree for Windows工具：  
打开进入 [Tree for Windows](http://gnuwin32.sourceforge.net/packages/tree.htm) 页面，选择下载 Binaries zip 文件。  
解压压缩包，找到压缩包内的 bin 目录，将 bin 目录下的 tree.exe 复制  
找到 C:\\Program Files\Git\usr\bin 目录，将 tree.exe 粘贴到该目录下，安装即完成  
