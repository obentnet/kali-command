# 前言
> 一个记录kali学习的小笔记  

kali是一个功能性比较强的linux系统。  
笔记下的所有教程均在VMware Workstations环境下的kali系统中内进行。  
如果你也想体验体验,可以先去下载Kali.  

笔记工具的目录是按照kali开始菜单的分类排的。  
我觉得比较方便点，慢慢来，慢慢学。  

此宝典工程量巨大，如果发现任何问题，请及时联系[obent@qq.com](mailto:obent@qq.com)反馈!

*** 本教程初衷是为了大家学会使用kali内的工具，请不要用于非法行为内！***

## 鸣谢
如果你对本项目感兴趣，或者本项目帮助了你。  
请赞助我们！  
![donate](https://cdn.jsdelivr.net/gh/obentnet/kali-command/cdn/images/donate.png)

### 鸣谢名单
| 昵称 | 金额 | 时间 |
| --------   | :-----  | :----- |
| 奇趣保罗 | 5￥ | 2021-11-1 |


# 奇淫巧技

## Kali的下载  
Kali官网：[kali.org](https://kali.org/)  
选择你喜欢的安装方式,然后安装完进系统就可以了。  
我这里使用的是VMware Workstations,下载完安装包，解压出来然后在vm中导入虚拟机就可以了。  
> 稍微吐槽一下,默认账户密码为啥kali不写在文档里，我找了半天.

## Kali更换语言
这里是Kali2021.3版本,默认为英文.如果看不惯，可以换中文。  
我这个版本虚拟机内是有中文语言包的，然后更换中文也很简单。  
直接打开Terminal终端，输入`dpkg-reconfigure locales`并回车

![dpkg-reconfigure locales](https://cdn.jsdelivr.net/gh/obentnet/kali-command/cdn/images/skills-kali-change-language-01.png)

按一下空格，进入后一直往下找，找到 `zh_CN.UTF-8 UTF-8` 后,空格选中后回车两次  
选中小键盘往下选择`zh_CN.UTF-8 UTF-8`  

![dpkg-reconfigure locales](https://cdn.jsdelivr.net/gh/obentnet/kali-command/cdn/images/skills-kali-change-language-02.png)  

回车，然后就会开始处理，等到出现 `Generation complete.`这行字的时候，  
输入`sudo reboot`重启kali，再次进入系统你就会发现已经是中文了。  

## Kali打开ssh服务
这个就很简单了，  
因为kali默认策略，不用改ssh参数，  
直接terminal命令：  
`service ssh start`  
或  
`/etc/init.d/ssh start`  
就会看到服务开启了。  
输入: `service ssh status`来检查ssh服务是否正常运行。  
Windows端可以使用cmd来进行ssh操控。  
命令格式：  
`ssh -p22 kali@127.0.0.1`  

![img](https://cdn.jsdelivr.net/gh/obentnet/kali-command/cdn/images/skills-kali-open-ssh-service-windows.png)  

当然更建议使用putty等工具来进行远程。  

# 01-信息收集
> 信息收集 Infomation Gethering.  
## 存活主机识别

| 分类        | 工具   | 
| --------   | :-----  |
| 存活主机识别 | [arping](/zh-CN/01-Infomation-Gathering/arping?id=arping) |
|         | [fping](/zh-CN/01-Infomation-Gathering/fping?id=fping) |
|         | [hping3](/zh-CN/01-Infomation-Gathering/hping3?id=hping3) |
|         | [masscan](/zh-CN/01-Infomation-Gathering/masscan?id=masscan) |
|         | [thcping6](/zh-CN/01-Infomation-Gathering/thcping6?id=thcping6) |

## 路由分析
| 分类        | 工具   | 
| --------   | :-----  |
| 路由分析 | [netdiscover](/zh-CN/01-Infomation-Gathering/netdiscover?id=netdiscover) |
|         | [netmask](/zh-CN/01-Infomation-Gathering/netmask?id=netmask) | 

## 情报分析
| 分类        | 工具   | 
| --------   | :-----  |
| 情报分析 | maltego |
|         | spiderfoot |
|         | spiderfoot-cli |
|         | theharvester |

## 网络扫描
| 分类        | 工具   | 
| --------   | :-----  |
| 网络扫描 | masscan |
|         | nmap |

## DNS分析
| 分类        | 工具   | 
| --------   | :-----  |
| DNS分析 | dnsenum |
|         | dnsrecon |
|         | fierce |

## IDS/IPS识别
| 分类        | 工具   | 
| --------   | :-----  |
| IDS/IPS识别 | lbd |
|         | wafw00f |

## SMB分析
| 分类        | 工具   | 
| --------   | :-----  |
| SMB分析 | enum4linux |
|         | nbtscan |
|         | smbmap |

## STMP分析
| 分类        | 工具   | 
| --------   | :-----  |
| STMP分析 | swaks |

## SNMP分析
| 分类        | 工具   | 
| --------   | :-----  |
| SNMP分析 | onesixtyone |
|         | snmp-check |

## SSL分析
| 分类        | 工具   | 
| --------   | :-----  |
| SSL分析 | ssldump |
|         | sslh |
|         | sslscan |
|         | sslyze |

## 其他
| 分类        | 工具   | 
| --------   | :-----  |
| 其他 | dmitry |
|         | ike-scan |
|         | legion |
|         | maltego |

# 02-漏洞分析
## Fuzzing工具集
| 分类        | 工具   | 
| --------   | :-----  |
| Fuzzing工具集 | spike-generic_chunked |
|         | spike-generic_tcp |
|         | spike-generic_listen_tcp |
|         | spike-generic_send_tcp |
|         | spike-generic_send_udp |

## VoIP工具集
| 分类        | 工具   | 
| --------   | :-----  |
| VoIP工具集 | voiphopper |

## 其他
| 分类        | 工具   | 
| --------   | :-----  |
| 其他 | legion |
|         | nikto |
|         | nmap |
|         | unix-privesc-check |
# 03-Web程序
## CMS识别
| 分类        | 工具   | 
| --------   | :-----  |
| CMS识别 | wpscan |

## Web漏洞扫描
| 分类        | 工具   | 
| --------   | :-----  |
| Web漏洞扫描 | cadaver |
|         | davtest |
|         | nikto |
|         | skipfish |
|         | wapiti |
|         | whatweb |
|         | wpscan |

## Web爬行
| 分类        | 工具   | 
| --------   | :-----  |
| Web爬行 | cutycapt |
|         | dirb |
|         | dirbuster |
|         | wfuzz |

## Web应用代理
| 分类        | 工具   | 
| --------   | :-----  |
| Web应用代理 | burpsuite |

## 其他
| 分类        | 工具   | 
| --------   | :-----  |
| 其他 | commix |
|         | skipfish |
|         | sqlmap |
|         | wpscan |
|         | ZAP |

# 04-数据库评估软件
| 分类        | 工具   | 
| --------   | :-----  |
| ALL | SQLite database browser |
|         | skipfish |
|         | sqlmap |

# 05-密码攻击
## 哈希工具集
| 分类        | 工具   | 
| --------   | :-----  |
| 哈希工具集 | mimikatz |
|         | pth-curl |
|         | pth-net |
|         | pth-rpcclient |
|         | pth-smbclient |
|         | pth-smbget |
|         | pth-sqsh |
|         | pth-winexe |
|         | pth-wmic |
|         | pth-wmis |
|         | pth-xfreedp |
|         | smbmap |

## 离线密码攻击
| 分类        | 工具   | 
| --------   | :-----  |
| 离线密码攻击 | chntpw |
|         | hashcat |
|         | hashid |
|         | hash-identifier |
|         | ophcrack-cli |
|         | samdump2 |

## 在线攻击
| 分类        | 工具   | 
| --------   | :-----  |
| 在线攻击 | hydra |
|         | hydra-gtk |
|         | onesixtyone |
|         | patator |
|         | thc-pptp-bruter |

## Password Profilling & Wordlists
| 分类        | 工具   | 
| --------   | :-----  |
| Password Profilling & Wordlists | cewl |
|         | crunch |
|         | rsmangler |
|         | wordlists |

## 其他
| 分类        | 工具   | 
| --------   | :-----  |
| 其他 | cewl |
|         | crunch |
|         | hashcat |
|         | john |
|         | medusa |
|         | ncrack |
|         | ophcrack |
|         | wordlists |

# 06-无线攻击
## 蓝牙工具集
| 分类        | 工具   | 
| --------   | :-----  |
| 蓝牙工具集 | spooftooph |

## 无线工具集
| 分类        | 工具   | 
| --------   | :-----  |
| 无线工具集 | bully |
|         | fern wifi cracker |

## 其他
| 分类        | 工具   | 
| --------   | :-----  |
| 其他 | airrack-ng |
|         | fern wifi cracker |
|         | kismet |
|         | pixiewps |
|         | reaver |
|         | wifiite |

# 07-逆向工程
| 分类        | 工具   | 
| --------   | :-----  |
| 逆向工程 | clang |
|         | clang++ |
|         | MASM shell |
|         | radare2 |

# 08-漏洞利用工具集
| 分类        | 工具   | 
| --------   | :-----  |
| 漏洞利用工具集 | metasploit freamwork |
|         | msf payload creator |
|         | searchsploit |
|         | social engineering toolkit |
|         | sqlmap |

# 09-嗅探/欺骗
## 网络欺骗
| 分类        | 工具   | 
| --------   | :-----  |
| 网络欺骗 | dnschef |
|         | rebind |
|         | sslplit |
|         | tcpreplay |

## 网络嗅探
| 分类        | 工具   | 
| --------   | :-----  |
| 网络嗅探 | dnschef |
|         | netsniff-ng |

## 其他
| 分类        | 工具   | 
| --------   | :-----  |
| 其他 | ettercap-graphical |
|         | macchanger |
|         | mitmproxy |
|         | netsniff-ng |
|         | responder |
|         | wireshark |

# 10-权限维持
## 系统后门
| 分类        | 工具   | 
| --------   | :-----  |
| 系统后门 | dbd |
|         | powersploit |
|         | sbd |

## Tunnel工具集
| 分类        | 工具   | 
| --------   | :-----  |
| Tunnel工具集 | dbd |
|         | dns2tcpc |
|         | dns2tcpd |
|         | exe2hex |
|         | iodine |
|         | miredo |
|         | proxychains4 |
|         | proxytunnel |
|         | pwnat |
|         | sslh |
|         | stunnel4 |
|         | udptunnel |

## Web后门
| 分类        | 工具   | 
| --------   | :-----  |
| Web后门 | laudanum |
|         | weevely |

# 其他
| 分类        | 工具   | 
| --------   | :-----  |
| 其他 | exe2hex |
|         | mimikatz |
|         | powersploit |
|         | proxychains4 |
|         | weevely |

# 11-数字取证
## 取证分割工具集
| 分类        | 工具   | 
| --------   | :-----  |
| 取证分割工具集 | magicrescue |
|         | scalpel |
|         | scrounge-ntfs |

## 取证镜像工具集
| 分类        | 工具   | 
| --------   | :-----  |
| 取证镜像工具集 | guymager |


# 12-报告工具集
# 13-Social Engineering Tools
# 43-Kali & OffSec Links