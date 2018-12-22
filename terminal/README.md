## linux终端命令

`如果英语比较好，可以查看man文档`  

 - 我的总结比较差，但是舍不得删  
 附上别人总结比较全的  
 https://github.com/jaywcjlove/linux-command  

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

    .tar-------------------------------基于gzip和bzip2的一个压缩  
    c---创建---压缩  
    x---释放---解压缩  
    v---显示提示信息---压缩解压缩---可以省略  
    f---指定压缩文件的名字  
    z---使用gzip的方式压缩文件--- .gz  
    j---使用bzip2的方式压缩文件--- .bzip2  
    压缩：  
    tar zcvf 生成的压缩包的名字(xxx.tar.gz) 要压缩的文件或目录
    tar jcvf 生成的压缩包的名字(xxx.tar.bz2) 要压缩的文件或目录
    eg:
    tar zcvf alltxt.tar.gz *.txt
    tar jcvf animal.tar.bz2 animal/*.txt
    解压缩:
    tar zxvf 压缩包名字 目录  -------------目录不写则解压到当前目录
    eg:  
    tar zxvf alltxt.tar.gz
    tar jxvf animal.tar.bz2 -C test/  
    
    .rar   ------------必须手动安装该软件
    安装: sudo apt-get install rar
    参数:
       压缩: a
       解压缩: x
    rar a 生成的压缩文件的名字(temp) 压缩的文件或目录 ------------压缩的名字不用加.rar,自动加  
    eg: rar a animal animal
    解压缩：  
    rar x 压缩文件名 解压目录
    eg: rar x all.rar----------后边应该写解压到的目录，不写则解压到当前目录
    
    .zip
    压缩:
        zip 压缩包的名字 压缩的文件或目录
    解压:  
        unzip 压缩包的名字
        unzip 压缩包的名字 -d 解压目录
    压缩目录: zip -r animal animal  
    
## 用户    

    添加用户: sudo adduser baozheng
    切换用户: su baozheng
    添加用户组: sudo groupadd Robin
    修改密码: sudo passwd Robin
    修改当前用户密码: passwd
    修改root密码: sudo passwd
    
## 其他
    
    ps a       ------列出当前用户信息
    ps au
    ps aux     ------查看没有终端的应用程序
    有终端与用户进行交互
    管道 指令1 | 指令2
    指令1的输出作为指令2的输入
    指令2处理完毕，将信息输出到屏幕
    eg:
      ps aux | grep bash
      显示的最后一个结果不要，是grep占用的进程
      
    进程: kill -l 查看
    杀死进程: kill -9 5286   --------5286是进程号
    top ---- 查看任务管理器
    查看本机ip: ifconfig
    测试主机间通信: ping ip
    ping ip -c 4
    4 ---- 代表只发送4条
    查看域名的ip: nslookup www.baidu.com
    
    修改文件名: mv 原文件名 新文件名

## 为什么写这个

    之前看了bilibili的视频，后来作者删了，这是我的记的笔记！
