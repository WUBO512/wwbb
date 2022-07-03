Linux服务搭建
============

1.LAMP + wordpress博客
------------------------------
安装宝塔面板
---------------
yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh
安装环境：
-----------
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/1.png)
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/2.png)
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/3.png)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.Nginx反向代理服务器配置命令
sudo rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
yum -y install nginx
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/4.png)
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/5.png)
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/6.png)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
测试访问：
-----------
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/7.png)
安装所需软件包：
------------------
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/8.png)
创建文件夹：
-------------
mkdir /home/test
chmod -R 777 /home/test/
cd /home/test/
---------------------------------
将客户端信息添加到文件中：
---------------------------------
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/9.png)
关闭selinux和防火墙：
-------------------------
setenforce 0
systemctl stop firewalld
systemctl disable firewalld
--------------------------------
搭建客户端：
--------------
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/10.png)
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/11.png)
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
测试：
![centos7](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%BA%94%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/12.png)