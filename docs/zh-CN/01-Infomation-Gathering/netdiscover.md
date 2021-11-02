# netdiscover

基于ARP的网络扫描工具netdiscover  
ARP是将IP地址转化物理地址的网络协议。通过该协议，可以判断某个IP地址是否被使用，从而发现网络中存活的主机。  
Kali Linux提供的netdiscover工具，就是借助该协议实施主机发现。它既可以以被动模式嗅探存活的主机，也可以以主动模式扫描主机。  
用户还可以根据网络稳定性，调整发包速度和数量。  
> 引用: https://blog.csdn.net/nzjdsds/article/details/82778531

# 命令格式
`netdiscover -r IP/24`

## 参数释义

    Netdiscover 0.8 [Active/passive ARP reconnaissance tool]  
    Written by: Jaime Penalba jpenalbae@gmail.com  

    Usage: netdiscover [-i device] [-r range | -l file | -p] [-m file] [-F filter] [-s time] [-c count] [-n node] [-dfPLNS]  
    -i device: your network device  
    -r range: scan a given range instead of auto scan. 192.168.6.0/24,/16,/8  
    -l file: scan the list of ranges contained into the given file  
    -p passive mode: do not send anything, only sniff  
    -m file: scan a list of known MACs and host names  
    -F filter: customize pcap filter expression (default: "arp")  
    -s time: time to sleep between each ARP request (milliseconds)  
    -c count: number of times to send each ARP request (for nets with packet loss)  
    -n node: last source IP octet used for scanning (from 2 to 253)  
    -d ignore home config files for autoscan and fast mode  
    -f enable fastmode scan, saves a lot of time, recommended for auto  
    -P print results in a format suitable for parsing by another program and stop after active scan  
    -L similar to -P but continue listening after the active scan is completed  
    -N Do not print header. Only valid when -P or -L is enabled.  
    -S enable sleep time suppression between each request (hardcore mode)  

    If -r, -l or -p are not enabled, netdiscover will scan for common LAN addresses.  

## 实例

### 查看网络信息
命令`ifconfig`
