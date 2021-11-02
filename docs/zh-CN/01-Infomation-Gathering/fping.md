# fping

fping程序类似于ping（ping是通过ICMP（网络控制信息协议InternetControl Message Protocol）协议回复请求以检测主机是否存在）。fping与ping不同的地方在于，fping可以在命令行中指定要ping的主机数量范围，也可以指定含有要ping的主机列表文件。

与ping要等待某一主机连接超时或发回反馈信息不同，fping给一个主机发送完数据包后，马上给下一个主机发送数据包，实现多主机同时ping。如果某一主机ping通，则此主机将被打上标记，并从等待列表中移除，如果没ping通，说明主机无法到达，主机仍然留在等待列表中，等待后续操作。

Fping类似于ping，但比ping强大。fping与ping不同的地方在于，fping可以在命令行中指定要ping的主机数量范围，也可以指定含有要ping的主机列表文件。
与ping要等待某一主机连接超时或发回反馈信息不同，fping给一个主机发送完数据包后，马上给下一个主机发送数据包，实现多主机同时ping。如果某一主机ping通，则此主机将被打上标记，并从等待列表中移除，如果没ping通，说明主机无法到达，主机仍然留在等待列表中，等待后续操作。

> 引用: https://blog.csdn.net/baidu_19348579/article/details/109442692

## 命令格式
`fping [options] [targets...]`

## 参数释义
用法: `fping [options] [targets...]`

    Probing options:
       -4, --ipv4         只ping ipv4的地址
       -6, --ipv6         只ping ipv6的地址
       -b, --size=BYTES   ping 数据包的大小。（默认为56）
       -B, --backoff=N    设置指数反馈因子到f
       -c, --count=N      ping每个目标的次数 (默认为1)
       -f, --file=FILE    从文件获取目标列表( - 表示从标准输入)(不能与 -g 同时使用)
       -g, --generate     通过指定开始和结束地址来生成目标列表 (只有在 -f 未指定时)
                          (在目标列表中提供起始和结束IP，或CIDR地址)
                          (举例： fping -g 192.168.1.0 192.168.1.255 或 fping -g 192.168.1.0/24)
       -H, --ttl=N        set the IP TTL value (Time To Live hops)
       -I, --iface=IFACE  绑定到自定义端口
       -l, --loop         天长地久模式: 一直发到电脑爆炸
       -m, --all          使用提供的主机名的所有IP (例如: IPv4 and IPv6), 与 -A 一同使用
       -M, --dontfrag     set the Don't Fragment flag
       -O, --tos=N        set the type of service (tos) flag on the ICMP packets
       -p, --period=MSEC  interval between ping packets to one target (in ms)
                          (in loop and count modes, default: 1000 ms)
       -r, --retry=N      number of retries (default: 3)
       -R, --random       random packet data (to foil link data compression)
       -S, --src=IP       set source address
       -t, --timeout=MSEC individual target initial timeout (default: 500 ms,
                          except with -l/-c/-C, where it's the -p period up to 2000 ms)
    
    Output options:
       -a, --alive        显示可ping通的目标
       -A, --addr         将目标以ip地址的形式显示
       -C, --vcount=N     同-c，返回的结果为冗长格式
       -D, --timestamp    print timestamp before each output line
       -e, --elapsed      显示返回数据包所费时间
       -i, --interval=MSEC  发送ping数据包之间的间隔（默认值：10毫秒）
       -n, --name         show targets by name (-d is equivalent)
       -N, --netdata      output compatible for netdata (-l -Q are required)
       -o, --outage       show the accumulated outage time (lost packets * packet interval)
       -q, --quiet        quiet (don't show per-target/per-ping results)
       -Q, --squiet=SECS  same as -q, but show summary every n seconds
       -s, --stats        print final stats
       -u, --unreach      show targets that are unreachable
       -v, --version      show version
       -x, --reachable=N  shows if >=N hosts are reachable or not

> 部分参考：https://blog.csdn.net/weixin_49071539/article/details/109800584

## 实例
### 基本命令
命令: `fping 1.1.1.3`  

![img](/images/fping/fping-01.png)

1.1.1.3是我校的内网的网关，自然就成了我的靶机了😅

### ip列表
命令: `fping -f FILENAME`

### IP范围
命令: `fping -g [startIP] [endIP]`

![img](/images/fping/fping-02.png)