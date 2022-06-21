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
#6.确认自防火墙状态，并设置为"引导启动"  
service iptables status # 查看防火墙状态
chkconfigtables on #设置防火墙ip自启




  

