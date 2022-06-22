#1.access.log 为某公司真实日志  
##已知其公司为一家共享充电宝的互联网公司，主要业务地区位于西南地区，公司总部位于重庆。  
##现今其怀疑公司IT系统遭遇到恶意攻击(但实际上也不完全确定)。尝试分析日志，并适当下结论。  
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
  
#2.文件夹中的excel为某安全设备所导出的日志。尝试在Linux下分析报告：  
1） 不同安全告警标签的数量统计  
  

  
  
