# hping3
<warning style="color:red;">本页未被完善！请谨慎参考！</warning>  

Hping3 是一个命令行下使用的 TCP/IP 数据包组装/凾析工具，通常 web服务会用来做压力测试使用，也可以迚行 DOS 攻击的实验。同样 Hping 只能每次扫描一个目标。
kali常用攻击手段之Hping3攻击
> 引用: https://blog.csdn.net/qq_42877870/article/details/105027743

## 命令格式：
`hping3 host [options]`
## 参数释义
    usage: hping3 host [options]
      -h  --help      show this help
      -v  --version   show version
      -c  --count     packet count
      -i  --interval  wait (uX for X microseconds, for example -i u1000)
          --fast      alias for -i u10000 (10 packets for second)
          --faster    alias for -i u1000 (100 packets for second)
          --flood      sent packets as fast as possible. Don't show replies.
      -n  --numeric   numeric output
      -q  --quiet     quiet
      -I  --interface interface name (otherwise default routing interface)
      -V  --verbose   verbose mode
      -D  --debug     debugging info
      -z  --bind      bind ctrl+z to ttl           (default to dst port)
      -Z  --unbind    unbind ctrl+z
          --beep      beep for every matching packet received
    Mode
      default mode     TCP
      -0  --rawip      RAW IP mode
      -1  --icmp       ICMP mode
      -2  --udp        UDP mode
      -8  --scan       SCAN mode.
                       Example: hping --scan 1-30,70-90 -S www.target.host
      -9  --listen     listen mode
    IP
      -a  --spoof      spoof source address
      --rand-dest      random destionation address mode. see the man.
      --rand-source    random source address mode. see the man.
      -t  --ttl        ttl (default 64)
      -N  --id         id (default random)
      -W  --winid      use win* id byte ordering
      -r  --rel        relativize id field          (to estimate host traffic)
      -f  --frag       split packets in more frag.  (may pass weak acl)
      -x  --morefrag   set more fragments flag
      -y  --dontfrag   set don't fragment flag
      -g  --fragoff    set the fragment offset
      -m  --mtu        set virtual mtu, implies --frag if packet size > mtu
      -o  --tos        type of service (default 0x00), try --tos help
      -G  --rroute     includes RECORD_ROUTE option and display the route buffer
      --lsrr           loose source routing and record route
      --ssrr           strict source routing and record route
      -H  --ipproto    set the IP protocol field, only in RAW IP mode
    ICMP
      -C  --icmptype   icmp type (default echo request)
      -K  --icmpcode   icmp code (default 0)
          --force-icmp send all icmp types (default send only supported types)
          --icmp-gw    set gateway address for ICMP redirect (default 0.0.0.0)
          --icmp-ts    Alias for --icmp --icmptype 13 (ICMP timestamp)
          --icmp-addr  Alias for --icmp --icmptype 17 (ICMP address subnet mask)
          --icmp-help  display help for others icmp options
    UDP/TCP
      -s  --baseport   base source port             (default random)
      -p  --destport   [+][+]<port> destination port(default 0) ctrl+z inc/dec
      -k  --keep       keep still source port
      -w  --win        winsize (default 64)
      -O  --tcpoff     set fake tcp data offset     (instead of tcphdrlen / 4)
      -Q  --seqnum     shows only tcp sequence number
      -b  --badcksum   (try to) send packets with a bad IP checksum
                       many systems will fix the IP checksum sending the packet
                       so you'll get bad UDP/TCP checksum instead.
      -M  --setseq     set TCP sequence number
      -L  --setack     set TCP ack
      -F  --fin        set FIN flag
      -S  --syn        set SYN flag
      -R  --rst        set RST flag
      -P  --push       set PUSH flag
      -A  --ack        set ACK flag
      -U  --urg        set URG flag
      -X  --xmas       set X unused flag (0x40)
      -Y  --ymas       set Y unused flag (0x80)
      --tcpexitcode    use last tcp->th_flags as exit code
      --tcp-mss        enable the TCP MSS option with the given value
      --tcp-timestamp  enable the TCP timestamp option to guess the HZ/uptime
    Common
      -d  --data       data size                    (default is 0)
      -E  --file       data from file
      -e  --sign       add 'signature'
      -j  --dump       dump packets in hex
      -J  --print      dump printable characters
      -B  --safe       enable 'safe' protocol
      -u  --end        tell you when --file reached EOF and prevent rewind
      -T  --traceroute traceroute mode              (implies --bind and --ttl 1)
      --tr-stop        Exit when receive the first not ICMP in traceroute mode
      --tr-keep-ttl    Keep the source TTL fixed, useful to monitor just one hop
      --tr-no-rtt       Don't calculate/show RTT information in traceroute mode
    ARS packet description (new, unstable)
      --apd-send       Send the packet described with APD (see docs/APD.txt)

## 实例
`hping3 -c 100000 -d 120 -S -w 64 -p 80 --flood --rand-source rzgx.com`  

![img](/images/hping3/hping3-01.png)

-c 1000 = 发送的数据包的数量。  

-d 120 = 发送到目标机器的每个数据包的大小。单位是字节 -S = 只发送 SYN 数据包。  

-w 64 = TCP 窗口大小。  

-p 80 = 目的地端口(80 是 WEB 端口)。你在这里可以使用仸何端口。  

–flood = 尽可能快地发送数据包，丌需要考虑显示入站回复。洪水攻击模式  

> 要注意的是,输入命令回车后,Terminal终端并不会实时更新，是在后台持续ping的  
> 可以试用`top`命令查看机器的状态  
> 当你觉得打的差不多的时候，就可以按`Ctrl + C`暂停ping  