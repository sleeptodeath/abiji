[TOC]
## 01.windows快捷键

- win+L  切换用户
* win+D  返回桌面
* win+E  文件资源管理器
* win+R  运行命令

## 02.Dos 命令
* cd 	改变当前目录。切换盘符:  c:   e:
	 dir 	列文件名 相当于ls
	 md 	创建目录  md a\b\c
	 rd 	删除文件夹   rd /S（递归删除，默认只能删除空文件） /Q（不询问） 文件名
	 del 	删除文件或者文件夹 del  /S /Q
* notepad  xx  创建文件
	 move 	移动文件 \
	  copy 	拷贝文件  copy 源 目标
* xcopy 复制文件夹 xcopy /E 源 目标   /E递归
	 type 	查看文件 
	  cls  	清屏
	 ren/rename 重命名	ren 原文件名  修改后文件名
* echo 'fdsafd' > a.txt  重定向：覆盖
* echo 'dfsafa' >> a.txt  重定向：在文件后追加 
* find "xxx"
* exit  退出命令行
* path  路径
	 date 	日期
* time  时间
* mspaint  画图工具
* ping 
* ipconfig 

## 3.linux介绍

### 3.1 linux的一些知识点
* OS发展：Unix->Minix->Linux
* GNU  , POSIX (Portable Operating System Interface)
* Linux内核：kernel http://www.kernel.org
  * 稳定版
  * 开发版
* 发行版：Ubuntu、RedHat、CentOS、Debian、Fedora、SuSE、OpenSUSE、Arch Linux、SolusOS
* 桌面
  * KDE
  * GNOME

#### 3.2 linux使用场景
* 应用领域：
  * 桌面领域
  * 服务器: 免费、稳定、高效
  * 嵌入式
* 特点：多用户、多任务、支持多线程和多CPU的操作系统

## 4.shell
#### 4.1 终端详解

* username@machinename:~$/#

	 xuqingyuan@xuqingyuan-virtual-machine:~$ ,	$代表普通用户
- root@xuqingyuan-virtual-machine:~#  ,# 代表root用户

#### 4.2 terminal终端的快捷操作

|||
|---|---|
|ctrl + alt + t		|新建终端|
|ctrl + shift + t |新建第二个终端|
|ctrl + alt +F1-F6 |访问终端会话，每次访问会出现登入提示 |
|alt + F7 			|返回图形化桌面环境|
|ctrl + shift + + |终端字体放大|
|ctrl + - 			|终端字体缩小|
|鼠标滚轮      		|复制|

#### 4.3 终端的行操作
|  |   |
| ------ | ---- |
|ctrl + a |跳到行首|
|ctrl + e |跳到行尾|
|ctrl + f |前进|
|ctrl + b |后退|
|ctrl + u |剪切至行首|
|ctrl + k |剪切至行尾|
|ctrl + y |粘贴|
|ctrl + d |删当前光标|
|ctrl + p |向上翻历史记录 或者 方向键 up|
|ctrl +n |向下翻历史记录  或者 方向键 down|

####  4.4 通配符

| | |
|---|---|
|*|匹配0个或多个|
|?| 匹配任一单个|
|[] 	|匹配任意属于字符计中的字符|
|[a-f]	|匹配从 a 到 f 范围内的的任意一个字符|
|[!charater]	|匹配任意不属于字符计中的字符|
|[[:class]] 	|匹配任意一个属于制定字符类的字符|
	[:alnum:]
	[:alpha:]
	[:digit:]
	[:lower:]
	[:upper:]

- exit 推出终端
- init 0 关机

## 5.Linux常用命令:

### 5. 1 文件操作命令

#### 5.1.1 `文件分类`

文件详细信息

d|rwx|r-x|---| 3| root| root| 97| Jun 30 21:20| abrt

文件类型|所有者读写权限|所有组读写权限|其他人读写权限| 硬链接数| 所有者| 所有组 | 文件大小 |　最近访问时间| 文件名

|||
|--|--|
|- |普通文件|
|d  |目录|
|l |软连接|
|p  |管道|
|b  |块设备|
|c | 字符设备|
| s    | 网络编程相关的socket文件 |

#### 5.1.2 文件处理命令

##### pwd （print working directory）查看当前路径

```shell
pwd  	#查看当前路径
pwd -P	#显示出实际的路径，而非使用link软连接后路径。
```

##### ls 列出任何目录的文件和目录
```shell
ls [FILE].. #列出路径下包含的文件和目录

ls / 		# 查看根目录
ls / /home 	# 查看根目录和家目录

ls -l		# 长格式输出
ls -lh  	# 长格式时输出，并以可读的方式显示文件大小

ls -a 		# 列出所有文件，包括隐藏文件

ls -i		# 显示索引节点（inode)号

ls -lt 		# 以文件修改时间进行排序
ls -S		# 以文件大小进行排序

ls --reverse # 逆序

tree -L 3 xx 以树形结构查看xx多少层

```

##### cd （Change Directory的缩写）,切换工作目录
```shell
cd [相对路径或绝对路径]  #切换工作目录

cd ~ 	#切换到用户家目录 /home/username
cd  	#切换到用户家目录
cd /    #切换到根目录，

cd -    #相互切换, 

cd .	
cd ..	#切换到上一级
```

##### touch 更新时间戳，文件不存在则创建
```shell
touch file   #如果文件不存在则创建， 存在则更新文件时间
```

##### mkdir 创建目录 
```shell
mkdir dir1 dir2   			# 不存在则创建目录,存在会报错
mkdir dir1/dir2				# error, 如果dir1不存在会报错，可用-p
mkdir -p dir1/dir2/dir3 	# 若路径中的目录不存在，则先创建目录如dir1，dir2
```

##### cp 复制
```shell
cp [选项] 源文件或者目录 目标文件或者目录

cp 	file1 file2		# 若file2不存在则复制,存在则覆盖 
cp	file1 dir1    	# 若目录dir1存在,则把file1复制到目录dir1中, 不存在则创建file1的备份
cp 	-r dir1 dir2	# 若目录dir2存在,则复制dir1到dir2中，不存在则创建dir1的备份(注意 -r)

cp -r	# 递归处理，讲目录下的文件和子目录一起复制
cp -f  	# 强制,不提示
cp -i  	# 是否覆盖提示,更安全,(默认直接覆盖)
cp -v  	# 显示进度, 
cp -u  	# update更新, 只复制不存在的

cp -p	# 复制的同时，不修改文件属性，包括所有者，所属组，权限和时间
cp -a  	# attribute 拷贝属性和权限
```

##### mv 移动和重命名：
```shell
mv [选项] 源文件或者目录{1..} 目标文件或者目录

mv  文件 文件(已存在） 	# 覆盖
mv	文件 文件(不存在） 	# 改名
mv	文件 目录          # 移动
mv	目录 目录（已存在）	# 移动
mv	目录 目录（不存在）	# 改名 

mv -f  #强制,不提示
mv -i  #覆盖会提示  
mv -v  #显示进度
```

##### rm 删除： 默认只能删除文件，不能删除文件夹

```shell
rm [选项] 文件或者目录{1..}

# 注意要备份啊，谨慎删除
rm file		# 删除文件
rm -i file	# 删除会提示要求确认
rm -rf dir  # 强制删，递归删除目录

rm -r  # 删除目录,递归删除
rm -f  # 强制删除，不提示
rm -i  # 有提示，删除过程逐一确认
rm -v  # 显示信息	
```

#### 5.1.3 文件查看命令
##### cat  显示,连接

```powershell
cat /etc/passwd		# 查看文件
cat -n test.txt  	# 对输出的所有行编号
cat a.txt b.txt >  c.txt  # 将a.txt,b.txt合并输出到c.txt
cat > test.txt   # 根据用户输入创建文件，ctrl+D完成,相当蠢的方式
```

##### head, tail

```shell
#head
head file		# 默认10行
head -n filename  # 查看文件的前n行，

head /ect/passwd   		# 显示/ect/passwd的前10行
head -5 /ect/passwd		# 显示/ect/passwd的前5行

#tail
tail file			# 默认10行
tail -n filename  	# 查看文件的后n行

tail /ect/passwd   		# 显示/ect/passwd的后10行
tail -5 /ect/passwd		# 显示/ect/passwd的后5行

tail -f  #动态查看，
```

##### more 分页显示文件 

```shell
# 推荐用less代替
more 文件名

# f/Space 显示下一页
# Enter  显示下一行
# q 退出
```

##### less 查看文件内容： 

```shell
less filename 	#	less并不少

# 可上下滚动文件，
# f/Space 向下翻页，
# b		  向上翻页
# G  文件末尾， g  文件开头
# /pattern查找
# h帮助
# q	退出
```

####  5.1.4 权限管理命令

#####  权限说明

* 读写权限

|权限|文件|目录|
| --   | ---  | --   |
| r    | 可打开，读取文件内容 | 可显示目录下的文件（同时必须有x权限） |
| w | 可修改文件内容 | 可删除，创建，重命名文件（同时必须有x权限） |
| x | 可执行文件 | 可cd进目录 |

* 用户所有者,用户组,其他人权限
  * ugo, a

##### su,sudo 更改用户身份 

```shell
su 		# 切换到root，但不改变路径
su - 	# 切换为root, 路径为root目录 
su user	# 切换为user
exit 	# 退出当前用户的shell环境
		# 或者 ctrl + D 退出

sudo command # 提升用户为管理员,来运行命令

```
##### chmod 变更文件或目录的权限

```shell
#字母表示
# u（user） g(user group) o(other) a(all)  
# +(添加权限) -（取消权限） =（设定权限）
chmod u+rwx,g=--- a.txt  
chmod ugo+rwx a.txt

#数字表示
# r 	w 		x   
# 100 	010 	001
chmod 777 a.txt  # 将a.txt的权限设置为 rwxrwxrwx  
chmod 7 a.txt  <=> chmod 007 a.txt #省略的话，默认前面补0	

# 
chmod -R  #递归为文件夹下的设置权限
```

##### chown 更改文件或目录的所有者  

```shell
chown [选项] 用户:用户组 文件或目录{1..}

# 属主
chown xqy dir1  # 修改文件dir1的属主为xqy
# 属组
chown :xqy dir1	# 修改文件dir1属组为xqy ，“:”,
chown .xqy dir1	# 修改文件dir1属组为xqy ，“.”,
# 属主：属组
chown -R xqy:xqy dir1 #修改属主，属组  -R递归修改
chown -R xqy.xqy dir1 #修改属主，属组  -R递归修改

#
chown -R # 递归为文件夹下的更改属组或属主
```

##### chgrp 更改文件或者目录的所属组， 可用chown代替



#### 5.1.4 文件搜索命令
##### which 查看`可执行程序命令`的位置
```shell
which command 	# 查看可执行程序命令的位置

which ls		# /bin/ls
which cd		# shell builtin,不是可执行程序命令
which l			# aliase别名，不是可执行程序命令
```

#####  find 查找文件或者目录
```shell
find 搜索路径 [选项] 搜索关键字

find /etc/ -maxdepth 1 -name pas* -type f

# 关键字
-name  '[a-e]*' /  'test.c'  /  '*.c'
-size  2M , +2M, -2M, -size +4k -size -5M
-perm  0777 查找权限为777的文件或目录
-user	# 根据文件所有者查找
-type  	# 根据文件类型查找 f（普通文件） d(目录） l b s 类型
```

##### locate 查找文件或者目录

```shell
# 功能同 find -name  但速度块， 搜索的是/var/lib/locatedb  每天更新一次
# 课通过updatedb 手动更新数据库

locate /ect/pas
updatedb  # 更新
```

##### grep 查找文件里与字符串匹配的行
```shell
grep [option] 'pattern' 文件名 

grep 'root' /etc/service  # 在/etc/service搜索包含root的行 

grep -n # 显示行数
grep -v # 输出不匹配的	
grep -i # 不区分大小写

#正则： ^a 行首, k$ 行尾 ,  [abc],   .(匹配任意) , ?,   + 

```

### 5.2 网络管理和通信命令

##### ifconfig   查看网络配置

```shell
# interfaces config
ifconfig # 查看本机的网络配置信息
```

##### netstat   查看网络状态

```shell
netstat –a		# 显示所有端口
netstat –at		# 显示所有TCP端口
netstat –au		# 显示所有UDP端口
```

##### ping 测试主机间网络连通性

```shell
ping baidu.com  
# ctrl+D 结束打印

ping -c		# 设置回应次数
ping -s		# 设置数据包大小
ping -v 	# 详细显示指令执行过程
```

##### write 向里一个用户发送消息

```shell
write 用户名
# ctrl+D 结束
```

##### wall root向所有用户发送信息

```shell
wall [message]
# ctrl+D 结束
```

### 压缩解压命令

#### 压缩文件知识

* **常见的压缩文件格式**：.gz, .bz2， .zip
* **归档**：tar， 只负责打包，不负责压缩

#### 压缩归档命令

##### tar 归档

```shell
#归档并压缩   
tar -czvf  xx.tar.gz  a.txt c.txt  	# 打包压缩为xx.tar.gz
tar -cjvf  xx.tar.bz2 a.txt c.txt	# 打包压缩为xx.tar.bz2

# 查看
tar -tf test.tar.gz  # -t查看

#解压 
tar -xvf  xx.tar.gz -C hh #  -C 解压到那个位置

tar -c 	# 打包
tar -v	# 显示详细信息
tar -f	# 指令文件名
tar -z	# gzip压缩
tar	-j	# bzip2压缩
tar -x	# 解压
tar -t 	# 查看
tar -C  # 解压到那个位置
```

##### gzip/gunzip 获得.gz格式压缩包

```shell
# 压缩后不保存源文件
gzip [options] [FILE]..  # 压缩文件（不能目录）获得.gz格式的压缩包

gzip a.txt b.txt  #得到a.txt.gz, b.txt.gz

#解压缩
gunzip [options] 压缩包包名  # 解压.gz格式的压缩包

gunzip a.txt.gz  # 解压得到 a.txt
```

##### bzip2/bunzip2  获得.bz2格式压缩包

```shell

bzip2 [options] [FILE]..  # 压缩文件（不能目录）获得.bz2格式的压缩包

bzip2 a.txt b.txt  # 得到a.txt.bz2, b.txt.bz2
bzip2 -k 	# 保留源文件

#解压缩
bunzip2 [options] 压缩包包名  # 解压.bz2格式的压缩包

bunzip2 a.txt.bz2  # 解压得到 a.txt
```

##### zip / unzip 获得.zip格式压缩包

```shell
# 压缩后会保存源文件
zip [-r] [压缩后文件名称] 文件或目录

zip -r a.zip a.txt   # -r 递归目录

#解压
unzip [选项] 压缩包名
unzip xx.zip -d hh  , -d 解压到那个目录
```

### 帮助命令

man info whatis， whoami

####  --help

```shell
command --help	#查看帮助
mdkir 	--help
ls 		--help
```
#### man:   有问题找男人

```shell
man command	#查看帮助
man ls
man man

man 章节号	命令名

man 3 printf
man 1 printf

# 章节号
# 1. Standard commands（标准命令）
# 2. System calls（系统调用，如open,write）
# 3. Library functions（库函数，如printf,fopen）
# 4. Special devices（设备文件的说明，/dev下各种设备）
# 5. File formats（文件格式，如passwd）
# 6. Games and toys（游戏和娱乐）
# 7. Miscellaneous（杂项、惯例与协定等，例如Linux档案系统、网络协# 定、ASCII 码；environ全局变量）
# 8. Administrative Commands（管理员命令，如ifconfig）

# 空格键	显示手册页的下一屏
# Enter 键	一次滚动手册页的一行
# b	回滚一屏
# f	前滚一屏	
# q	退出
# /word	搜索 word 字符串
```

#### info 获取帮助信息
```shell
info command

info ls		#可通过按Enter键跳转超链接
	
info coreutils	
```

#### whatis 显示命令的简要描述
```shell
whatis command

whatis ls # 简要介绍命令功能
```


#### type 查看命令是否为内建命令

```shell
type commond	#查看命令类型
type ls			
#ls is aliased to `ls --color=auto'
type cd			
# shell builtin
type cp
#cp is /bin/cp

```


#### alias 取别名
```shell
alias 命令名="命令操作" # 为命令操作取别名
alias				 # 查看所有别名
alias cp='cp -i' # 为xx设置别名
alias foo='cd /usr;ls;cd -'

# 删除别名
unalias 命令名   # 删除当前shell环境中的别名
```

#### date, cal 时间和日期命令, 

* date  date显示日期

  - '月日时分年' data '+%Y-%m-%d %H:%M:%S' hwclock -s同步硬件 -w同步系统

* cal 日历  
	```shell
	cal #显示当月的日历
	cal 7 2009 #显示 某年某月
	```



#### wc 统计多少行
```shell
wc test.txt
#行数，字数， 字节数
wc -l	#line查看行数
wc -c	#bytes字节数
wc -w 	#word
```

#### clear 清屏	
	```shell
	clear   #或者 ctrl+ l
	```

#### history 查看历史命令  
```shell

# 放在用户家目录 .bash_history
history		#可通过
!行号		#执行第行号个命令
!!		#重复执行最后一个命令

```

#### 5.2硬盘和内存，df,free

- df 命令用于检测文件系统的磁盘空间占用和空余情况
	```shell
	df -a	#显示所有文件系统的磁盘使用情况
	df -h 	#显示大小以M，KB等为单位
	df -T	#显示文件系统
	```
- du 查看当前路径下的文件信息   
	```shell
	du -d 1 # 查看深度为1的文件信息
	du -h 
	```

- free 显示内存使用情况
	```shell
	free -h #显示大小以M，KB等为单位
	free -t #total显示RAM+swap
	```

### 6 文件和目录常用命令：

#### Linux 下文件和目录的特点

- 以'.'开头的文件名是隐藏文件，ls不会列出，要使用ls-a
- 文件名区分大小写
- linux中没有文件拓展名
- 一切皆文件
- **.** 代表当前目录
- **..** 代表上一级目录

#### file 查看文件类型
```shell
file 文件名.. #查看文件类型 
file csapp  #查看csapp的类型
file *		#查看所有文件类型
```

#### 文件分类
*  - 普通文件
*  d  目录
*  p  管道
*  b  块设备
*  c  字符设备
*  l  软连接



#### touch,vim, echo 创建文件:  
```shell
touch filename  #不存在时,创建，存在时修改最后修改日期
vi/vim			#vim创建
echo str > filename #管道创建

```

#### ln 创建硬链接，软链接：
~~~shell
```shell
ln -s 源文件  链接文件 #软连接，-s soft ,如果软连接和源文件不在同一目录，应该要用绝对路径创建

ln 源文件  链接文件  #硬链接，用来备份文件,只占一份空间
ls -i	#显示索引节点（inode)号, 可用来判断硬链接是否指向同一个文件

~~~



## 用户和用户组：

* **root**:  #   ;  **用户**：$

##### id,whoami

```shell
id		 #显示当前用户的uid和gid
id xqy   #显示是否有这个用户

whoami	 # 显示当前用户的名称
who 	 # 显示谁正在登入
```

### 用户和用户组管理

#### 用户管理

##### passwd更改用户密码

```shell
# /etc/shadow   存放密码
passwd	【选项】 username # 根据提示原有密码然后更新,但密码必须是强密码
passwd xqy # 修改xqy的密码,但密码必须是强密码

#要想设置弱密码，可以
su #切换超级用户
passwd username #在为username设置密码，此时可以是简单密码

-l	# 锁定密码，锁定后密码失效，无法登录
-d  # 删除密码，仅管理员可用
-f	# 强制执行

```

##### useradd 添加用户

```shell
# /etc/passwd 存放用户
useradd xqy   # 添加用户

useradd -u # uid 
useradd	-g # gid
useradd	-d # 指定用户登录时的目录
useradd	-m # 文件不存在则创建 
useradd	-s # shell
useradd -r # 创建系统账号
useradd -c # 描述

# 创建一个用户时会影响的文件：
/etc/passwd  
/etc/shadow  
/etc/group  
/etc/gshadow
/etc/home
/var/spool/mail # 邮箱
```

##### userdel 删除用户

```shell
userdel xqy -rf # 删除用户  

userdel -r 	# 删除home目录下的文件和邮件文件
userdel	-f	# 强制删除
```

##### usermod	 修改用户的信息 

```shell
# 只修改了passwd文件,家目录没修改,邮箱目录也没改
-u 	# uid 
-g 	# gid 
-s 	# shell
-d 	# home
-c 	# 描述 
-aG	# 添加组; 

```

#### 用户组管理

* 每个用户都有一个用户组，创建用户时未指定，则会以用户账号作为用户的用户组,
* /etc/group

##### groupadd 添加用户组

```shell
groupadd [选项] 参数
-g # gid 指定id值
-r # 创建系统用户组
-o # 允许创建组id已存在的用户组
```

##### groupdel 删除用户组

```shell
 # 当组有成员时，不能删除
 groupdel 参数
 
```

##### groupmod 修改用户组

``` shell
groupmod [选项] [用户组]

groupmod -g # 指定组id
-n  # 修改用户组的组名
-o	# 允许组id不唯一
```

#### 用户切换

##### su

##### sudo

```shell
visudo	# 比 vim /etc/sudoers 安全
# /etc/sudoers   配置sudo命令

```



## Shell编程

### Shell概述

#### shell的分类：BSh, CSh, KSh,bash

#### shell的功能：命令解释

#### path路径： echo $PATH

### Shell应用技巧

####  输入输出,重定向，
```shell
#标准输入0，标准输出1，标准错误2

# 标准输入重定向
命令 < 文件名
wall < file	# 将file中内容弄个作为wall的输入

# 标准输出重定向
命令 > 文件名
cat /etc/passwd >  c.txt  # 清空c.txt
cat /etc/passwd >>  c.txt	# 在文件后追加

# 标准错误重定向
命令 2> 文件名
gcc -c hello.c -o hello 2>file	# 清空
gcc -c hello.c -o hello 2>>file	# 追加
ls -l /bin/usr &> output-error.txt # 将标准输出和标准错误重定向
ls -l /bin/usr 2> /dev/null # 位桶，不处理  
```
#### 管道  

```shell
# 管道：|  管道一端输出作为另外一端的输入
ls -l /usr/bin | less #  
ls /usr/bin /bin | sort | less	#sort进行过滤排序
ls /usr/bin /bin | sort | uniq | less   #uniq删除重复
						 uniq -d		#-d查看重复
ls /usr/bin /bin | sort | uniq | wc -l  #wc -l统计行数
ls /bin | grep ls
ls /usr/include | grep stdio.h
```



## 进程

* ps -aux  #显示进程信息
  ```shell
  ps -aux	#常用
  ps -a	#显示终端上的所有进程，包括其他用户的进程
  ps -u	#显示进程的详细状态
  ps -x	#显示没有控制终端的进程
  ps -w	#显示加宽，以便显示更多的信息
  ps -r	#只显示正在运行的进程
  ps -e   #
  ps -e | grep mysql #
  ```


* top 用来动态显示运行中的进程
	```shell
	M	#根据内存使用量来排序
	P	#根据CPU占有率来排序
	T	#根据进程运行时间的长短来排序
	U	#可以根据后面输入的用户名来筛选进程
	k	#可以根据后面输入的PID来杀死进程。
	q	#退出
	h	#获得帮助
	```

* htop


* kill 终止进程 需要配合 ps 使用。
	```shell
	kill [-signal] pid #终止进程
	```


* 关机重启
  reboot	重新启动操作系统
  shutdown –r now	重新启动操作系统，shutdown会给别的用户提示
  shutdown -h now	立刻关机，其中now相当于时间为0的状态
  shutdown -h 20:25	系统在今天的20:25 会关机
  shutdown -h +10	系统再过十分钟后自动关机
  init 0	关机
  init 6	重启

* 



* 安装软件：
* 换国内的镜像源
1. 找 阿里云或清华啥的
2. cp /etc/apt/sources.list /etc/apt/sources.list.backup
3. vim /etc/apt/sources.list 复制粘贴
4. sudo apt update

* sudo apt-get update  更新源
* sudo apt-get install package 安装包
* sudo apt-get remove package 删除包
* sudo apt-cache search package 搜索软件包
* sudo apt-cache show package  获取包的相关信息，如说明、大小、版本等
* sudo apt-get install package --reinstall   重新安装包
* sudo apt-get -f install   修复安装
* sudo apt-get remove package --purge 删除包，包括配置文件等
* sudo apt-get build-dep package 安装相关的编译环境
* sudo apt-get upgrade 更新已安装的包
* sudo apt-get dist-upgrade 升级系统






* 
* 服务开启
* service mysql start
* service mysql stop
* service mysql restart
* service mysql status
* 开启ssh服务
* 安装：sudo apt install openssh-server
* 启动：sudo service ssh start
* 查看服务启动状态：   sudo ps -e | grep ssh  ,  sudo service ssh status

## 7 Linux常用开发工具

###  vi编辑器: 

#### vi基础知识

##### 工作模式：

* 命令模式(command mode), 插入模式(insert mdoe), 底行模式(last line mode)

#### 命令模式

##### 移动

|              |      |        |
| ------------ | ---- | ------ |
| **方向移动** | h    | 左移   |
|              | l    | 右移   |
|              | j    | 下一行 |
|              | k    | 上一行 |
| **行级移动** | 0    | 行首   |
|              | $    | 行尾   |
| **单词级** | w | 下一个单词首字母 |
|              | e | 下一个单词尾字母 |
| **文档级** | G | 文档尾行 |
|  | nG | 跳转到第n行 |
|              | gg | w文档首行 |

##### 删除

|      |                    |
| ---- | ------------------ |
| x    | 删除光标所在的字符 |
| dd   | 删除行             |
| ndd  | 删除n行            |
| d+$  | 删除光标位置到行尾 |
| d+0  | 删除光标位置到行首 |
| d+w  |                    |
| d+gg | 删除所在行到首行   |
| d+G  | 删除所在行到尾行   |

##### 复制和粘贴

|       |                      |
| ----- | -------------------- |
| yy    | 复制当前行           |
| nyy   | 复制n行              |
| y + $ | 复制到行尾           |
| y + 0 | 复制到行首           |
| p     | 在当前光标下一行粘贴 |
| np    | 粘贴n行              |

##### 撤销：  u

##### 重复： .

##### 替换：r，R



#### 插入模式

* 进入插入模式： a i o ， A,I , O

#### 底行模式

* :set nu  设置行号
* :set nonu  取消行号
* :n    移动到第n行
* :/xx  查找xx
* 内容替换
* 

* ubuntu vi 中 backspace问题  ， ： 安装vim

* ctrl + n 补全

* ctrl + b ,ctrl + f 翻屏

* v V 选中一片

* > << 整体向右左移动

* .重复执行

* ! 可输入shell命令

* / str查找
  n: 下一个
  N：上一个

* 替换命令：
  :%s/abc/123/g  #末行模式下，将光标所在行的abc替换成123
  :1, 10s/abc/123/g #末行模式下，将第一行至第10行之间的abc替换成123

* vim 配置
1. /etc/vim/vimrc
2. ~/.vimrc
3. ~/.vimrc优先级高



### Linux 主要目录速查表

- /：根目录，一般根目录下只存放目录，在 linux 下有且只有一个根目录，所有的东西都是从这里开始
  - 当在终端里输入 `/home`，其实是在告诉电脑，先从 `/`（根目录）开始，再进入到 `home` 目录
- /bin、/usr/bin：可执行二进制文件的目录，如常用的命令 ls、tar、mv、cat 等
- /boot：放置 linux 系统启动时用到的一些文件，如 linux 的内核文件：`/boot/vmlinuz`，系统引导管理器：`/boot/grub`
- /dev：存放linux系统下的设备文件，访问该目录下某个文件，相当于访问某个设备，常用的是挂载光驱`mount /dev/cdrom /mnt`
- /etc：系统配置文件存放的目录，不建议在此目录下存放可执行文件，重要的配置文件有
  - /etc/inittab
  - /etc/fstab
  - /etc/init.d
  - /etc/X11
  - /etc/sysconfig
  - /etc/xinetd.d
- /home：系统默认的用户家目录，新增用户账号时，用户的家目录都存放在此目录下
  - `~` 表示当前用户的家目录
  - `~edu` 表示用户 `edu` 的家目录
- /lib、/usr/lib、/usr/local/lib：系统使用的函数库的目录，程序在执行过程中，需要调用一些额外的参数时需要函数库的协助
- /lost+fount：系统异常产生错误时，会将一些遗失的片段放置于此目录下
- /mnt: /media：光盘默认挂载点，通常光盘挂载于 /mnt/cdrom 下，也不一定，可以选择任意位置进行挂载
- /opt：给主机额外安装软件所摆放的目录
- /proc：此目录的数据都在内存中，如系统核心，外部设备，网络状态，由于数据都存放于内存中，所以不占用磁盘空间，比较重要的文件有：/proc/cpuinfo、/proc/interrupts、/proc/dma、/proc/ioports、/proc/net/* 等
- /root：系统管理员root的家目录
- /sbin、/usr/sbin、/usr/local/sbin：放置系统管理员使用的可执行命令，如 fdisk、shutdown、mount 等。与 /bin 不同的是，这几个目录是给系统管理员 root 使用的命令，一般用户只能"查看"而不能设置和使用
- /tmp：一般用户或正在执行的程序临时存放文件的目录，任何人都可以访问，重要数据不可放置在此目录下
- /srv：服务启动之后需要访问的数据目录，如 www 服务需要访问的网页数据存放在 /srv/www 内
- /usr：应用程序存放目录
  - /usr/bin：存放应用程序
  - /usr/share：存放共享数据
  - /usr/lib：存放不能直接运行的，却是许多程序运行所必需的一些函数库文件
  - /usr/local：存放软件升级包
  - /usr/share/doc：系统说明文件存放目录
  - /usr/share/man：程序说明文件存放目录
- /var：放置系统执行过程中经常变化的文件
  - /var/log：随时更改的日志文件
  - /var/spool/mail：邮件存放的目录
  - /var/run：程序或服务启动后，其 PID **存放在该目录下**