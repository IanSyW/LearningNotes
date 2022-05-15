# Ubuntu

## 操作系统

### 概论

- 功能

1. 直接操纵硬件
2. 提供系统调用
3. 终端命令



- 分类

1. 桌面操作系统 （Windows、MacOS、Linux）
2. 服务器操作系统（Linux、Windows server）
3. 嵌入式操作系统（Linux）
4. 移动设备操作系统（iOS、Android ）



- Linux发行版（GNU）

1. Ubuntu、CentOS。。

> 包含了桌面环境、办公套件等应用软件和Linux内核

### 目录和内容

Linux 多用户 / -> /home -> /iansy 无盘符

Windows 单用户 盘符

## 命令

### 基本命令

ctrl shift = 放大终端字体

ctrl - 缩小终端字体

``` 
ls  # 查看当前文件夹下的内容

pwd  # 查看当前所在的文件夹

cd  # 切换文件夹

touch  # 新建文件

mkdir  # 创建目录

rm  # 删除文件

clear  # 清屏

tab  # 自动补全 （两下显示所有）
```
通配符

```
*  # 任意个字符（可以是0）
?  # 单个字符
[]  # 字符组
[1-3]23.txt  [123]23.txt
>>> 123.txt 223.txt 323.txt
```

### 命令格式

``` 
command [-options] [parameter]
```

``` 
command --help
man command  # manual 手册

b  # 回滚一页
回车  # 显示一行
空格  # 翻一页
q  # 退出
```

### 文件和目录常用命令

1. ls
   - . 开头的是隐藏文件
   - . 表示当前目录  cd.  ls.
   - .. 表示上一层目录  cd..  ls..

```
# list

ls -a  # 显示所有文件，包括隐藏文件 -all 
ls -l  # 以列表显示详细信息
ls -l -h  # 人性化显示文件大小

# 可以合并
ls -lha

ls 2*
```

2. cd

```
cd  # 回到用户的主目录
cd ~  # 回到用户的主目录
cd -  # 在最近常用的两个目录间切换

cd 
```

3. mkdir

``` mkdir
mkdir -p a/b/c/d  # 连续创建嵌套文件夹
```

4. rm

``` 
直接删除，不能恢复

# 删除目录
rm -r  # 可以一次性删除多个嵌套目录

rm -f  # 强制删除
```

### 拷贝和移动命令

1. tree

```
tree [目录名]
tree  # 树状图展示ls
tree ～  # 展示家目录的树状图

tree -d  # 只展示文件夹
```

2. cp

``` 
cp 源文件 目标文件/目标目录  (直接覆盖文件或复制到目录下)
cp -i 源 目标  # 覆盖前提示
cp -r 源 目标  # 复制目录
```

3. mv

```
mv 源文件 目的目录
mv 123.txt .
mv 123.txt ~/Desktop/

mv 123.txt demo.txt  # 重命名  !可能覆盖
```

### 查看文件内容

1. cat
2. more

``` 
# cat
concatenate  # 一次显示文件所有内容

cat -b  # 对非空内容输出行号
cat -n  # 空行也有行号

# more
more  # 一次显示一屏
空格  # 显示下一屏
回车  # 下滚一行
b /f  # 回滚一屏 
```

3. grep

```
grep -n  # 显示行号
grep -v  as read  # read中不包含as的
grep -i  # 忽略大小写

模式查找
^a  # a开头的
ke$  # ke结尾的
```

### 其他

1. echo + 重定向

``` 
# 重定向
>  # 覆盖
>>  # 追加
将显示到终端的防到文件中
```

2. 管道 ｜

```
把一个命令的输出作为另一个命令的输入
ls -lh ～ ｜ grep -ni Do
```

### 远程管理常用命令

1. shutdown

```
shutdown -r [时间]  # 重启
shutdown -c  # 取消关机
shutdown -r now
shutdown 20:25
shutdown +10  # 十分钟之后关机
```

2.   查看网卡信息

```
ifconfig  # 查看网卡配置信息
ping ip  # 

ifconfig ｜ grep
```

3. ssh

```
ssh [-p port] user@remote  # 默认端口22

```

4. scp 传输文件

```
scp -P port 源文件 user@remote:Desktop/01.py
scp -P port user@remote:Desktop/01.py 源文件 
scp -r user@remote:Desktop 源文件  # 复制目录
```

5. ssh高级

```
~目录（家目录）下有.ssh文件夹，存放着ssh配置信息

# 免密码登陆
ssh-keygen  # 生成密钥对
ssh-copy-id user@remote

# 配置别名
Host 别名
	HostName ip
	User iansy
	Port 22
```

### 用户权限常用命令

1. 组 - 用户  分配权限                                                                       

硬连接数 —> 子文件夹

2. chmod 修改权限

```
chmod +/-rwx 文件名/目录名

执行文件  ./01.py

没有可执行，进不去文件夹
没有可读 不能ls
```

3. 超级用户 root

```
sudo
```

4. 组管理

```
groupadd  # 添加组
groupdel  # 删除组
cat /etc/group  # 管理组
chgrp -R 组名 文件/目录名  # -R 递归修改文件子目录

usermod -g 组 用户名  # 修改主组
usermod -G 组 用户名  # 修改附加组
```

5. 添加用户

```
sudo useradd -m -g 组名 用户名
-m  # 自动创建家目录
-g  # 指定组

sudo passwd 用户名  # 添加密码

userdel -r 用户名  # -r 同时删除家目录

用户信息存储在 /etc/passwd
```

6. 查看用户信息

```
id iansy 
who  # 当前登陆的
whoami

切换用户shell 
sudo usermod -s /bin/bash iansy  

which 命令  # !查看位置
```

7. 切换用户

```
su - 用户  # -跳到用户家目录
su -   # 切换到root
```

8. 修改权限

``` 
chmod -R 755 文件名｜目录名  #  数字分别代表拥有者、组、其他：421
chown 用户名 文件名｜目录名   #
chgrp -R 组名 文件名｜目录名  # -R递归修改子文件夹
```

### 系统信息命令

1. 时间和日期

```
date
cal  # calender 一个月的日历
cal -y  # 一整年的日历
```

2. 磁盘信息

``` 
df -h  # disk free
du -h  # disk usage
```

3. 进程信息

```
ps aux  # process status 一般用ps au
a		显示其他用户的
u 	详细信息
x		全部进程

top  # 退出用q

kill -9 PID  # 杀死进程，-9强行终止
```

### 其他命令

1. 查找文件

```
find [路径] -name "*.py"  
find -name "*.py"
```

2. 软链接（快捷方式）

```
ln -s 源文件的绝对路径 链接名  # -s表示软链接
硬链接  ————新的引用
```

3. 打包压缩

```  
# 打包文件
tar -cvf 打包文件.tar 被打包的文件名｜目录名 

# 解包文件
tar -xvf 打包文件.tar

# 压缩文件 gzip
xxx.tar.gz

tar -zcvf 打包文件.tar.gz 被压缩的文件
tar -zxvf 打包文件.tar.gz [-C 目标路径]

# 压缩文件 bzip2
xxx.tar.bz2

tar -jcvf 打包文件.tar.bz2 被压缩文件
tar -jxvf 打包文件.tar.bz2
```

4. 软件安装

```
apt Advanced Packaging Tool

sudo apt install 软件包
sudo apt remove 软件包
sudo apt upgrade
```

