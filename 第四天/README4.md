linux服务器  
==========  

1.资产划分  
--------------  

序号	知识产权	服务要求  
1	10.100.250.5	LNMP + discuz 论坛网站  
2	10.100.250.50	LAMP + wordpress博客  
3	172.29.10.10	Nginx代理服务器  
4	10.100.100.100	NFS 备份服务器  

2.要求  
--------  

1)域名 discuz.qt.com ----> 论坛网站  
wordpress.qt.com ----> wordpress博客  
172.29.10.10为Nginx代理服务  

2)NFS同步  
备份，discuz、wordpress网站的日志到NFS服务器下的两个/backup_logs目录下  

3)实现效果  
访问discuz.qt.com 能到达discuz论坛网站  
wordpress.qt.com 能到达wordpress博客  

3.拓扑图  
  

  
