# netmask
netmaks可以在 IP范围、子网掩码、cidr、cisco等格式中互相转换，并且提供了IP地址的点分十进制、16进制、8进制、2进制之间的互相转换

> 引用：https://blog.csdn.net/It_Roo/article/details/105846181

## 命令格式
`netmask spec [spec ...]`

## 参数释义
    netmask: invalid option -- 'e'  
    netmask: invalid option -- 'l'  
    netmask: invalid option -- 'p'  
    This is netmask, an address netmask generation utility  
    Usage: netmask spec [spec ...]  
      -h, --help                    Print a summary of the options  
      -v, --version                 Print the version number  
      -d, --debug                   Print status/progress information  
      -s, --standard                Output address/netmask pairs  
      -c, --cidr                    Output CIDR format address lists  
      -i, --cisco                   Output Cisco style address lists  
      -r, --range                   Output ip address ranges  
      -x, --hex                     Output address/netmask pairs in hex  
      -o, --octal                   Output address/netmask pairs in octal  
      -b, --binary                  Output address/netmask pairs in binary  
      -n, --nodns                   Disable DNS lookups for addresses  
      -f, --files                   Treat arguments as input files  
    Definitions:  
      a spec can be any of:  
        address  
        address:address  
        address:+address  
        address/mask  
      an address can be any of:  
        N           decimal number  
        0N          octal number  
        0xN         hex number  
        N.N.N.N     dotted quad  
        hostname    dns domain name  
      a mask is the number of bits set to one from the left  

## 实例
### 查看版本ip地址对应信息
命令: `netmask -v IP or IP:IP`  

![img](/images/netmask/netmask-01.png)

### 查看状态信息
命令: `netmask -d IP or IP:IP`  

![img](/images/netmask/netmask-02.png)

### cidr转换
命令: `netmask -c IP or IP:IP`  

![img](/images/netmask/netmask-03.png)

### 查看地址和掩码
命令: `netmask -s IP or IP:IP`  

![img](/images/netmask/netmask-04.png)

### cisco反向掩码转换
命令: `netmask -i IP or IP:IP`  

![img](/images/netmask/netmask-05.png)

### 查看ip地址范围

命令: `netmask -r IP or IP:IP`  

![img](/images/netmask/netmask-06.png)

### 十六进制转换

命令: `netmask -x IP or IP:IP`  

![img](/images/netmask/netmask-07.png)

### 八进制转换

命令: `netmask -o IP or IP:IP`  

![img](/images/netmask/netmask-08.png)

### 二进制转换

命令: `netmask -b IP or IP:IP`  

![img](/images/netmask/netmask-09.png)

### dns查找

命令: `netmask -n IP or IP:IP`  

![img](/images/netmask/netmask-10.png)