# centos 清理空间  


查看整体的空间使用情况   
df -h   


查看根目录下各目录占用的空间   
du -sh /* | sort -nr   


查看二级目录下子目录和文件的占用空间   
du -sh /opt/* | sort -nr  

 
查看当前目录下的所有文件夹的使用情况  
du -h --max-depth=1  

