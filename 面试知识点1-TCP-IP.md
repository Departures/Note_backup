---
title: 面试知识点1 -- TCP/IP
date: 2017-09-18 09:10:06
tags: 面试
---
# 面试知识点1 -- TCP/IP
啊啊啊啊啊不能忘了不能忘了

1. 电路交换与分组交换的区别？ 优劣对比。
电路交换
```txt
电路交换：是以电路连接为目的的交换方式，通信之前要在通信双方之间建立一条被双方独占的物理通道
优点：
	（1）由于通信线路为通信双方用户专用，数据直达，所以传输数据的时延非常小。
	（2）通信双方之间的屋里通路一旦建立，双方可以随时通信，实时性强。
	（3）双方通信时按发送顺序传送数据，不存在失序问题。
	（4）电路交换既适用于传输模拟信号，也适用于传输数字信号。
	（5）电路交换的交换设备及控制均比较简单。
	缺点：
	（1）电路交换平均连接建立时间对计算机通信来说较长。
	（2）电路交换家里连接后，物理通路被通信双方独占，即使通信线路空闲，也不能供其他用户使用，因而信道利用率低。
	（3）电路交换时，数据直达，不同类型，不同规格，不同速率的终端很难相互进行通信，也难以在通信过程中进行差错控制。
```
分组交换
```txt
分组交换是以分组为单位进行传输和交换的，它是一种存储——转发交换方式，
即将到达交换机的分组先送到存储器暂时存储和处理，等到相应的输出电路有空闲时再送出。

	优点：
	（1）分组交换不需要为通信双反预先建立一条专用的通信线路，不存在连接建立时延，用户可随时发送分组。
	（2）由于采用存储转发方式，加之交换节点具有路径选择，当某条传输线路故障时可选择其他传输线路，提高了传输的可靠性。
	（3）通信双反不是固定的占用一条通信线路，而是在不同的时间一段一段地部分占有这条物理通路，因而大大提高了通信线路的利用率。
	（4）加速了数据在网络中的传输。因而分组是逐个传输，可以使后一个分组的存储操作与前一个分组的转发操作并行，这种流水线式传输方式减少了传输时间。
	（5）分组长度固定，相应的缓冲区的大小也固定，所以简化了交换节点中存储器的管理。
	（6）分组较短，出错几率减少，每次重发的数据量也减少，不仅提高了可靠性，也减少了时延。
	缺点：
	（1）由于数据进入交换节点后要经历存储转发这一过程，从而引起的转发时延（包括接受分组、检验正确性、排队、发送时间等），而且网络的通信量越大，造成的时延就越大，实时性较差。
	（2）分组交换只适用于数字信号。
	（3）分组交换可能出现失序，丢失或重复分组，分组到达目的节点时，对分组按编号进行排序等工作，增加了麻烦。


	综上，若传输的数据量很大，而且传送时间远大于呼叫时间，则采用电路交换较为合适；当端到端的通路有很多段链路组成是，采用分组交换较为合适。从提高整个网络的信道利用率上看，分组交换优于电路交换。

```

2. OSI有哪几层，会画出来，知道主要几层的各自作用。
```txt
物理层：提供一个传输原始比特流的物理连接，实现透明的传送比特流。(RJ45、CLOCK、IEEE802.3)
数据链路层：建立相邻节点间的数据链路，在有差别的物理介质上实现无差错的传输(PPP、FR、HDLC、VLAN、MAC)
网络层：提供逻辑编址，数据寻址和路由。(NAT、IP、IPX、OSPF、RIP、IGRP、ICMP、ARP、RARP)
传输层：提供端到端的透明传输。(TCP、UDP、SPX、SSL)
会话层：提供数据同步过程中的会话管理。(NFS、SQL、NETBIOS、RPC)
表示层：数据格式转换。(JPEG、MPEG、ASII)
应用层：为用户的应用程序提供网络接口。(HTTP，HTTPS，FTP，TELNET，SSH，SMTP，POP3)
```

3. TCP/IP有哪几层，会画出来，知道所有层数的作用，会列举各层主要的协议名称。
![](http://img.blog.csdn.net/20140415215419250)
```txt
数据链路层：建立相邻节点间的数据链路，在有差别的物理介质上实现无差错的传输(PPP、FR、HDLC、VLAN、MAC)
网络层：提供逻辑编址，数据寻址和路由。(NAT、IP、IPX、OSPF、RIP、IGRP、ICMP、ARP、RARP)
传输层：提供端到端的透明传输。(TCP、UDP、SPX)
应用层：为用户的应用程序提供网络接口。(HTTP，HTTPS，FTP，TELNET，SSH，SMTP，POP3)

OSI和TCP/IP区别
相同点：1、都有应用层、传输层、网络层。
2、都是下层服务上层。

不同点：1、层数不同。
2、模型与协议出现的次序不同，TCP/IP先有协议，后有模型（出
现早），ISO/OSI先有模型，后有协议（出现晚）。
```
4. 硬件(MAC)地址的概念及作用。
```txt
MAC地址也叫物理地址、硬件地址或链路地址，由网络设备制造商生产时写在硬件内部。
MAC地址的长度为48位（6个字节），通常表示为12个16进制数，每2个16进制数之间用冒号隔开，
如：08:00:20:0A:8C:6D就是一个MAC地址，其中前6位16进制数08:00:20代表网络硬件制造商的编号，
它由IEEE（电气与电子工程师协会）分配，而后3位16进制数0A:8C:6D代表该制造商所制造的某个网络产品（如网卡）
的系列号。只要你不去更改自己的MAC地址，那么你的MAC地址在世界是惟一的。

在数据链路层中，交换机通过识别MAC地址进行数据包的传输
```

5. ARP协议的用途 及算法、在哪一层上会使用arp ？
```txt
ARP协议的用途：解决同一个局域网内主机或路由器的IP地址和MAC地址的映射问题。
算法：在主机的ARP高速缓存中应存放一个从IP地址到MAC地址的映射表，并且这个映射表还经常动态更新（新增或超时删除）。
在网络层会使用ARP。
```

6. 知道各个层使用的是哪个数据交换设备。（交换机、路由器、网关）
```txt
物理层用到的设备是 集线器和中继器
数据链路层用到的设备是 交换机和网桥
网络层用到的设备是 路由器
应用层用到的设备是 网关

网桥工作在数据链路层，将两个LAN连起来，根据MAC地址来转发帧，
路由器router处理网络层的数据，因此它们更容易互连不同的数据链路层，如令牌环网段和以太网段。
网关(Gateway)又称网间连接器、协议转换器。网关在网络层以上实现网络互连，是最复杂的网络互连设备，仅用于两个高层协议不同的网络互连。
```
7. 路由表的内容。
```txt
对每组网络界面（interface），路由表至少会存有下面的资讯：
    网络ID（Network ID, Network number）：就是目标地址的网络ID。
    子网掩码（subnet mask）：用来判断IP所属网络
    下一跳地址/接口（Next hop / interface）：就是数据在发送到目标地址的旅途中下一站的地址。其中interface指向next hop（即为下一个route）。一个自治系统（AS, Autonomous system）中的route应该包含区域内所有的子网络，而默认网关（Network id: 0.0.0.0, Netmask: 0.0.0.0）指向自治系统的出口。
根据应用和执行的不同，路由表可能含有如下附加信息：
    花费（Cost）：就是数据发送过程中通过路径所需要的花费。
    路由的服务质量
    路由中需要过滤的出/入连接列表
```

8. 分组转发算法。
```txt
    从数据报的首部提取目的主机的IP地址D，得出目的网络地址N
    若N就是于此路由器直接相连的某个网络地址，则进行直接交付，不需要在经过其他路由器，直接把数据报交付给目的主机（这里包括把目的地址D转换为具体的MAC地址，把数据报封装成MAC帧，在发送此帧）；否则就是间接交付。
    若路由表中有目的地址为D的特定主机路由，则把数据报传送给路由表中所指明的下一跳路由器。
    若路由表中有达到网络N的路由，则把数据报传送给路由表中所指明的下一跳路由器。
    若路由表中有一个默认路由，则把数据报传送给路由表中所指明的默认路由器
    报告转发分组出错。
```
9. IP报文的格式，格式的各个字段的含义要理解。
![](http://my.csdn.net/uploads/201204/10/1334070198_2001.png)
```txt
1.目前的协议版本号是4 ，因此I P 有时也称作I P v 4。
2.首部长度指的是首部占32 bit字的数目，包括任何选项。由于它是一个4比特字段，因此首部最长为6 0个字节
3.服务类型（TO S）字段包括一个3 bit的优先权子字段（现在已被忽略），4 bit的TO S子字段和1 bit未用位但必须置0。4 bit的TO S分别代表：最小时延、最大吞吐量、最高可靠性和最小费用。4 bit中只能置其中1 bit。如果所有4 bit均为0，那么就意味着是一般服务。
4.总长度字段是指整个I P数据报的长度，以字节为单位。利用首部长度字段和总长度字段，就可以知道I P数据报中数据内容的起始位置和度。由于该字段长1 6比特，所以I P数据报最长可达6 5 5 3 5字节
5.T T L（t i m e - t o - l i v e ）生存时间字段设置了数据报可以经过的最多路由器数。它指定了数据报的生存时间。 T T L的初始值由源主机设置（通常为 3 2或6 4 ），一旦经过一个处理它的路由器，它的值就减去 1。当该字段的值为0时，数据报就被丢弃，并发送 I C M P报文通知源主机。
6.标识字段唯一地标识主机发送的每一份数据报。通常每发送一份报文它的值就会加1
7.最后一个字段是任选项，是数据报中的一个可变长的可选信息。目前，这些任选项定义
```

10. MTU的概念，啥叫路径MTU？ MTU发现机制，TraceRoute。
[维基百科](https://zh.wikipedia.org/wiki/%E6%9C%80%E5%A4%A7%E4%BC%A0%E8%BE%93%E5%8D%95%E5%85%83)
```txt
最大传输单元:是指一种通信协议的某一层上面所能通过的最大数据包大小（以字节为单位）。
最大传输单元这个参数通常与通信接口有关（网络接口卡、串口等）。

```
11. RIP协议的概念及算法。
定义：
```txt
路由信息协议:是一种内部网关协议（IGP），为最早出现的距离向量路由协定。
属于网络层，可以通过不断的交换信息让路由器动态的适应网络连接的变化，
这些信息包括每个路由器可以到达哪些网络，这些网络有多远等。
```
算法：
```txt
 对每一个相邻路由器发送过来的RIP报文，进行以下步骤：
    （1）对地址为X的相邻路由器发来的RIP报文，先修改此报文中的所有项目：把“下一跳”字段中的地址都改为X，并把所有的"距离"字段的值加1.每个项目都有三个关键数据，即：目的网络N，距离是d，下一跳路由器是X。
    （2）对修改后的RIP报文中的每一个项目，进行如下步骤：
        * 若原来的路由表中没有目的网络N，则把该项目添加到路由表中，
        * 若下一跳路由器地址是X，则把收到的项目替换原路由表中的项目
        * 若收到的项目中距离d小于路由表中的距离，则进行更新
    （3）若3分钟还没有收到相邻路由器的更新路由表，则把此相邻路由器记为不可到达的路由器，即把距离设置为16。
    （4）返回
```
12. ICMP协议的主要功能。
定义:
```txt
网络控制消息协定是网路协议族的核心协议之一。它用于TCP/IP网络中发送控制消息，
提供可能发生在通信环境中的各种问题反馈，通过这些信息，令管理者可以对所发生的问题作出诊断，
然后采取适当的措施解决。
```
功能
```txt
侦测远端主机是否存在
建立及维护路由资料
重导数据传送路径
数据流量控制
```

13. Ping协议的实现原理，ping 命令格式。
ICMP, ping baidu.com
14. 子网划分的概念，子网掩码。
子网掩码是一个32位地址，用于屏蔽IP地址的一部分以区别网络标识和主机标识，并说明该 IP 地址是在局域网上，还是在远程网上。
子网掩码计算
255.255.255.240---> 1111 1111 1111 1111 1111 1111 1111 0000
可推算出 2^4个地址 去掉

15. IP地址的分类，如何划分的，及会计算各类地址支持的主机数。
一个IP地址主要由两部分组成：一部分是用于地址该地址所从属的网络地址；另一部分用于指明该网络上某个特定主机的主机地址

IP协议的作用主要有两个，一个是为每一台计算机分配IP地址，另一个是确定哪些地址在同一个子网络

1. IP地址由网络地址和主机地址组成，根据网络地址不同被分为A、B、C、D、E共5类。
2. A类网络地址为1~126，B类网络地址为128~191，C类网络地址为192~223，
3.主机地址均为1~254，因为网络地址及广播地址除外。
4.私有地址：10.0.0.0–10.255.255.254（A）、172.16.0.0–172.31.255.254（B）、192.168.0.0--192.168.255.254（C）

16. DNS的概念，用途，DNS查询的实现算法。

17. TCP与UDP的概念，相互的区别及优劣。
```txt
1、TCP（Transmission Control Protocol）的概念
     TCP是一种面向连接的，提供可靠交付服务和全双工通信的，基于字节流的端到端的传输层通信协议。

    TCP在传输数据之前必须先建立连接，数据传输结束后要释放连接。
    每一条TCP连接只能有2个端点，故TCP不提供广播或多播服务。
    TCP提供可靠交付，通过TCP连接传输的数据，无差错、不丢失、不重复、并且按序到达。
    TCP是面向字节流的。虽然应用进程和TCP的交互是一次一个数据块(大小不等），但TCP把英语程序交下来的数据看成仅仅是一连串的无结构的字节流。TCP并不知道所传输的字节流的含义。

2、UDP（User Datagram Protocol）的概念
     UDP是一种无连接的，尽最大努力交付的，基于报文的端到端的传输层通信协议。

    UDP，在发送数据之前不需要建立连接
    UDP不保证可靠交付，主机不需要位置复杂的连接状态
    UDP是面向报文的。UDP对应用层交下来的报文，既不合并，也不拆分，而是保留这些报文的的边界，即应用层交给UDP多长的报文，UDP就照样发送，即一次发送一个报文。在接收端，UDP一次交付一个完整的报文。
    UDP没有拥塞控制，网络出现的拥塞不会使源主机的发送速率降低。
    UDP支持一对一、一对多、多对一和多对多的交互通信。
    UDP的首部开销小，只有8个字节，比TCP的20个字节的首部要短

    TCP协议面向连接，UDP协议面向非连接
    TCP协议传输速度慢，UDP协议传输速度快
    TCP协议保证数据顺序，UDP协议不保证
    TCP协议保证数据正确性，UDP协议可能丢包
    TCP协议对系统资源要求多，UDP协议要求少
```



18. 三次握手，四次断开过程。
![](http://hi.csdn.net/attachment/201108/7/0_131271823564Rx.gif)

19. TIME_WAIT状态的概念及意义。
主动关闭的一方在发送最后一个ack 后就会进入TIME_WAIT 状态 停留2MSL（max segment lifetime）时间
* 防止上一次连接中的包，迷路后重新出现，影响新连接（经过2MSL，上一次连接中所有的重复包都会消失）
* 可靠的关闭TCP连接
    在主动关闭方发送的最后一个ack(fin) ，有可能丢失，这时被动方会重新发
    fin, 如果这时主动方处于CLOSED 状态 ，就会响应rst 而不是ack。所以
    主动方要处于TIME_WAIT 状态，而不能是CLOSED 。
    TIME_WAIT 并不会占用很大资源的，除非受到攻击。
    还有，如果一方send 或recv 超时，就会直接进入CLOSED 状态

20. TFTP 与 FTP的区别。
```txt
FTP协议在TCP/IP协议族中属于应用层协议，用于在远端服务器和本地客户端之间传输文件，使用TCP端口20和21进行传输。端口20用于传输数据，端口21用于传输控制消息。
TFTP简单文件传输协议也是用于在远端服务器和本地主机之间传输文件的，相对于FTP，TFTP没有复杂的交互存取接口和认证控制，适用于客户端和服务器之间不需要复杂交互的环境。TFTP协议的运行基于UDP协议，使用UDP端口69进行数据传输。


基于的传输协议不一样：FTP是基于TCP TFTP是基于UDP
端口号不一样：FTP是用21.20 TFTP是69
速度和安全方面：FTP在速度方面没有TFTP快但是FTP安全好
```


# 总结
面试主要会问一些很基础的如TCP三次握手，osi模型及一些什么设备在哪一层等等之类的。
反正我会经常忘记
需要经常复习
