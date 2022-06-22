1.access.log 为某公司真实日志  
======================== 
已知其公司为一家共享充电宝的互联网公司，主要业务地区位于西南地区，公司总部位于重庆。  
现今其怀疑公司IT系统遭遇到恶意攻击(但实际上也不完全确定)。尝试分析日志，并适当下结论。  
------------------------------------------------------------------------------------------------------  
第一步先查找具有攻击性的关键字  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/1.png)  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/2.png)  
##select关键字都在路径里，并没被用于攻击  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/3.png)  
##pwd出现在编码后的字段中，没问题  
2021.9.27访问量前10的IP汇总:  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/4.png)  
2021.9.28访问量前10的IP汇总:  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/5.png)  
ps:第一列为出现次数  
经过检测这些IP都来自于重庆 贵阳 珠海 广安 六盘水市 广安市  
使用360星图分析结果如下：  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/6.png)  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/7.png)  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/8.png)  
攻击大部分来自于敏感目录访问，判断结果为攻击失败
  
2.文件夹中的excel为某安全设备所导出的日志。尝试在Linux下分析报告：  
========================================================  
1） 不同安全告警标签的数量统计  
------------------------------------  
cat 1.csv |cut -d "," -f 11 |sort |uniq -d -c |sort -n -r  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/9.png)  

2） 攻击次数最多的IP地址TOP10  
-------------------------------------  
cat 1.csv |cut -d "," -f 2,11|sort |uniq -d -c |sort -n -r|awk  -F, '{printf "%-8s %-10s\n",$1,$2,$3}'|nl|head -10  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/10.png)  

3.netstat.txt与ps.txt为失陷主机的netstan -an与ps -aux的执行结果。尝试如下内容：（言之有理即可）  
================================================================================  
netstat.txt看出了活跃的Internet连接(服务器和已建立)以及活动的UNIX域套接字(服务器和已建立的)  
ps.txt可以看出用户名、进程ID、进程CPU占用率、进程内存占用率、进程所使用的虚存大小、实际内存大小、与进程关联的终端、进程状态、进程启动时间、进程使用的总CPU时间、正在执行的命令行命令  
Ss状态代表它是进程的领导者（之下有子进程）以及目前是睡眠状态  
<表示高优先级进程  N代表低优先级进程   l代表多进程   I代表空闲  

1） 找出恶意进程  
-------------------  
manager     4613  0.0  0.1   3140  2832 pts/0    S    20:24   0:00 ./tmp/awk.elf  
原因：这个首先是在tmp里整文件，就有可能是装木马准备反弹shell，然后再看文件后缀elf，断定他肯定是恶意进程  

2） 找出恶意的网络连接及恶意主机IP  
-----------------------------------------  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/11.png)  
pts表示远程登录，4444是kali默认的监听端口，很明显上传了木马在监听准备反弹shell  
再一看与22端口建立连接那就是ssh远程连接，因为已经ESTABLISHED，所以攻击者已经知道了受害者的账号密码  

3)后续深度排查思路，列出命令  
----------------------------------  
a.查看非 root 运行的进程  
ps -U root -u root -N  
b.检测隐藏进程  
![kali](https://github.com/WUBO512/wwbb/blob/main/%E7%AC%AC%E4%B8%89%E5%A4%A9/%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE/12.png)  
c.查看历史命令  
history 200  //200表示最近200条命令  
d.查看 uid 为 0 的账号  
awk -F: '($3==0)' /etc/passwd  
e.查看最近20条登录失败记录  
lastb -10 (-n)  
f.查看是否有新增用户  
less /etc/passwd  
假如被入侵，文件肯定会有所改动，可以查相关配置文件、以及tmp里的一些平时写马常用的后缀文件名等  
g.查看最近两天访问的文件  
find / -ctime 2 >  /tmp/1.txt  
h.查看最近两天有无文件权限或者所属组的修改  
find / -mtime 2  >  /tmp/1.txt  
如果kill恶意程序往往会遇到被kill掉的程序自启动，所以要检查一下计划任务(cron)  
crontab -u root -l  
cat /etc/crontab  
查看root用户计划任务  
ls /var/spool/cron/  
ls -l /etc/cron.*   
最后可以看看系统路径   echo $PATH

  
  
    

  
  



  
      


  

  
  
