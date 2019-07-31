



华为云:

119.3.211.100

root  xqy123456.

mysql root xqy123456.



ubuntu16.04升级为18.04

```

```



#### 点击图标最小化

```SHELL
gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'
```

#### 统一Win10和Ubuntu18.04双系统的时间

```shell
timedatectl set-local-rtc 1
```

#### 安装 gnome-tweak

```SHELL
sudo apt install gnome-tweak-tool
```



#### 换源

> 修改 /etc/apt/sources.list文件

1.备份

```shell
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

2.修改/etc/apt/sources.list,替换为需要的源(这里为清华源)

```shell
sudo vim /etc/apt/sources.list

# 清华源
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial universe

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates universe

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial multiverse

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates multiverse

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security universe deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security multiverse


# 阿里源
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse

```

3.更新

```shell
sudo apt update
```



#### 创建用户并设置sudo权限

> 参考:https://blog.csdn.net/heiheiya/article/details/86063137
>
> vim /etc/sudoers 
>
> 
>
> root ALL=(ALL:ALL) ALL

#### 为软件创建桌面快捷方式

> Linux 系统中的Desktop Entry 文件以 .desktop为后缀名。Desktop Entry 文件是 Linux 桌面系统中用于描述程序启动配置信息的文件。 
> 存放在进入`/usr/share/applications` 目录
>
> 参考: https://blog.csdn.net/u010071211/article/details/81114269

１. 创建：　sudo vim /usr/share/applications/eclipse.desktop
2. 编辑: 

   ```shell
   [Desktop Entry]
   Encoding=UTF-8
   Nmae=Eclise  	#名称
   Comment=Eclipse
   Exec=/usr/local/eclipse/eclipse   #软件的具体路径
   Icon=/usr/local/eclipse/icon.xpm	# 图标
   StartupNotify=true
Type=Application
   Terminal=false		#软件打开时是否启动终端
   ```
   

#### 安装mysql,并设置远程连接

> Ubuntu18.04 
>
> 参考:https://www.cnblogs.com/woshimrf/p/ubuntu-install-mysql.html

1.安装mysql

```shell
sudo apt install mysql-server mysql-common mysql-client
```

2.字符集修改为utf-8

```mysql
sudo mysql -u root 
# 如果装的mariadb, 默认字符集已经是utf8了。mysql则不是,可通过一下测试
show variables like 'char%';

show variables like 'collation%';
```

修改字符集合

```shell
sudo vim /etc/mysql/my.cnf
```

添加以下内容

```shell
[mysqld]
collation-server = utf8_unicode_ci
init-connect='SET NAMES utf8'
character-set-server = utf8
```

重启：

```shell
service mysql restart
```

3.登录权限问题,以及远程登录

> Ubuntu18.04 安装mysql或者mariadb之后，发现普通用户和远程都没有权限连接。
>
> Access denied for user: 'root@localhost'
>
> 解决:删除root,重新创建用户

登录

```shell
sudo mysql -u root
```

查看当前用户

```mysql
SELECT USER,Host FROM mysql.user;
```

删除root

```mysql
DROP USER 'root'@'localhost';
```

重建root

```mysql
CREATE USER 'root'@'%' IDENTIFIED BY '123456';
# ERROR 1819密码太简单错误,按以下更改一下密码要求即可
set global validate_password_policy=0;
set global validate_password_length=4;
```

授权(允许远程登录)

```mysql
#1.
mysql -u root -p
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;


#2.修改/etc/mysql/mysql.conf/mysqld.cnf  注释掉127.0.0.1
```

workbench连接

```
# 安装ssh
sudo apt install ssh
sudo apt-get install openssh-server

选TCP over Ssh
输入信息即可

```

![1559050829681](/home/xuqingyuan/.config/Typora/typora-user-images/1559050829681.png)

#### shadowsocks  客户端版

> https://blog.csdn.net/yjt1325/article/details/84638759

#### shadowsocks 翻墙

> 0. vultr 修改ipv6,
> 1. sudo apt install python-pip shadowsocks
>
> 2. vim /etc/shadowsocks.json
>
>    ```
>    {
>        "server":"::",   # ipv6
>        "local_address":"127.0.0.1",
>        "local_port":1080,
>        "port_password":{
>             "2008":"nmslwsnd",  #端口,密码
>             "9999":"nmslwsnd"
>        },
>        "timeout":300,
>        "method":"aes-256-cfb",  # 使用策略
>        "fast_open":false
>    }
>    ```
>
>    3. ssserver -c /etc/shadowsocks.json -d start/stop/restart





