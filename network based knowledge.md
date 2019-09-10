[TOC]

# 网络基础

## 网络基本概念

![1567565008918](https://github.com/CS4Fly/NetWork/blob/master/images/1567565008918.png)

![1567817913064](https://github.com/CS4Fly/NetWork/blob/master/images/1567817913064.png)

机柜1U=4.45cm	42U标准机柜

### 网络类型

- 总线型
- 树型
- 星型
- 环型
- 部分网状型

### 网络传输模式

- 单工：只能有一个方向的通信而没有反方向的交互
- 半双工：通信的双方都可以发送信息，但不能双方同时发送
- 双工：通信的双方可以同时发送和接收信息

### 网络通信类型

- 单播

- 组播

- 广播

  ![1567567839351](https://github.com/CS4Fly/NetWork/blob/master/images/1567567839351.png)

### CSMA/CD协议

![1567566049366](https://github.com/CS4Fly/NetWork/blob/master/images/1567566049366.png)

![1567566988129](https://github.com/CS4Fly/NetWork/blob/master/images/1567566988129.png)

## OSI七层模型

![1567569235572](https://github.com/CS4Fly/NetWork/blob/master/images/1567569235572.png)

### 网络分层体系结构

![1567579116318](https://github.com/CS4Fly/NetWork/blob/master/images/1567579116318.png)

![1567579349718](https://github.com/CS4Fly/NetWork/blob/master/images/1567579349718.png)

### 封装与解封装

![1567580566579](https://github.com/CS4Fly/NetWork/blob/master/images/1567580566579.png)

![1567580633153](https://github.com/CS4Fly/NetWork/blob/master/images/1567580633153.png)

![1567580673137](https://github.com/CS4Fly/NetWork/blob/master/images/1567580673137.png)

![1567580720519](https://github.com/CS4Fly/NetWork/blob/master/images/1567580720519.png)

![1567580753844](https://github.com/CS4Fly/NetWork/blob/master/images/1567580753844.png)

# TCP/IP协议

![1567582210934](https://github.com/CS4Fly/NetWork/blob/master/images/1567582210934.png)

![1567582231741](https://github.com/CS4Fly/NetWork/blob/master/images/1567582231741.png)

![1567582268707](https://github.com/CS4Fly/NetWork/blob/master/images/1567582268707.png)

![1567582552007](https://github.com/CS4Fly/NetWork/blob/master/images/1567582552007.png)

### IP数据报

![1567582913854](https://github.com/CS4Fly/NetWork/blob/master/images/1567582913854.png)

版本	占4 bit，指IP协议的版本，目前的IP协议版本号为4（即IPv4）

首部长度	占4 bit，可表示的最大数值是15个单位（一个单位为4字节），因此IP的首部长度的最大值是60字节。

总长度	占16 bit，指首部和数据之和的长度，单位为字节，因此数据的最大长度为65535字节。总长度必须不超过最大传送单元MTU。

标识（identification）	占16 bit，它是一个计数器，用来产生数据报的标识。

标志（flag）占3 bit，目前只有两个比特有意义。（**分组，在网络层**）
标志字段的最低位是MF（More Fragment）MF=1表示后面"还有分片".MF=0表示最后一个分片。
标志字段中间的一位是DF（Don't Fragment），只有当DF=0时才允许分片。

片偏移（13 bit）指出：较长的分组在分片后某片在原分组中的相对位置。片偏移以**8个字节为偏移单位**。➗8
**MSS 最大报文段长度 1420（剔除固定报文20Bytes为1400字节）**

生存时间：每经过**一个网段**减1跳；（路由汇总时出现）

协议（8 bit）字段	指出此数据报携带的数据使用何种协议，以便目的主机的IP层将数据部分上交给哪个处理过程（**用编号值表示**）

首部检验和（16 bit）字段	只检验数据报的首部不包括数据部分。这里不采用CRC检验码而采用简单的计算方法。

源地址和目的地址都各占4字节



### IP地址

![1567583463066](https://github.com/CS4Fly/NetWork/blob/master/images/1567583463066.png)

![1567585092724](https://github.com/CS4Fly/NetWork/blob/master/images/1567585092724.png)

![1567585325604](https://github.com/CS4Fly/NetWork/blob/master/images/1567585325604.png)

![1567585340953](https://github.com/CS4Fly/NetWork/blob/master/images/1567585340953.png)

![1567585353922](https://github.com/CS4Fly/NetWork/blob/master/images/1567585353922.png)

### 子网划分

#### 等分子网划分

![1567586685784](https://github.com/CS4Fly/NetWork/blob/master/images/1567586685784.png)

#### 可变长子网掩码 VLSM



### IPv6

**长度 128位   由48位的全局前缀、16位的子网ID和64位的接口标识符组成**

分类：单播、组播、**任播** 一对最近



### ARP协议

#### RARP协议

#### 代理ARP协议

代理ARP是ARP协议的一个变种。对于没有配置缺省网关的计算机要和其他网络中的计算机实现通信，网关收到源计算机的ARP请求会使用自己的MAC地址与目标计算机的IP地址对源计算机进行应答。

#### 无故ARP协议

主机有时会使用自己的IP地址作为目标地址发送ARP请求。

作用：

- 检查重复地址（如果收到ARP响应表明存在重复地址）。
- 用于通告一个新的数据链路标识。当一个设备收到一个arp请求时，发现arp缓冲区中已有发送者的IP地址，则更新此IP地址的MAC地址条目。

### ICMP协议
ICMP（Internet Control Message Protocol）被认为是网络层的一个组成部分。它传递差错、控制、查询报文等信息

ICMP报文常被IP层或更高层协议（TCP或UDP）使用，如Ping
IP协议并不是一个可靠的协议，它不保证数据被送达，那么，保证数据送达的工作应该由其他的模块来完成。

ICMP定义了很多信息类型，例如：
- 目的地不可达
- TTL超时
- 信息请求
- 信息应答
- 地址请求
- 地址应答

![1567653762094](C:\Users\LD\AppData\Roaming\Typora\typora-user-images\1567653762094.png)

![1567652822718](https://github.com/CS4Fly/NetWork/blob/master/images/1567652822718.png)

### tracert 路由追踪

- Tracert用于查看IP数据报从一台主机传到另一台主机所经过的路由。
- Trace route程序使用ICMP报文和IP首部中的TTL字段（生存周期）
- 由于ICMP报文是通过IP数据包传送的，因此Tracert命令可以从中取出IP源地址。

### telnet应用

- 明文传输
- TCP 23
- telnet探测服务器或应用端口是否开启



### 小结

- ICMP定义了网络层控制和传递消息的功能；
- ping使用ICMP回送请求与应答检测网络连通性；4
- tracert使用TTL超时机制检测网络连通性。

### 问题：端到端传输与点到点输出的区别

点到点是物理拓扑；点到点是网络层的；

端到端是网络连接；网络要通信必须要建立连接，一旦连接建立起来，就说明已经是端到端连接了。

即端到端是逻辑链路，端到端是传输层的。

端到端是由无数的点到点实现和组成的。



### TCP报头

![1567672670837](https://github.com/CS4Fly/NetWork/blob/master/images/1567672670837.png)

**确认比特ACK**     只有当 ACK = 1时确认号字段才有效。当ACK=0时，确认号无效。**确认号ack=序号+1**

复位比特RST（ReSeT） 当RST=1时，表明TCP连接中出现严重差错（如由于主机崩溃或其他原因），必须释放连接，然后再重新建立运输连接。

同步比特SYN	同步比特SYN置为1，就表示这是一个连接请求或连接接受报文。

终止比特FIN（FINal） 	用来释放一个连接。当FIN=1时，表明此报文段的发送端的姿据已发送完毕，并要求释放运输连接。

窗口字段	占2字节。窗口字段用来控制对方发送的数据量，单位为字节.TCP连接的一端根据设置的缓存空间大小确定自己的接收窗口大小，然后通知对方以确定对方的发送窗口的上限。

检验和	占2字节。检验和字段检验的范围包括首部和数据这两部分。在计算检验和时，要在TCP报文段的前面加上12字节的伪首部。

紧急指针字段	占16 bit，紧急指针指出在本报文段中的紧急数据的最后一个字节的序号.

选项字段	长度可变。TCP只规定了一种选项，即最大报文段长度MSS（Maximum Segment Size），MSS告诉对方TCP："我的缓存所能接收的报文段的数据字段的最大长度是MSS个字节。"

填充字段	这是为了使整个首部长度是4字节的整数倍。



### C/S模式

TCP的连接和建立都是采用客户服务器方式。
主动发起连接建立的应用进程叫做客户（client）。
被动等待连接建立的应用进程叫做服务器（server）。



### TCP建立连接	三次握手

![1567672921205](https://github.com/CS4Fly/NetWork/blob/master/images/1567672921205.png)

### TCP释放连接	四次挥手

![1567673395797](https://github.com/CS4Fly/NetWork/blob/master/images/1567673395797.png)

### TCP可靠传输机制

#### 传输确认

![1567673621800](https://github.com/CS4Fly/NetWork/blob/master/images/1567673621800.png)

#### TCP确认号和序列号

![1567673646823](https://github.com/CS4Fly/NetWork/blob/master/images/1567673646823.png)

#### 超时重传

![1567673692567](https://github.com/CS4Fly/NetWork/blob/master/images/1567673692567.png)

#### 固定窗口

![1567673723363](https://github.com/CS4Fly/NetWork/blob/master/images/1567673723363.png)

#### 滑动窗口

![1567673743079](https://github.com/CS4Fly/NetWork/blob/master/images/1567673743079.png)

#### 流量控制

![1567673802260](https://github.com/CS4Fly/NetWork/blob/master/images/1567673802260.png)

### UDP报头

![1567674080505](https://github.com/CS4Fly/NetWork/blob/master/images/1567674080505.png)

### 应用层协议

#### DNS服务

- tcp 53 udp 53

  ![1567674062883](https://github.com/CS4Fly/NetWork/blob/master/images/1567674062883.png)

![img](https://github.com/CS4Fly/NetWork/blob/master/images/$B@M}ED_Z31_IREKEX]5[EO.jpg)

#### 资源记录和区域文件

区域中包含组成相关DNS域资源信息的资源记录

资源记录类型

A资源记录：用来指定主机名（或域名）对应的IP地址记录。
CNAME资源记录：别名记录。这种记录允许您将多个名字映射到另外一个域名.
MX资源记录：邮件交换记录
NS资源记录：域名服务器记录，用来指定域名由哪台服务器来进行解析
SOA资源记录
PTR资源记录

#### DNS查询方式

- 递归查询
- 迭代查询
- 反向查询

#### DNS域名解析完整过程

![1567675579032](https://github.com/CS4Fly/NetWork/blob/master/images/1567675579032.png)

访问web.microsoft.com

1. 先检查本机是不是该资源
2. 检查hosts文件
3. 查缓存
4. 以上三步全否定，则请求设置指向的DNS服务器
5. DNS服务器检查自己是不是资源所在，检查配置文件，检查缓存
6. 第5步失败请求根服务器，根服务器告诉DNS服务器com域名服务器的所在
7. DNS服务器请求com域名服务器，com域名服务器告诉microsoft域名服务器的所在
8. DNS服务器请求microsoft域名服务器，microsoft域名服务器告诉-资源所在主机地址
9. DNS服务器返回该地址给客户机，客户机直接去访问该资源服务器。



#### DHCP协议 

- DHCP是Dynamic Host Configuration Protocol（动态主机配置协议）的缩写；
- DHCP是从**BOOTP**（Baotstrap Protocol，自举协议）发展而来；
- DHCP采用**客户端/服务器**模式，服务器负责集中管理，客户端向服务器提出配置申请，服务器根据策略返回相应配置信息；
- DHCP报文采用**UDP封装**，服务器端的端口号是**67**，客户端的端口号是**68**

##### 地址分配方式

- 手动分配
- 自动分配
- 动态分配

##### 租约过程--四线会话

![1567674933298](https://github.com/CS4Fly/NetWork/blob/master/images/1567674933298.png)

1. **DHCP Discover（广播）**

   这个过程主机封装报文，**源ip为0.0.0.0，目标ip为255.255.255.255；数据包没有完成封装是无法发送的！**

2. **DHCP Offer（单播）**

3. **DHCP Request（广播）**

   服务器还未确认IP给他，所以还是广播

4. **DHCP ACK（单播）**

   

   **租约过50%，单播dhcp request消息包向服务器请求续约；**

   **租约过87.5%，广播服务器请求IP；**

   ![1567675042721](https://github.com/CS4Fly/NetWork/blob/master/images/1567675042721.png)

### 主机间通信过程

#### 以太网MAC地址（第8个比特位）

![1567676219453](https://github.com/CS4Fly/NetWork/blob/master/images/1567676219453.png)

#### 二层主机通信过程

#### 三层主机通信过程（IP地址不会发生改变，源和目的MAC会一直改变）

**冲突域：**总线型拓扑结构，**交换机隔离冲突域，不隔离广播域；hub是不隔离冲突域的，因为是总线型；路由器是两者都隔离。

**广播域：**



# 路由基础

ctrl + shift + 6  停止域名解析，防止输入时发生错误

或者config模式下 **no ip domain-lookup**



### 路由器

#### 路由器关键功能

- 检查数据包的目的地

- 发现可能的路由信息

- 选择最佳路径

- 验证和维护路由信息

- 路由器隔离广播包，可以防止网络广播风暴

  

#### 连接到路由器的设备特征

- 路由器上所有直连设备**在不同冲突域之中**
- 路由器上所有直连设备**在不同广播域之中**
- 路由器各接口上所有直连设备**独享**接口带宽



#### 路由项的分类

- 主机路由：掩码长度是32位的路由，表明此路由匹配单-IP地址。
- 子网路由：掩码长度小于32但大于0，表明此路由匹配一个子网。
- 默认路由：掩码长度为0，表明此路由匹配全部IP地址，



#### **路由匹配原则**

先匹配优先级（管理距离），如果都是使用同一协议，再匹配掩码长度，掩码长度最长的被匹配；

在路由表中，静态路由中有一个特殊的路由：**默认路由**；**默认路由是最后被匹配的**。



#### 路由的来源

- 直连路由
  开销小，配置简单，无需人工维护。只能发现本接口所属网段的路由。
- 手工配置的静态路由
  无开销，配置简单，需人工维护，适合简单扑结构的网络。
- 路由协议发现的路由
  开销大，配置复杂，无需人工维护，适合复杂拓扑结构的网络。



#### 度量值

度量值代表距离。它们用来在寻找路由时确定最优路由路径。每一种路由算法在产生路由表时，会为每一条通过网络的路径产生一个数值（度量值），最小的值表示最优路径。度量值的计算可以只考虑路径的一个特性，但更复杂的度量值是综合了路径的多个特性产生的。

通常影响路由度量值的因素：线路延迟、带宽、线路使用率、线路可信度、跳数、最大传输单元

不同路由协议参考的因素不同



#### 浮动路由

对一个网段在路由表当中存在**优先级不一的路由** 叫做 浮动路由（主从备份的感觉）



#### 无类ip

就是vlsm可变长掩码不属于abc类ip地址，只要是掩码不是默认的。



### 冗余架构

- 双活
  - 主主
  - 互为主备：不同业务的主备

![1567836883902](https://github.com/CS4Fly/NetWork/blob/master/images/1567836883902.png)

- 主备

  主线路出问题时备线路才跑数据

通过设置度量值来设置主备



### 路由表规则

show ip route路由表永远显示优先级最高的



### 路由协议与可路由协议

ospf 算法**需要进程**，**应用层**，又工作在**网络层**



- 内部网关协议 IGP
- 外部网关协议 EGP

![1567847191349](https://github.com/CS4Fly/NetWork/blob/master/images/1567847191349.png)

**收敛**：网络从不稳定状态到达一个稳定状态的所用时间。称为收敛速度。



#### 解除路由环路方法

- 定义路由不可达
- 水平分割
- 路由抑制 毒性反转
- 抑制时间
- 触发更新（不等待更新周期）



### RIP协议概述

距离矢量算法

端口520

- v1无法携带掩码；广播
- V2携带掩码，支持VLSM和CIDR；组播方式，224.0.0.9；

![1567844492472](https://github.com/CS4Fly/NetWork/blob/master/images/1567844492472.png)

更新原则：

- 学习最新的
- 走最近的
- 学习新增的跳数小于16hop的

3个定时器：

- Update：发送路由更新的时间间隔，默认30秒
- Timeout：定义老化时间，如果在老化时间内没有收到某条路由的更新报文，则该条路由的度量值被设置为16，并从路由表中撤销，默认值180秒。（**仍存在于路由器的缓存中，只是不显示在路由表中**）
- Garbage-Collect：定义了一条路由从度量值16开始，直到它从路由器里被删除所经历的时间，默认值120秒。（**从路由器表中缓存彻底删除**）

**Q:为什么不用了？**
A:因为rip更新速度太慢了



### OSPF协议概述

router ospf 1 设置ospf进程

**没有更新周期，根据链路状态变化来实时更新**；

**根据链路状态选择最佳路径**

![1567845804756](https://github.com/CS4Fly/NetWork/blob/master/images/1567845804756.png)

![1567846027391](https://github.com/CS4Fly/NetWork/blob/master/images/1567846027391.png)

Router ID最好手动配置，如果由路由器自动选举，当IP地址发生改变时又需要重新收敛，导致延时，所以最好手动配置。

#### 骨干区

![1567847259028](https://github.com/CS4Fly/NetWork/blob/master/images/1567847259028.png)

![1567847677899](https://github.com/CS4Fly/NetWork/blob/master/images/1567847677899.png)

骨干路由器

![1567847628707](https://github.com/CS4Fly/NetWork/blob/master/images/1567847628707.png)

#### DR和BDR选举

DR和BDR是针对网段而言的

DR通过 224.0.0.5 组播回应

![1567847943892](https://github.com/CS4Fly/NetWork/blob/master/images/1567847943892.png)

![1567848036895](https://github.com/CS4Fly/NetWork/blob/master/images/1567848036895.png)

![1567848085077](https://github.com/CS4Fly/NetWork/blob/master/images/1567848085077.png)

![1567848530883](https://github.com/CS4Fly/NetWork/blob/master/images/1567848530883.png)

#### 优势



#### OSPF报文类型

![1567990581485](https://github.com/CS4Fly/NetWork/blob/master/images/1567990581485.png)

#### 区域内路由计算（LSA类型）

![1567990863771](https://github.com/CS4Fly/NetWork/blob/master/images/1567990863771.png)

![1567990977992](https://github.com/CS4Fly/NetWork/blob/master/images/1567990977992.png)





# 交换网络

交换机隔离冲突域，不隔离广播域

网桥=少接口的交换机

二层交换机功能：地址学习；帧的转发/过滤；环路防止；

交换机MAC地址表老化时间300秒；

交换机只学源MAC，不学习目的MAC（因为目的MAC可能是广播包）

交换机对数据帧的转发和过滤；

广播风暴：广播一旦发出，必须得接受，但可以不回应

### VLAN间路由

逻辑隔离网络，减少广播域范围，但增加了广播域数量；

VLAN（Virtual Local Area Network），中文"虚拟局域网"
最早的VLAN技术是**由Cisco公司1996年**提出。
定义：它是一种可以不考虑用户的物理位置，而只需根据功能、应用等因素将用户从逻辑上划分为功能上相对独立的工作组的网络技术。

#### 作用

- 限制广播域
- 增强局域网的安全性
- 提高了网络的健壮性
- 灵活构建工作组

每个VLAN逻辑上相当于一个独立的网桥
VLAN可以跨越多个交换机
Trunk可以承载多个VLAN的信息流
在Trunk上使用特殊的封装格式以区分不同的VLAN

VLAN1：默认VLAN，特殊的VLAN，管理VLAN

**交换机默认access口，access口一般连接的是终端，终端无法处理VLAN数据帧（VLAN标签tag）；**VLAN数据帧（tag）只在交换机内部和trunk链路中存在。

**Trunk口是可以读取VLAN数据帧，承载不同VLAN的信息流。**

#### 划分方式

- **根据接口划分：基于端口的VLAN   (最常用)**
- 根据MAC划分
- 根据IP划分：基于IP子网的VLAN
- 根据协议划分

#### IEEE802.1q 协议和封装格式

dot1q

![1567994482492](https://github.com/CS4Fly/NetWork/blob/master/images/1567994482492.png)

#### 交换机接口模式

1. Access接口

   ![1567996385984](https://github.com/CS4Fly/NetWork/blob/master/images/1567996385984.png)

2. trunk接口

   ![1567996523431](https://github.com/CS4Fly/NetWork/blob/master/images/1567996523431.png)

sw#vlan database

sw#vlan # name xxx

把接口加入vlan，就算接口物理故障，也能快速恢复网络。

没有百分百的安全，只有快速的响应。

#### 生成树协议

 https://www.jianshu.com/p/f4b7eaa6d697

##### 引入原因

- 冗余拓扑消除了由于单点故障所引致的网络不通问题
- 冗余拓扑却带来了广播风暴、重复帧和MAC地址表不稳定的问题
- 复杂的拓扑将导致多个环路的产生
- 第二层将没有机制停止环路的产生（**有没有环路看逻辑架构，不看物理架构**）

![1568018150661](https://github.com/CS4Fly/NetWork/blob/master/images/1568018150661.png)

##### 工作原理

**只有一个根桥**

![1568018250615](https://github.com/CS4Fly/NetWork/blob/master/images/1568018250615.png)

##### 算法

选举判定的依据
确定根网桥，使用网桥ID

计算到根网桥的最小根路径成本

确定最小的发送方网桥ID

确定最小的端口ID

**成本计算**（链路开销值，老的cost不再使用）    **按带宽的倒数计算**

##### 网桥ID

![1568018597365](https://github.com/CS4Fly/NetWork/blob/master/images/1568018597365.png)

**选举只看桥ID**；

**网桥优先级取值范围只能是4096的倍数**；

**其中低12bit为VLAN号占用（VID）**；

**查看时为32769，因为32768为高4位，低12位为vlan 1；**

先比较桥ID的优先级，再比较MAC；数值越小，优先级越高

##### 端口ID

![1568019408265](https://github.com/CS4Fly/NetWork/blob/master/images/1568019408265.png)

先比较端口ID的优先级，再比较端口编号；数值越小，优先级越高；

##### - 根网桥的选择

![1568019692657](https://github.com/CS4Fly/NetWork/blob/master/images/1568019692657.png)

##### - 根端口的选举

非根桥到根桥的端口（这个端口属于？？？）是根端口

##### - 选路规则

先计算开销cost；再计算根网桥id；再比较根端口id

##### - 指定端口

是指网络（指交换机到交换机的一个链路两端）或链路到达根网桥的端口（这个端口属于？？？）

**在同一个环路当中，根桥上的接口都属于指定端口**

##### 端口状态

![1568021904484](https://github.com/CS4Fly/NetWork/blob/master/images/1568021904484.png)

- 阻塞状态：只接收BPDU，不发送BPDU
- 阻塞-->侦听-->学习-->转发（大概50s）
- portfast 速端口：由disabled状态立即进入forwarding状态
- uplinkfast  上层链路速端口：由阻塞状态立即到转发状态

##### STP重新计算

拓扑变化

- 加入或移除交换机
- 链路中断或恢复

生成树通过BPDU检测到这些情况，生成树重新计算收敛。

##### STP不足

收敛时间太长

##### RSTP快速生成树协议

加快了收敛速度

##### RSTP、STP的不足

多个实例可能带来多个环路，无法解决

##### MSTP 多生成树协议

![1568022969292](https://github.com/CS4Fly/NetWork/blob/master/images/1568022969292.png)

##### 三种模式的区别

![1568023042543](https://github.com/CS4Fly/NetWork/blob/master/images/1568023042543.png)

![1568023064975](https://github.com/CS4Fly/NetWork/blob/master/images/1568023064975.png)

### 高可用性

#### VRRP

##### 选举

默认值 100

值越大的越优先

优先级相同IP地址越大的越优先

成为主

当上层链路出现问题时，主交换优先级降一个值，降到比备交换小。（端口追踪技术）

### 端口安全

802.1x

### 端口镜像

用作数据审计、数据分析；并不能对数据进行控制；

![1568087558145](https://github.com/CS4Fly/NetWork/blob/master/images/1568087558145.png)

![1568087916737](https://github.com/CS4Fly/NetWork/blob/master/images/1568087916737.png)

# 访问控制列表

访问控制列表（ACL）是应用在路由器接口的指令列表，用来告诉路由器哪些数据包可以接收转发，哪些数据包需要拒绝

ACL的工作原理：读取第三层及第四层包头中的信息，根据预先定义好的规则对包进行过滤

**核心技术：包过滤** 网络层

### 作用

提供网络访问的基本安全手段
可用于Qos 控制数据流量
控制并发连接数量

### ！ 访问控制列表的出入

默认策略:隐含拒绝

![1568099132478](https://github.com/CS4Fly/NetWork/blob/master/images/1568099132478.png)

![1568099404647](https://github.com/CS4Fly/NetWork/blob/master/images/1568099404647.png)

#### Deny和permit命令

Access-list 1 deny **172.16.4.13 0.0.0.0**  （**0.0.0.0**是**通配符**，也可以写成**host ip add**）

Access-list 1 permit 172.16.0.0 0.0.255.255

Access-list 1 permit **0.0.0.0 255.255.255.255** （也可以写成**any**）

### 分类

- **标准ACL** 1-99 1300-1999
  - 只能限制源IP
  - **尽量靠近目标主机进行限制**
- **扩展ACL** 100-199 2000-2699
  - 检查源IP、目的IP、特定TCP/IP，协议和目的端口等
  - **尽量靠近源主机进行限制**
- 命名ACL

### ！ 检查过程

![1568100232051](https://github.com/CS4Fly/NetWork/blob/master/images/1568100232051.png)

![1568100439091](https://github.com/CS4Fly/NetWork/blob/master/images/1568100439091.png)

### 访问控制列表的配置

![1568103586455](https://github.com/CS4Fly/NetWork/blob/master/images/1568103586455.png)

#### 插入ACL条目

![1568104170769](https://github.com/CS4Fly/NetWork/blob/master/images/1568104170769.png)

#### 删除ACL条目

![1568104235568](https://github.com/CS4Fly/NetWork/blob/master/images/1568104235568.png)

