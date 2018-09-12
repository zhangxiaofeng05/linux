## linux终端命令

如果英语比较好，可以查看man文档  

|命令|解释|
|------|-----|
|Ctrl+p|相当于↑，上一个终端命令|
|Ctrl+n|相当于↓，下一个终端命令|
|date|查看日期|
|history|用户使用终端的命令记录|
|Ctrl+b|光标向左移一个|
|Ctrl+f|光标向后移一个|
|Ctrl+a|光标跳到最左边|
|Ctrl+e|光标跳到最右边|
|Ctrl+h|删除光标前边的一个字符|
|Ctrl+d|删除光标后边的一个字符|
|Ctrl+u|删除光标前边所有|
|Ctrl+l|清屏或者clear|    


>敲命令按一次Tab可补全(唯一)路径  
二次会给出有歧义的命令  

|命令|解释|
|-------|-----|
|.|当前目录|
|..|当前的上一个目录|
|cd -|返回临近的目录，就是从一个目录刚切换到当前目录，使用命令就切换回去了|
|pwd|查看当前目录所在位置|
|cd|什么也不加，直接返回家目录，相当于`cd ~`|
|tree|展示树状结构`sudo apt-get install tree`|
|tree git|展示git的目录|
|ls|展示当前目录下的文件|
|ls -l|展示文件类型、文件所有者、文件的硬链接数、文件创建或修改的时间、文件名|
|ls -la|查看所有的(包括隐藏的)|   

> r---read  
  w---write  
  x---执行  
  
|命令|解释|
|------|-----| 
|mkdir <文件名>|创建目录|
|mkdir <文件名>/<文件名> - p|创建嵌套目录,`-p是参数，放在文件名前边也可以`|
|rmdir aa|删除aa这个空目录|
|rm aa -r|删除aa这个目录(不会放到回收站),`-r 是参数，递归删除`|
|rm -ri aa|会给出提示(递归删除)|
|touch aa|若aa存在，修改时间，不存在就创建|
|cp hello.c temp|把hello.c复制到temp目录下|
|cat <文件名>|查看文件内容|
|cp dir1 dir2 -r|把dir1目录复制到dir2目录下|
|mv name1 name2|把name1改成name2(改名)|
|df -h|查看磁盘的使用量|
|which ls|查看ls命令的所在目录，有时候查看系统是否安装一个软件，用此命令|
|chmod 权限 文件名|更改文件的权限|  

> -:没有权限
  r:4    -------阅读权限  
  w:2    -------写权限  
  x:1    -------执行权限  
  765  
  7------rwx---文件所有者  
  6------rw---文件所属组  
  5------rx---其他人  
  eg：chmod 777 temp  
 
|命令|解释|
|------|-----|
|sudo chown zhangsan temp|把temp的所有者改成zhangsan|
|sudo chown luffy:lisi temp|改变所有者、所属组|
|sudo chgrp itcast temp|改变所属组|

## 查找

    find + 查找目录 + -name + "文件名字"
    “hello*”通配符所有的
    "hello？"通配符一个字符
    find + 查找目录 + -size + +10k      大于10k
    find + 查找目录 + -size + -10k      小于10k
    find + 查找目录 + -size + +10M -size -100M     查找大于10M且小于100M
    find + 查找目录 + -type + 类型名
    
    普通文件[f]
    目录[d]
    链接符号[l]
    块设备[b]
    字符设备[c]
    socket文件[s]
    管道[p]
    eg:find ~ -type p
    mkfifi aa   创建管道  
    按文件内容查找:
    grep -r "查找内容" + 查找路径
    eg:grep -r stdio linux/
    
    
## 安装软件

    在线安装: sudo apt-get install tree       tree为软件名  
    移除: sudo apt-get remove tree  
    更新: sudo apt-get update                 --更新软件列表 
    清理所有软件安装包: sudo apt-get clean  
    ---实际清理的是/var/cache/apt/archives目录下的.deb文件  
    
    deb包离线安装  
    安装: sudo dpkg -i xxx.deb  
    删除: sudo dpkg -r xxx  
    
## 挂载  

     sudo fdisk -l      查看磁盘分区  
     sudo mount /dev/sdb1 /mnt  
     sudo unmount /mnt  

## 压缩  

    .tar
    
