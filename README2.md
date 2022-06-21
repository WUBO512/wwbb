#1.kali源的配置文件全路径  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/1.png)  
#2.后缀为deb以及rpm的安装包安装命令分别为?  
后缀为deb：dpkg -i 名称.deb  
后缀为rpm：rpm -ivh 名称.rpm
#3.在kali安装virtualbox的时候，需要先查看本机内核，命令为?查看最新内核命令为?
uname -srm  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/3.png) 
#4.使用root用户远程连接服务器身份  
ssh root@42.192.66.85  
前提是服务器允许root登录  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/4.png)  
#5.查看selinux 状态  
sestatus  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/55.png)  
#6.确认自防火墙状态，并设置为"引导启动"  
service iptables status # 查看防火墙状态
chkconfigtables on #设置防火墙ip自启  
#7.建立用户QT,并指定用户uid为0，且用户组为QT  
groupadd QT # 创建QT组
useradd QT -g QT # 创建QT用户并添加到QT组
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/5.png)
修改QT密码数据中的第三段为0  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/6.png)  
切换到QT用户输入id  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/7.png)  
#8.退出root用户，使用QT身份远程连接服务器，并确定用户身份  
修改ssh服务器配置，查找并修改 PermitRootLogin yes #rootLogin  
#9.建立目录名为farma的文件夹  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/8.png)  
#10. 查看新建立的文件夹的权限及属主属组  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/9.png)  
权限为所有者:读写执行;所属者:读执行;其他人:执行  
所属:root  
#11.将/etc/shadow文件拷贝到farma文件夹中，并改名为test  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/10.png)  
#12.使用绝对路径的方式进入到farm文件夹中  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/11.png)  
#13. 使用相对路径进入到farm文件夹中
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/12.png)  
#14.查看文件内容  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/13.png)  
#15.查看test文件的前3行  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/14.png)  
#16.查看test文件后5行  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/15.png)  
#17.查看test文件7-10行  
sed -n 7,10p test  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/16.png)  
#18.查看系统的全部进程并将结果保存到/var/farm目录中，命名为jc.txt  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/17.png)  
#19. 在jc.txt中，文件尾部添加一行内容：coding by QT! (至少2种方式)  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/18.png)  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/19.png)  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/20.png)  
#20.查看系统的进程，并找出与ssh相关的内容，结束除/usr/sbin/sshd外所有ssh进程，并确认是通过服务器端断开的访问连接.(使用一行命令)  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/21.png)  
ps -ef | grep ssh & kill  1030 583  3043 3102  
#21.在系统中另建立一个名为farm1的用户,使其拥有sudo权限  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/22.png)  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/23.png)  
#22.切换至farm1用户  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/24.png)  
23.将farm文件夹中所有文件的属主改为farm1，属组改为QT1  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/25.png)  
24.查找系统中名字以pass字段开头的文件(多种方式)   
find / -name "pass*"  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/26.png)  
25.查找/var目录中的文件，且过去一天内被修改过权限  
find /var -ctime 1  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/27.png)  
26.查找/etc目录中，文件包含password内容的文件 (多种方式)  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/28.png)  
find / -name "*.*" | xargs grep "password" # 指定目录为 / 后，*.* 为匹配所有文件，xargs 命令是为了方便处理过长数据  
27.使用一行命令提取主机中的所有可登录用户，并按照字母正常顺序排序，结果保存至家目录中的user.txt中  
cat /etc/passwd | grep -E 'bin/csh|bin/bash' > a.txt && sort a.txt > user.txt  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/29.png)  
28.查找主机中所有uid为0的用户  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/30.png)  
29.将test文件中的所有:替换为+  
vim test #打开文件  
%s/:/+/g  #替换文中所有：为+  
30.切割测试文件保存为每5个行为一个文件  
split -l 5 test test -d  
31.安装名为nginx的服务，并启动该服务  
wget http://nginx.org/download/nginx-1.16.1.tar.gz  //下载  
tar -xvf nginx-1.16.1.tar.gz -C /opt/  //解压  
./configure --prefix=/opt/nginx --without-http_rewrite_module   //设置编译路径  
make && make install  //编译  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/31.png)  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/32.png)  
32.配置一个计划任务，用户root，每隔5小时的第46分钟执行命令echo hello >/root/hello.txt  
46*/5***root echo hello >/root/hello.txt  # */5表示每隔5小时 46表示每小时的第46分钟  ***表示每天  
33.在文件/etc/passwd中查找所有包含字符串oo或者ai的行。将找出的行按照原文的先后顺序拷贝到/root/cc文件中  
cat /etc/passwd | grep -E 'oo|ai' > /root/cc  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/33.png)  
34.删除掉/var/log/audit/audit.log,然后数据恢复到/opt中  
lsof | grep /var/log/audit/audit.log  
cp /proc/585/fd/5 /opt/audit.log  
ll /opt/audit.log  
35.查看服务名为Nginx所对应的进程id，再通过查询到的该id查找该进程打开的文件  
ps -ef | grep 'nginx'  #进程后显示的文件路径即为该进程打开的文件  
36.查看网络连接状态，并提取出来源IP以及PID号（一行命令）  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/34.png)  
##实战能力  
cat test | cut -d "/" -f 3-4 > wubo.txt && sed 's/$/\/login.action /g' wubo.txt > wuwu.txt  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BEday2/35.png)  








  
    

  

