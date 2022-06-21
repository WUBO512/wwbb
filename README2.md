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
#20.  
    

  

