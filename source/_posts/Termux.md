---
title: Termux
date: 2020-01-30 16:39:28
tags:
---

Termux 高级终端安装使用配置教程,这篇文章拖了有小半年.因为网上相关的文章相对来说还是比较少的,恰好今天又刷了机,所以就特意来总结一下,希望本文可以帮助到其他的小伙伴.发挥Android平台更大的DIY空间.
简介
Termux是一个Android下一个高级的终端模拟器,开源且不需要root,支持apt管理软件包，十分方便安装软件包,完美支持Python,PHP,Ruby,Go,Nodejs,MySQL等。随着智能设备的普及和性能的不断提升，如今的手机、平板等的硬件标准已达到了初级桌面计算机的硬件标准,用心去打造完全可以把手机变成一个强大的工具.

官网
Github项目地址
Google Play下载地址
Google Play下载的版本比酷安要新,有能力建议下载Google PLay版本的.

基本操作
长按屏幕
显示菜单项（包括复制、粘贴、更多），此时屏幕出现可选择的复制光标


长按屏幕
├── COPY:复制
├── PASTE:更多
├── More:更多
   ├── Select URL: 选择网址
   └── Share transcipt: 分享命令脚本
   └── Reset: 重置
   └── Kill process: 杀掉当前终端会话进程
   └── Style: 风格配色
   └── Help: 帮助文档
从左向右滑动
显示隐藏式导航栏，可以新建、切换、重命名会话session和调用弹出输入法


显示扩展功能按键
扩展功能键是什么?就是PC端常用的按键如:ESC键，CTR键，TAB键,但是手机上难以操作的一些按键.

效果图


方法一
从左向右滑动,显示隐藏式导航栏,长按左下角的KEYBOARD.

方法二
使用Termux快捷键:音量++Q键

实用快捷键
Ctrl键是终端用户常用的按键 - 但大多数触摸键盘都没有这个按键。为此，Termux使用音量减小按钮来模拟Ctrl键。
例如，在触摸键盘上按音量减小+ L发送与在硬件键盘上按Ctrl + L相同的输入。

Ctrl+A -> 将光标移动到行首
Ctrl+C -> 中止当前进程
Ctrl+D -> 注销终端会话
Ctrl+E -> 将光标移动到行尾
Ctrl+K -> 从光标删除到行尾
Ctrl+L -> 清除终端
Ctrl+Z -> 挂起（发送SIGTSTP到）当前进程
音量加键也可以作为产生特定输入的特殊键.

音量加+E -> Esc键
音量加+T -> Tab键
音量加+1 -> F1（和音量增加+ 2→F2等）
音量加+0 -> F10
音量加+B -> Alt + B，使用readline时返回一个单词
音量加+F -> Alt + F，使用readline时转发一个单词
音量加+X -> Alt+X
音量加+W -> 向上箭头键
音量加+A -> 向左箭头键
音量加+S -> 向下箭头键
音量加+D -> 向右箭头键
音量加+L -> | （管道字符）
音量加+H -> 〜（波浪号字符）
音量加+U -> _ (下划线字符)
音量加+P -> 上一页
音量加+N -> 下一页
音量加+. -> Ctrl + \（SIGQUIT）
音量加+V -> 显示音量控制
音量加+Q -> 显示额外的按键视图
快速上手
基本命令
Termux除了支持apt命令外,还在此基础上封装了pkg命令,pkg命令向下兼容apt命令.apt命令大家应该都比较熟悉了,这里直接简单的介绍下pkg命令:

Bash
pkg search <query>              搜索包
pkg install <package>           安装包
pkg uninstall <package>         卸载包
pkg reinstall <package>         重新安装包
pkg update                      更新源
pkg upgrade                     升级软件包
pkg list-all                    列出可供安装的所有包
pkg list-installed              列出已经安装的包
pkg shoe <package>              显示某个包的详细信息
pkg files <package>             显示某个包的相关文件夹路径
目录环境结构
Bash
~ > echo $HOME
/data/data/com.termux/files/home

 ~ > echo $PREFIX
/data/data/com.termux/files/usr

 ~ > echo $TMPPREFIX
/data/data/com.termux/files/usr/tmp/zsh
长期使用Linux的朋友可能会发现，这个HOME路径看上去可能不太一样,为了方便,Termux 提供了一个特殊的环境变量:PREFIX


更换国内源
更换Termux清华大学源,加快软件包下载速度.

设置默认编辑器

Bash
export EDITOR=vi
编辑源文件

Bash
apt edit-sources
将原来的https://termux.net官方源替换为http://mirrors.tuna.tsinghua.edu.cn/termux

Bash
# The termux repository mirror from TUNA:
deb https://mirrors.tuna.tsinghua.edu.cn/termux stable main保存并退出  
直接编辑源文件

上面是官方推荐的方法,其实还有更简单的方法,类似于Linux下直接去编辑源文件:

Bash
vi  $PREFIX/etc/apt/sources.list
如果清华源 出一些问题的话，大家可以尝试先用着官方源：

Bash
# The main termux repository:
deb https://termux.org/packages/ stable main
安装基本工具
Bash
pkg update
pkg install vim curl wget git unzip unrar
Termux优化
终端配色
主要使用了zsh来替代bash作为默认shell.
使用一键安装脚本来安装,一步到位,顺便启动了外置存储,可以直接访问SD卡下的目录.

执行下面这个命令确保已经安装好了curl

Bash
sh -c "$(curl -fsSL https://github.com/Cabbagec/termux-ohmyzsh/raw/master/install.sh)"  


Android6.0以上会弹框确认是否授权,允许授权后Termux可以方便的访问SD卡文件.
脚本允许后先后有如下两个选项:
Enter a number, leave blank to not to change: 14
Enter a number, leave blank to not to change: 6
分别选择背景色和字体
想要继续更改挑选配色的话,继续运行脚本来再次筛选:

Bash
$ ~/termux-ohmyzsh/install.sh
exit重启sessions会话生效配置

访问外置存储优化
执行过上面的zsh一键配置脚本后,并且授予文件访问权限的话,会在家目录生成storage目录，并且生成若干目录，软连接都指向外置存储卡的相应目录


创建QQ文件夹软连接

手机上一般经常使用手机QQ来接收文件,这里为了方便文件传输,直接在storage目录下创建软链接.
QQ

Bash
ln -s /data/data/com.termux/files/home/storage/shared/tencent/QQfile_recv QQ
TIM

Bash
ln -s /data/data/com.termux/files/home/storage/shared/tencent/TIMfile_recv TIM
最后效果图如下:



这样可以直接在home目录下去访问QQ文件夹,非常方便文件的传输,大大提升了工作效率.
http://mirrors.tuna.tsinghua.edu.cn/termux
oh my zsh主题配色
编辑.zshrc配置文件

$ vim .zshrc
第一行可以看到,默认的主题是agnoster主题:



在.oh-my-zsh/themes目录下放着oh-my-zsh所有的主题配置文件.
下面是国光认为还不错的几款主题
agnoster


robbyrussell


jaischeema


re5et


junkfood


cloud


random

当然如果你是个变态的话,可以尝试random主题,每打开一个会话配色主题都是随机的.

Bash
ZSH_THEME="random"
修改启动问候语
默认的启动问候语如下:



这个对于初学者有一定的帮助在前期,随着对Termux的熟悉,这个默认的问候语就会显得比较臃肿.
编辑问候语文件直接修改问候语:
Bash
vim $PREFIX/etc/motd
修改完的效果如下:



这样启动新的会话的时候看上去就会简洁很多.
管理员身份
手机没有root
利用proot工具来模拟某些需要root的环境

Bash
pkg install proot
然后终端下面输入:

termux-chroot
即可模拟root环境
在这个proot环境下面,相当于是进入了home目录,可以很方便地进行一些配置.



在管理员身份下，输入exit可回到普通用户身份。
手机已经root
安装tsu,这是一个su的termux版本,用来在termux上替代su:

Bash
pkg install tsu
然后终端下面输入:

tsu
即可切换root用户,这个时候会弹出root授权提示,给予其root权限,效果图如下:



在管理员身份下，输入exit可回到普通用户身份。
信息安全
因为termux可以很好的支持Python,所以几乎所有用Python编写的安全工具都是可以完美的运行使用的. 总的来说可玩性还是比较高的.

Metasploit
安装Ｍetasploit

目前Termux官方的pkg已经支持直接安装Metasploit了，通过如下两条命令即可安装，下载过程大约1分钟左右（当然国光我是挂代理的），安装一些相关的依赖包大约10分钟左右：

Bash
pkg install unstable-repo
pkg install metasploit

最新的MSF5版本已经有cve-2019-0708的exploit了

Nmap
端口扫描必备工具

Bash
pkg install nmap

hydra
Hydra是著名的黑客组织THC的一款开源暴力破解工具这是一个验证性质的工具，主要目的是：展示安全研究人员从远程获取一个系统认证权限。

Bash
pkg install hydra

sslscan
SSLscan主要探测基于ssl的服务，如https。SSLscan是一款探测目标服务器所支持的SSL加密算法工具。
SSlscan的代码托管在Github

Bash
pkg install sslscan

whatportis
whatportis是一款可以通过服务查询默认端口，或者是通过端口查询默认服务的工具，简单易用。在渗透测试过程中，如果需要查询某个端口绑定什么服务器，或者某个应用绑定的默认端口，可以使用whatportis查询。

pip2 install whatportis

SQLmap
SQLmap是一款用来检测与利用SQL注入漏洞的免费开源工具 官方项目地址

直接git clone源码

git clone https://github.com/sqlmapproject/sqlmap.git
cd sqlmap
python2 sqlmap.py
sqlmap支持pip安装了,所以建议直接 pip install sqlmap 来进行安装,然后终端下直接sqlmap就可以了,十分方便.


RouterSploit
RouteSploit框架是一款开源的路由器等嵌入式设备漏洞检测及利用框架。

Bash
pip2 install requests
git clone https://github.com/reverse-shell/routersploit
cd routersploit
python2 rsf.py

Slowloris
低带宽的DoS工具

git clone https://github.com/gkbrk/slowloris.git
cd slowloris
chmod +x slowloris.py

RED_HAWK
一款采用PHP语言开发的多合一型渗透测试工具，它可以帮助我们完成信息采集、SQL漏洞扫描和资源爬取等任务。

Bash
pkg install php
git clone https://github.com/Tuhinshubhra/RED_HAWK.git
cd RED_HAWK
php rhawk.php

Cupp
Cupp是一款用Python语言写成的可交互性的字典生成脚本。尤其适合社会工程学，当你收集到目标的具体信息后，你就可以通过这个工具来智能化生成关于目标的字典。

git clone https://github.com/Mebus/cupp.git
cd cupp
python2 cupp.py

Hash-Buster
Hash Buster是一个用python编写的在线破解Hash的脚本，官方说5秒内破解,速度实际测试还不错哦~

git clone https://github.com/UltimateHackers/Hash-Buster.git
cd Hash-Buster
python2 hash.py

D-TECT
D-TECT是一个用Python编写的先进的渗透测试工具,

wordpress用户名枚举
敏感文件检测
子域名爆破
端口扫描
Wordperss扫描
XSS扫描
SQL注入扫描等
git clone https://github.com/shawarkhanethicalhacker/D-TECT.git
cd D-TECT
python2 d-tect.py

WPSeku
WPSeku 是一个用 Python 写的简单的 WordPress 漏洞扫描器，它可以被用来扫描本地以及远程安装的 WordPress 来找出安全问题。被评为2017年最受欢迎的十大开源黑客工具.

Bash
git clone https://github.com/m4ll0k/WPSeku.git
cd WPSeku
pip3 install -r requirements.txt
python3 wpseku.py

XSStrike
XSStrike是一种先进的XSS检测工具。它具有强大的模糊测试引擎.

Bash
git clone https://github.com/UltimateHackers/XSStrike.git
cd XSStrike
pip2 install -r requirements.txt
python2 xsstrike

小结
因为Termux完美的支持Python和Perl等语言,所以有太多优秀的信息安全工具值得大家去发现了,这里我就不一一列举了.

Python环境部署
安装python2.7
Bash
pkg install python2
安装完成后,使用python2命令启动python 2.7.14环境.


安装python3
pkg install python
安装完成后,使用python命令启动python 3.6.5环境.


升级pip版本
Bash
python2 -m pip install --upgrade pip
python -m pip install --upgrade pip
这两条命令分别升级了pip2和pip3到最新版.
pip版本查看


ipython
ipython是一个python的交互式shell，支持变量自动补全，自动缩进，支持bash shell命令，内置了许多很有用的功能和函数。学习ipython将会让我们以一种更高的效率来使用python。
先安装clang,否则直接使用pip安装ipython会失败报错.

pkg install clang
pip install ipython
pip3.6 install ipython
然后分别使用ipython和ipython2进入py2和py3控制台:


编辑器
终端下有vim神器,并且官方也已经封装了vim-python,对vim进行了Python相关的优化.

Bash
pkg install vim-python
解决termux下的vim汉字乱码

在家目录下,新建.vimrc文件

Bash
vim .vimrc
添加内容如下:

set fileencodings=utf-8,gb2312,gb18030,gbk,ucs-bom,cp936,latin1
set enc=utf8
set fencs=utf8,gbk,gb2312,gb18030
然后source下变量:

Bash
source .vimrc
效果图


nodejs
安装nodejs
Bash
pkg install nodejs
安装比较方便,但是在安装的时候报错了

Cannot read property 'length' of undefined
查了下是这边版本的问题



官方的解决方法如下
disable concurrency in case of libuv/libuv#1459

解决npm安装报错
Bash
vim $PREFIX/lib/node_modules/npm/node_modules/worker-farm/lib/farm.js
我这里修改length的是4,这个好像和CPU有关,总之这里的length得指定一个数字.



然后在重新安装下npm install hexo-cli -g成功.
MariaDB(MySQL)安装
MariaDB数据库管理系统是MySQL的一个分支，主要由开源社区在维护，采用GPL授权许可。开发这个分支的原因之一是：甲骨文公司收购了MySQL后，有将MySQL闭源的潜在风险，因此社区采用分支的方式来避开这个风险。

安装mariadb
Bash
pkg install mariadb
安装基本数据
Bash
mysql_install_db
启动mariadb服务
Bash
mysqld
启动完成后,这个会话就一直存活,类似与debug调试一样,只有新建会话才可以操作.



关于隐藏会话可以使用nohup命令和tmux命令,这里我建议使用tmux命令
新建termux会话
由于mariadb安装的时候没有设置密码,当前的mariadb密码为空.

mysql
直接进入mariadb数据库.输入exit退出数据库.


修改密码
输入一下命令,进行密码相关的安全设置:

Bash
mysql_secure_installation
输入当前输入密码
因为是空密码,这里默认 回车

Bash
Enter current password for root (enter for none):
设置新密码
这里设置新的root密码

Bash
Set root password? [Y/n] y
New password:
Re-enter new password:
其他设置
下面根据个人偏好来进行设置,没有绝对的要求

Bash
Remove anonymous users? [Y/n] Y                #是否移除匿名用户
Disallow root login remotely? [Y/n] n          #是否不允许root远程登录
Remove test database and access to it? [Y/n] n #是否移除test数据库
Reload privilege tables now? [Y/n] y           #是否重新加载表的权限
使用密码登录数据库
Mysql
$ mysql -uroot -p
Enter password: ***apache2

tmux
Tmux是一个优秀的终端复用软件，类似GNU Screen，但来自于OpenBSD，采用BSD授权。一旦你熟悉了 tmux 后， 它就像一个加速器一样加速你的工作效率。

安装tmux
Bash
pkg install tmux
新建mysql会话
上面介绍的mysqld后会一直卡在那里,强迫症表示接受不了,重启手机,现在尝试使用tmux来管理会话.

Bash
tmux new -s mysql
可以看到最下面的提示,表明现在是在mysql的会话下面操作


启动mysqld并断开会话
启动mysqld

Bash
mysqld
让会话后台运行
使用快捷键组合Ctrl+b + d，三次按键就可以断开当前会话。

使用mysql
现在那个mysqld会话被放在后台运行了,整个界面看上去很简介,使用

Bash
mysql -uroot -p
可以优雅的使用数据库了.
效果图



关于tmux更多进阶的用法这里不在过多介绍了.
php
termux封装的php版本是php 7.2.5

安装PHP
Bash
pkg install php
查看下版本


自PHP5.4之后 PHP内置了一个Web 服务器,来在termux下尝试下PHP Web Server的简单使.

编写测试文件
在家目录下建一个www文件夹:mkdir www
在www文件夹下新建一个index.php文件,其内容为

Php
<?php phpinfo();?>

启动WebServer
php -S 127.0.0.1:8080 -t www/
浏览器访问效果如下:


nginx
Nginx 是一个高性能的 Web 和反向代理服务器, 它具有有很多非常优越的特性.

安装nginx包
Bash
pkg install nginx
切换root用户
尝试下能不能解析默认的index.html主页
这个文件在termux上的默认位置为/data/data/com.termux/files/usr/share/nginx/html/index.html
切换root用户

默认的普通权限无法启动nginx,需要模拟root权限才可以

没有这个命令的话,手动安装pkg install proot包

termux-chroot
进入模拟的root环境

启动nginx
在模拟的root环境下启动nginx

nginx
termux上nginx默认的端口是8080
查看下8080端口是否在运行

Bash
netstat -an |grep 8080


然后手机本地直接访问:http://127.0.0.1:8080 查看下nginx是否正常启动.
效果图


这样一个默认的nginx服务就起来了,但是意义不大,得配置一下可以解析php才会有更大的意义.
停止nginx服务
这里是直接杀掉占用端口的进程,具体端口以实际情况为准.

Bash
fuser -k 8080/tcp
重启nginx服务
nginx -s reload
网站搭建
nginx解析PHP
nginx解析PHP这里单独拿出一级标题来叙述,成功解析的话,下面安装wordpress等cms就会轻松很多.
nginx本身不能处理PHP，它只是个web服务器，当接收到php请求后发给php解释器处理,nginx一般是把请求发fastcgi管理进程处理,PHP-FPM是一个PHP FastCGI管理器,所以这里得先安装php-fpm.

这里默已经安装了nginx和php,没有安装的话,使用pkg install php nginx来进行安装,参考上面部分进行配置

安装并配置php-fpm
安装php-fpm

Bash
pkg install php-fpm
配置php-fpm
进入proot环境,然后编辑配置文件www.conf(先进proot可以更方便操作编写相关配置文件)

Bash
termux-chroot
vim /etc/php-fpm.d/www.conf
定位搜索listen找到

listen = /data/data/com.termux/files/usr/var/run/php-fpm.sock
将其改为

listen = 127.0.0.1:9000
配置nginx
在proot环境下,然后编辑配置文件nginx.conf

vim /etc/nginx/nginx.conf
下面给出已经配置好的模板文件,直接编辑替换整个文件即可:

Bash

worker_processes  1;
events {
    worker_connections  1024;
}


http {
    include       mime.types;
    default_type  application/octet-stream;
    sendfile        on;
    keepalive_timeout  65;


    server {

        listen       8080;
        server_name  localhost;
        root   /data/data/com.termux/files/usr/share/nginx/html;
        index  index.html index.htm;


        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   /data/data/com.termux/files/usr/share/nginx/html;
        }


        location ~ \.php$ {
            root           html;
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            fastcgi_param  SCRIPT_FILENAME  /usr/share/nginx/html$fastcgi_script_name;
            include        fastcgi_params;
        }
    }

}
里面的网站默认路径就是nginx默认的网站根目录:

Bash
root   /data/data/com.termux/files/usr/share/nginx/html;
fastcgi_param  SCRIPT_FILENAME  /usr/share/nginx/html$fastcgi_script_name;
要修改网站默认路径的话,只需要修改这两处即可.

建立php测试文件
在/usr/share/nginx/html目录下新建一个phpinfo.php文件,其内容是:<?php phpinfo();?>



went
启动php-fpm和nginx
在proot环境下面分别启动php-fpm和nginx,这里的nginx不在proot环境下启动后会出一些问题,感兴趣的可以自己去研究看看.

Bash
php-fpm
nginx
浏览器访问测试
浏览器访问http://127.0.0.1:8080/phpinfo.php 查询php文件是否解析了.


搭建WordPress
这里只是用wordpress做个典型安利来讲解,类似地可以安装Discuz,DeDecms等国内主流的PHP应用程序.

方法一 使用PHP内置的Web Server
确保安装并配置了php和mariadb,没有安装好的话,参考本文中具体细节部分来进行安装.
新建数据库

*** 这里是mysql的密码

Sql
mysql -uroot -p*** -e"create database wordpress;show databases;"
下载解压wordpress

Bash
wget https://cn.wordpress.org/wordpress-4.9.4-zh_CN.zip
pkg install unzip
unzip wordpress-4.9.4-zh_CN.zip
启动PHP Web Server
到解压后的wordpress目录下,执行

Bash
cd wordpress
php -S 127.0.0.1:8080
然后浏览器访问127.0.0.1:8080开始进行wordperss的安装.
效果图


方法二 nginx+PHP+Mariadb
上面使用的方法一是直接使用PHP自带的PHP Web Server来运行的,看上去不够严谨~,所以这里用nginx来部署wordpress.
确保安装了PHP,php-fpm,mariadb,没有安装的话,参考本文中具体细节部分来进行安装和配置.
新建数据和wordpress下载参考上面的方法一,这里主要介绍使用nginx去解析wordpress源文件.
当前解压后wordpress的绝对路径是:

Bash
/data/data/com.termux/files/home/wordpress
编辑nginx.conf

Bash
vim /etc/nginx/nginx.conf
修改为如下几处:

root   /data/data/com.termux/files/home/wordpress;
        index  index.html index.htm index.php;

fastcgi_param  SCRIPT_FILENAME  /data/data/com.termux/files/home/wordpress$fastcgi_script_name;


启动php-fpm和nginx
在proot环境下面分别启动php-fpm和nginx,这里的nginx不在proot环境下启动后会出一些问题,感兴趣的可以自己去研究看看.
Bash
php-fpm
nginx
安装wordpress
浏览器访问:http://127.0.0.1:8080/wp-admin/setup-config.php进行安装.
效果图



同理安装其他博客也就轻而易举了,可玩性大大增加~
搭建hexo博客
安装hexo
npm install hexo-cli -g
部署hexo博客环境
然后建立一个目录,然后到这个目录下初始化hexo环境

mkdir hexoblog  #手动创建一个目录
cd hexoblog  
hexo init   #初始化hexo环境
hexo g      #生成静态文件
hexo s      #启动hexo


然后就跑起来一个最基本的hexo博客
关于hexo博客的详细教程,建议搭建去参考hexo官方文档,我这里重点在于 termux 其他的不作过多的叙述.
效果图

SSH
Termux ssh 连接电脑
有时候要操作电脑,这个时候有了termux,躺在床上就可以操作电脑了,岂不是美滋滋~~
安装openssh

Bash
pkg install openssh
然后就可以直接ssh连接你的电脑了

前提是电脑安装了ssh服务

Bash
$ ssh sqlsec@192.168.1.8
手机连接操作电脑效果图:


电脑ssh连接Termux
emmm 这个需求比较鸡肋,但是写文字嘛就得写全了~

安装openssh

同样也需要openssh才可以

pkg install openssh
启动sshd

安装完成后,sshd服务默认没有启动,所以得手动启动下:

sshd
因为手机上面低的端口有安全限制,所以这里的openssh默认的sshd默认的服务是8022端口上的.
ssh的用户名用whoami命令看下.



可以看到sshd启动后,端口才可以看到.
PC端生成公钥

ssh登录是key公钥模式登录,首先在PC端生成秘钥:

Bash
sqlsec@ubuntu:-> ssh-keygen -t rsa
执行完成后，会在家目录下创建3个文件
id_rsa, id_rsa.pub , known_hosts


拷贝公钥到手机

然后把公钥id_rsa.pub拷贝到手机的data\data\com.termux\files\home\.ssh文件夹中.

将公钥拷贝到验证文件中

在Termux下操作

Bash
cat id_rsa.pub > authorized_keys

PC端连接手机termux

Bash
sqlsec@ubuntu-> ssh -p8022 u0_a119@192.168.1.3
效果图



pc端连接手机termux 真心鸡肋呀~(忍不住自己吐槽下自己)
下载
使用Aria2打造自己的下载工具
Aria2是一个轻量级多协议和多源命令行下载实用工具。它支持 HTTP / HTTPS, FTP, SFTP, bt 和 Metalink。通过内置 Aria2 可以操作 json - rpc 和 xml - rpc。配置好的话还可以高速下载百度云文件.

安装aria2
pkg install aria2
本地启动服务
Bash
aria2c --enable-rpc --rpc-listen-all
这个rpc服务默认监听的是6800端口,启动后方便下面的Web界面连接操作.

webui-aria2
这是个Aria2的热门项目,把Aria2封装在了Web平台,操作起来更加简单便捷。

git clone https://github.com/ziahamza/webui-aria2.git
cd webui-aria2
node node-server.js
需要node来运行,没有安装的 话使用pkg install nodejs来安装

使用效果图 ,速度蛮快的 ,有兴趣的可以研究如何利用aria2来下载百度云文件,等你们来探索.


文件分享
KodExplorer
参考我的这篇文章：https://www.sqlsec.com/2019/11/kode.html

既然macOS可以直接搭建的话，那用Termux搭建的话应该也很简单吧：

Bash
# git clone 下载最新源码
git clone https://github.com/kalcaddle/KodExplorer/

# 到项目目录下
cd KodExplorer

# 启动php内置的WebServer
php -S 127.0.0.1:8080 -t .
git clone 国内网速可能比较慢 速度慢话 自行去官网找直链然后wget下载 速度会快很多

然后手机浏览器访问: http://127.0.0.1:8080 设置一下账号密码即可使用


实际体验还是很不错的，下面是主界面截图：


当然在局域网的情况下，通过IP地址，局域网的其他设备也是可以轻松访问到你的文件的，文件共享目的达成。

Termux-api
Termux:API，用于访问手机硬件,实现更多的可玩性,可以实现如下等功能:

访问电池信息
获取相机设备信息
获取本机设备信息
获取设置剪贴板信息
获取通讯录信息
获取设置手机短信
拨打号码
振动设备
安装Termux-api
Termux-api Google Play下载地址


补充一下链接如何在电脑上下载Google play上的应用？

安装Termux-api软件包
安装完Termux-apiAPP后,Termux里面必须安装对应的包后才可以实现操作手机底层.

Bash
pkg install termux-api
下面只列举一些可能会用到的,想要获取更多关于Termux-api的话,那就去参考官方文档.

获取电池信息
Bash
termux-battery-status
可以看到电池的-健康状况-电量百分比-温度情况等

Bash
{
  "health": "GOOD",
  "percentage": 67,
  "plugged": "UNPLUGGED",
  "status": "DISCHARGING",
  "temperature": 24.600000381469727
}
获取相机信息
Bash
termux-camera-info
获取与设置剪贴板
查看当前剪贴板内容

termux-clipboard-get
设置新的剪贴板内容

termux-clipboard-set PHP是世界上最好的语言
效果演示


获取通讯录列表
Bash
termux-contact-list

查看短信内容列表
Bash
termux-sms-inbox

发送短信
termux-sms-send
支持同时发送多个号码,实现群发的效果,官方介绍如下:

termux-sms-send -n number(s)  recipient number(s) - separate multiple numbers by commas
发送测试

Bash
termux-sms-send -n 10001 cxll

拨打电话
Bash
termux-telephony-call
拨打电话给10001中国电信,查看下话费有没有欠费~?

termux-telephony-call 10001

WiFi相关
获取当前WiFi连接信息

Bash
termux-wifi-connectioninfo
获取最近一次WiFi扫描信息

Bash
termux-wifi-scaninfo

小结
直接操作调动系统底层的话,可以通过编程来实现自动定时短信发送,语音播报等 DIY空间无线

一些无聊的尝试
一些无聊有趣的版块,如果你是一个正经讲究人,可以跳过这个板块以节约你的阅读时间.

nyancat 彩虹猫
彩虹貓（英语：Nyan Cat）是在2011年4月上传在Youtube 的视频，并且迅速爆红于网络，並在2011年YouTube浏览量最高的视频中排名第五.

Bash
pkg install nyancat
nyancat

什么鬼完全Get不到国外人的趣味点

终端二维码
Linux 命令行下的二维码,主要核心是这个网址:http://qrenco.de/

Bash
echo "http://www.sqlsec.com" |curl -F-=\<- qrenco.de


如果你不嫌无聊的话还可以扫描这个二维码,然后就打开我的博客了.
终端地图
一个基于nodejs编写的命令行下的地图.

npm install mapscii -g
mapscii
进入终端地图



操作方法
方向键 移动
a和z键 放大缩小
q键 退出
终端下的地图!讲究人~ 如果你足够无聊的话,还可以尝试能不能在这个地图上找到自己所在的位置.

其他没有写到的内容
安装Linux
甚至还可以在Termux里面在安装其他的Linux发行版.

由于本文篇幅已经过长了,这里不在叙述了,感兴趣,能折腾的自己去找一些资料.下面列出目前网友们用Termux可以成功安装的发行版:

Ubuntu
Arch
Fedora
Kali Nethunter
Ubuntu


Fedora


内网穿透
使用ngrok或者frp可以将Termux上面搭建的网站映射到外网上去,手机建站也不是不可能了.

Python Jupyter Notebook
Jupyter notebook（又称IPython notebook），支持运行超过40种编程语言。Python的一个强大的模块,成功安装的话可以实现比caddy的效果,支持web下的终端操作,支持代码高亮运行.由于这里需要安装大量文件,加上用户需求比较少,这一块感兴趣的话可以自己去探索.


下载工具
you-get
是一款命令行工具，用来下载网页中的视频、音频、图片，支持众多网站，包含 41 家国内主流视频、音乐网站，如 网易云音乐、AB
站、百度贴吧、斗鱼、熊猫、爱奇艺、凤凰视频、酷狗音乐、乐视、荔枝FM、秒拍、腾讯视频、优酷土豆、央视网、芒果TV
等等，只需一个命令就能直接下载视频、音频以及图片回来，并且可以自动合并视频。而对于有弹幕的网站，比如 B 站，还可以将弹幕下载回来

BaiduPCS-Go
仿 Linux shell 文件处理命令的百度网盘命令行客户端.

项目地址

可以完美在Termux上运行.


总结
相对来说 国外的Termux DIY的氛围比国内好很多,Youtube上的视频都有很高的播放量:


当然国内也有这么一批执着于Termux的玩家,只是相对来说还比较小众,写这篇文章只想让更多的人认识到Termux的生产力,使用Termux来做一些很cool的事情. 期待有更多Termux的优秀文章出现~


文章原作者: 国光
文章链接: https://www.sqlsec.com/2018/05/termux.html