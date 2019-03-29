
# 1. which XX

查看 程序安装目录
例；which docker-compose

# 2. echo $PATH

系统PATH确认

# 3. export PATH=$PATH:/usr/local/XX

自分のパス追加

# 4. sudo ln -s /usr/local/bin/XX /usr/bin/XX

シンボリックリンク追加
例；sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

# 5. chmod +x XX

ファイルの実行権限追加
例：  chmod +x /usr/local/bin/docker-compose

# 6. rsync -av 元　先

ファイルコピー \
例： \
rsync -av /vagrant/src/heapdump-5* /vagrant_data/src/

# 7. df / free

メモリ、ディスク使用率確認

# 8. netstat -an | grep LISTEN

LISTENしているポート一覧取得.

# 9. netstat -tan | grep ':8081' | awk '{print $6}' | sort | uniq -c

接続状態の確認と接続元IPのカウントをnetstatで行う。(8081ポート)

# 10. netstat -tan | grep ':8081' | awk '{print $6}' │: 3100000 | sort | uniq -c

ポート8081の接続状態（接続数など） \
結果例： \
&nbsp;&nbsp;&nbsp;&nbsp;900 ESTABLISHED \
&nbsp;&nbsp;&nbsp;&nbsp;1 LISTEN \
&nbsp;&nbsp;&nbsp;&nbsp;1 TIME_WAIT

# 11. vmstat 10 3

10秒ごとに３回でシステム情報を取得して表示する。

# 12. systemctl status XX

プロセス運行情報 \
例：systemctl status redis

# 13. tail -n 50 -f /var/log/nodejs/nodejs.log

ログの後ろから５０行取得

# 14. service httpd status[start][restart][stop]

サービスの起動確認

# 15. SSH接続関連

## 15.1. ssh

### $ ssh -l jsmith remotehost.example.com

登录到远程主机

### $ ssh -v -l jsmith remotehost.example.com

调试ssh客户端

### $ ssh -V

显示ssh客户端版本

## 15.2. ssh-keygen

### ssh-keygen -t rsa -f ~/.ssh/id_rsa_ansible -N ""

秘密键/公开键文件生成（RSA加密，新密码为空）\
生成文件
  
 1. id_rsa_ansible
 2. id_rsa_ansible.pub（公开键）

## 15.3. ssh-keyscan

### ssh-keyscan github.com >> ~/.ssh/known_hosts

初回SSH接続時にでる Are you sure you want to continue connecting (yes/no)? という問いに対して yes と答えたのと同じように、指定したホストの公開鍵を取得して ~/.ssh/known_hosts ファイルへ追記してくれる。

## 15.4. ssh-copy-id

### ssh-copy-id -i ${identity_file} ${USER}@${target_host}

ssh-copy-id -i ~/.ssh/hoge.pub user01@192.168.10.15 \
sshの公開鍵認証の鍵登録（.ssh/authorized_keys）

# 16. visudo

visudoコマンドは管理者の権限でのみ操作できる。（/etc/sudoers）

# 17. file

## 17.1. file xx.text

显示文件的属性，编码等信息

# 18. 圧縮解凍関連

## 18.1. tar

### $ tar cvf archive_name.tar dirname/

创建一个新的tar文件

### $ tar xvf archive_name.tar

解压tar文件

### $ tar tvf archive_name.tar

查看tar文件

# 19. 検索関連

## 19.1. grep

### $ grep -i "the" demo_file

在文件中查找字符串(不区分大小写)

### $ grep -A 3 -i "example" demo_text

输出成功匹配的行，以及该行之后的三行

### $ grep -r "ramesh" *

在一个文件夹中递归查询包含指定字符串的文件

## 19.2. find

### $ find -iname "MyProgram.c"

查找指定文件名的文件(不区分大小写)

### $ find -iname "MyProgram.c" -exec md5sum {} \

对找到的文件执行某个命令

## $ find ~ -empty

查找home目录下的所有空文件

# 20. sed

## $ sed 's/.$//' filename

当你将Dos系统中的文件复制到Unix/Linux后，这个文件每行都会以\r\n结尾，sed可以轻易将其转换为Unix格式的文件，使用\n结尾的文件

## $ sed -n '1!G; h; p' filename

反转文件内容并输出

## $ sed '/./=' thegeekstuff.txt | sed 'N; s/\n/ /'

为非空行添加行号

# 21. awk

## $ awk '!($0 in array) { array[$0]; print}' temp

删除重复行

## $ awk -F ':' '$3=$4' /etc/passwd

打印/etc/passwd中所有包含同样的uid和gid的行

## $ awk '{print $2,$5;}' employee.txt

打印文件中的指定部分的字段

# 22. vim

## $ vim +10 filename.txt

打开文件并跳到第10行

## $ vim +/search-term filename.txt

打开文件跳到第一个匹配的行

## $ vim -R /etc/passwd

以只读模式打开文件

# 23. diff

## $ diff -w name_list.txt name_list_new.txt

比较的时候忽略空白符

# 24. sort

## $ sort names.txt

以升序对文件内容排序

## $ sort -r names.txt

以降序对文件内容排序

## $ sort -t: -k 3n /etc/passwd | more

以第三个字段对/etc/passwd的内容排序

# 25. export

## $ export | grep ORCALE

输出跟字符串oracle匹配的环境变量 \
declare -x ORACLE_BASE="/u01/app/oracle" \
declare -x ORACLE_HOME="/u01/app/oracle/product/10.2.0" \
declare -x ORACLE_SID="med" \
declare -x ORACLE_TERM="xterm"

## $ export ORACLE_HOME=/u01/app/oracle/product/10.2.0

设置全局环境变量

# 26. xargs

## $ ls *.jpg | xargs -n1 -i cp {} /external-hard-drive/directory

将所有图片文件拷贝到外部驱动器

## $ find / -name *.jpg -type f -print | xargs tar -cvzf images.tar.gz

将系统中所有jpd文件压缩打包

## $ cat url-list.txt | xargs wget –c

下载文件中列出的所有url对应的页面

# 27. ls

## $ ls -lh

以易读的方式显示文件大小(显示为MB,GB...) \
-rw-r----- 1 ramesh team-dev 8.9M Jun 12 15:27 arch-linux.txt.gz

## $ ls -ltr

以最后修改时间升序列出文件

## $ ls -F

在文件名后面显示文件类型

# 28. pwd

输出当前工作目录

# 29. cd

cd -可以在最近工作的两个目录间切换 \
使用shopt -s cdspell可以设置自动对cd命令进行拼写检查

# 30. gzip

## $ gzip test.txt

创建一个*.gz的压缩文件

## $ gzip -d test.txt.gz

解压*.gz文件

## $ gzip -l *.gz

     compressed        uncompressed  ratio uncompressed_name
          23709               97975  75.8% asp-patch-rpms.txt
显示压缩的比率

# 31. bzip2

## $ bzip2 test.txt

创建*.bz2压缩文件

## bzip2 -d test.txt.bz2

解压*.bz2文件

# 32. uzip

## $ unzip test.zip

解压*.zip文件

## $ unzip -l jasper.zip

查看*.zip文件的内容 \
Archive:  jasper.zip

Length     Date   Time    Name
--------    ----   ----    ----
40995  11-30-98 23:50   META-INF/MANIFEST.MF
32169  08-25-98 21:07   classes_
15964  08-25-98 21:07   classes_names
10542  08-25-98 21:07   classes_ncomp

# 33. shutdown

## $ shutdown -h now

关闭系统并立即关机

## $ shutdown -h +10

10分钟后关机

## $ shutdown -r now

重启

## $ shutdown -Fr now

重启期间强制进行系统检查

# 34. ftp

## $ ftp IP/hostname

ftp命令和sftp命令的用法基本相似连接ftp服务器并下载多个文件 \

ftp> mget *.html \
ftp> mls *.html - \
显示远程主机上文件列表 \
/ftptest/features.html \
/ftptest/index.html \
/ftptest/othertools.html \
/ftptest/samplereport.html \
/ftptest/usage.html

# 35. crontab

## $ crontab -u john -l

查看某个用户的crontab入口

## */10 **** /home/ramesh/check-disk-space

设置一个每十分钟执行一次的计划任务

# 36. service

## $ service ssh status

查看服务状态

## $ service --status-all

查看所有服务状态

## $ service ssh restart

重启服务

# 37. ps

## $ ps -ef | more

查看当前正在运行的所有进程

## $ ps -efH | more

以树状结构显示当前正在运行的进程，H选项表示显示进程的层次结构

# 38. free

## $ free

默认情况下free会以字节为单位输出内存的使用量

## $ free -g

-g为GB，-m为MB，-k为KB，-b为字节

## free -t

如果你想查看所有内存的汇总，请使用-t选项，使用这个选项会在输出中加一个汇总行 \
Total:     7566584    1592148    5974436

# 39. top

top命令会显示当前系统中占用资源最多的一些进程（默认以CPU占用率排序）如果你想改变排序方式，可以在结果列表中点击O（大写字母O）会显示所有可用于排序的列，这个时候你就可以选择你想排序的列

## $ top -u oracle

如果只想显示某个特定用户的进程，可以使用-u选项

# 40. df

## $ df -k

显示文件系统的磁盘使用情况，默认情况下df -k 将以字节为单位输出磁盘的使用量

## $ df -h

使用-h选项可以以更符合阅读习惯的方式显示磁盘使用量

## $ df -T

使用-T选项显示文件系统类型

# 41. kill

kill用于终止一个进程。一般我们会先用ps -ef查找某个进程得到它的进程号，然后再使用kill -9 进程号终止该进程。你还可以使用killall、pkill、xkill来终止进程

$ ps -ef | grep vim \
$ kill -9 7243

# 42. rm

## $ rm -i filename.txt

删除文件前先确认

## $ rm -i file*

在文件名中使用shell的元字符会非常有用。删除文件前先打印文件名并进行确认

## $ rm -r example

递归删除文件夹下所有文件，并删除该文件夹

# 43. cp

## $ cp -p file1 file2

拷贝文件1到文件2，并保持文件的权限、属主和时间戳

## $ cp -i file1 file2

拷贝file1到file2，如果file2存在会提示是否覆盖

# 44. mv

## $ mv -i file1 file2

将文件名file1重命名为file2，如果file2存在则提示是否覆盖 \
注意如果使用-f选项则不会进行提示

## $ mv -v file1 file2

-v会输出重命名的过程，当文件名中包含通配符时，这个选项会非常方便

# 45. cat

## $ cat file1 file2

一次查看多个文件的内容，下面的命令会先打印file1的内容，然后打印file2的内容

## $ cat -n /etc/logrotate.conf

-n命令可以在每行的前面加上行号

# 46. mount

> mkdir /u01 \
> mount /dev/sdb1 /u01

如果要挂载一个文件系统，需要先创建一个目录，然后将这个文件系统挂载到这个目录上

> /dev/sdb1 /u01 ext2 defaults 0 2

也可以把它添加到fstab中进行自动挂载，这样任何时候系统重启的时候，文件系统都会被加载

# 47. chmod

## $ chmod ug+rwx file.txt

给指定文件的属主和属组所有权限(包括读、写、执行)

## $ chmod g-rwx file.txt

删除指定文件的属组的所有权限

## $ chmod -R ug+rwx file.txt

修改目录的权限，以及递归修改目录下面所有文件和子目录的权限

# 48. chown [-R] 属主名：属组名 文件名

## $ chown oracle:dba dbora.sh

同时将某个文件的属主改为oracle，属组改为db

## $ chown -R oracle:dba /home/oracle

使用-R选项对目录和目录下的文件进行递归修改

# 49. chgrp [-R] 属组名 文件名

更改文件属组

# 50. passwd

passwd用于在命令行修改密码，使用这个命令会要求你先输入旧密码，然后输入新密码

## passwd USERNAME

超级用户可以用这个命令修改其他用户的密码，这个时候不需要输入用户的密码

## passwd -d USERNAME

passwd还可以删除某个用户的密码，这个命令只有root用户才能操作，删除密码后，这个用户不需要输入密码就可以登录到系统

# 51. mkdir

## $ mkdir ~/temp

在home目录下创建一个名为temp的目录

## $ mkdir -p dir1/dir2/dir3/dir4/

使用-p选项可以创建一个路径上所有不存在的目录

# 52. ifconfig

ifconfig用于查看和配置Linux系统的网络接口

## $ ifconfig -a

查看所有网络接口及其状态

## $ ifconfig eth0 up/down

使用up和down命令启动或停止某个接口

# 53. uname

uname可以显示一些重要的系统信息，例如内核名称、主机名、内核版本号、处理器类型之类的信息

## $ uname -a

Linux john-laptop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

# 54. whereis

当你不知道某个命令的位置时可以使用whereis命令，下面使用whereis查找ls的位置

## $ whereis ls

ls: /bin/ls /usr/share/man/man1/ls.1.gz /usr/share/man/man1p/ls.1p.gz

## $ whereis -u -B /tmp -f lsmk

当你想查找某个可执行程序的位置，但这个程序又不在whereis的默认目录下，你可以使用-B选项，并指定目录作为这个选项的参数。下面的命令在/tmp目录下查找lsmk命令

lsmk: /tmp/lsmk

# 55. whatis

wathis显示某个命令的描述信息

## $ whatis ls

ls (1)  - list directory contents

## $ whatis ifconfig

ifconfig (8)         - configure a network interface

# 56. locate

locate命名可以显示某个指定文件（或一组文件）的路径，它会使用由updatedb创建的数据库

下面的命令会显示系统中所有包含crontab字符串的文件

$ locate crontab
/etc/anacrontab
/etc/crontab
/usr/bin/crontab
/usr/share/doc/cron/examples/crontab2english.pl.gz
/usr/share/man/man1/crontab.1.gz
/usr/share/man/man5/anacrontab.5.gz
/usr/share/man/man5/crontab.5.gz
/usr/share/vim/vim72/syntax/crontab.vim

# 57. man

## $ man crontab

显示某个命令的man页面

## $ man SECTION-NUMBER commandname

有些命令可能会有多个man页面，每个man页面对应一种命令类型 \
man页面一般可以分为8种命令类型

1. 用户命令
2. 系统调用
3. c库函数
4. 设备与网络接口
5. 文件格式
6. 游戏与屏保
7. 环境、表、宏
8. 系统管理员命令和后台运行命令

例如，我们执行whatis crontab，你可以看到crontab有两个命令类型1和5，所以我们可以通过下面的命令查看命令类型5的man页面

$ whatis crontab
crontab (1)          - maintain crontab files for individual users (V3)
crontab (5)          - tables for driving cron

$ man 5 crontab

# 58. tail

## $ tail filename.txt

tail命令默认显示文件最后的10行文本

## $ tail -n N filename.txt

你可以使用-n选项指定要显示的行数

## $ tail -f log-file

你也可以使用-f选项进行实时查看，这个命令执行后会等待，如果有新行添加到文件尾部，它会继续输出新的行，在查看日志时这个选项会非常有用。你可以通过CTRL-C终止命令的执行

# 59. less

## $ less huge-log-file.log

这个命名可以在不加载整个文件的前提下显示文件内容，在查看大型日志文件的时候这个命令会非常有用

当你用less命令打开某个文件时，下面两个按键会给你带来很多帮助，他们用于向前和向后滚屏

CTRL+F – forward one window \
CTRL+B – backward one window

# 60. su

## $ su - USERNAME

su命令用于切换用户账号，超级用户使用这个命令可以切换到任何其他用户而不用输入密码

## $ su - raj -c 'ls'

用另外一个用户名执行一个命令 \
示例中用户john使用raj用户名执行ls命令，执行完后返回john的账号

## $ su -s 'SHELLNAME' USERNAME

用指定用户登录，并且使用指定的shell程序，而不用默认的

# 61. mysql

## $ mysql -u root -p -h 192.168.1.2

mysql可能是Linux上使用最广泛的数据库，即使你没有在你的服务器上安装mysql，你也可以使用mysql客户端连接到远程的mysql服务器

连接一个远程数据库，需要输入密码

## $ mysql -u root -p

连接本地数据库

你也可以在命令行中输入数据库密码，只需要在-p后面加上密码作为参数，可以直接写在p后面而不用加空格

# 62. yum

## $ yum install httpd

使用yum安装apache

## $ yum update httpd

更新apache

## $ yum remove httpd

卸载/删除apache

# 63. rpm

## rpm -ivh httpd-2.2.3-22.0.1.el5.i386.rpm

使用rpm安装apache

## rpm -uvh httpd-2.2.3-22.0.1.el5.i386.rpm

更新apache

## rpm -ev httpd

卸载/删除apache

# 64. ping

## $ ping -c 5 gmail.com

ping一个远程主机，只发5个数据包

# 65. date

## date -s "01/31/2010 23:59:53"

设置系统日期

当你修改了系统时间，你需要同步硬件时间和系统时间
> # hwclock –systohc
> # hwclock --systohc –utc

# 66. wget

## $ wget XXX/sourceforge/nagios/nagios-3.2.1.tar.gz

使用wget从网上下载软件、音乐、视频

## $ wget -O taglist.zip XXX/download_script.php?src_id=7701

下载文件并以指定的文件名保存文件
