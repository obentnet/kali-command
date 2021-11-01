# masscan
> masscan是一个快速的端口扫描工具  
> 引用链接:  
> https://blog.csdn.net/isinstance/article/details/50466194  
> https://blog.bbskali.cn/2443.html  

## 命令格式
`masscan 192.168.123.1/24 -p 80`  
### 命令解释
`masscan IP/24 -p 端口`

## 参数释义
    usage:  
    masscan -p80,8000-8100 10.0.0.0/8 --rate=10000  
    scan some web ports on 10.x.x.x at 10kpps  
    masscan --nmap  
    list those options that are compatible with nmap  
    masscan -p80 10.0.0.0/8 --banners -oB <filename>  
    save results of scan in binary format to <filename>  
    masscan --open --banners --readscan <filename> -oX <savefile>  
    read binary scan results in <filename> and save them as xml in <savefile>  

## 实例
### 扫描段内单个端口
`masscan 1.1.1.3/24 -p 80`
`masscan IP/24 -p 端口`

![img](/images/masscan/masscan-01.png)

### 扫描段内多个端口
`masscan 1.1.1.3/24 -p 22,80,443`
`masscan IP/24 -p 端口1,端口2,端口3`

![img](/images/masscan/masscan-02.png)

### 快速扫描

使用如上的的设置可以得到结果，但速度将是比较慢。正如已经讨论的那样，整体上masscan要快一点，所以让我们加快速度。  
默认情况下，Masscan扫描速度为每秒100个数据包，这是相当慢的。为了增加这一点，只需提供该-rate选项并指定一个值。  
扫描100个常见端口的B类子网，每秒100,000个数据包。  


`masscan 10.50.98.1/16  --top-ports 100 -rate 100000`
`masscan IP/16 --top0ports 每秒数据包 -rate 每秒数据包`

### 结果保存
`masscan 10.50.98.1/16  --top-ports 100 > results.txt`
`masscan IP/16 --top-ports 每秒数据包 > 文件名`

除此之外，您还具有以下输出选项：  

    -oX filename：输出到filename的XML。  
    -oG filename：输出到filename在的grepable格式。  