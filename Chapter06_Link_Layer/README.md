# 第6章 数据链路层和局域网 (Data Link Layer and LANs)

> **章节定位**：聚焦数据链路层——负责相邻节点间的可靠传输，涵盖差错检测、多路访问控制、局域网核心技术及数据中心/链路虚拟化扩展，为网络层提供本地数据交付的基础。

---

## 📋 章节导航与重难点

### 6.1 [引论和服务](../Chapter06_Link_Layer/6.1_Introduction_and_Services.md)
- **核心**：
  - 链路层(`Data Link Layer`)定位：点到点(`point-to-point`)传输 vs 网络层端到端(`end-to-end`)路由
  - 节点(`node`)与链路(`link`)概念：主机、路由器、交换机均为节点；链路包括有线/无线/共享链路
  - 帧(`frame`)作为链路层PDU，承载网络层数据报
  - 链路层服务：成帧(`framing`)、链路接入(`link access`)、可靠传输(`reliable delivery`)、差错检测(`error detection`)、流量控制(`flow control`)
  - 适配器(`adapter`)实现链路层功能，半双工(`half-duplex`)与全双工(`full-duplex`)模式
- **难点**：
  - 链路层与网络层职责边界：链路层只负责相邻节点，网络层负责跨网络路径
  - 适配器作为软硬件交界：既处理硬件信号又执行协议逻辑，理解其双重角色

### 6.2 [差错检测和纠正](../Chapter06_Link_Layer/6.2_Error_Detection_nd_Correction.md)
- **核心**：
  - 差错检测基本框架：数据D + 冗余位EDC，接收方比对判断完整性
  - 单bit/2维奇偶校验(`Parity Check`)：偶校验/奇校验，只能检测奇数个bit翻转
  - Internet校验和(`Checksum`)：运输层/网络层常用，按字求和取反
  - CRC循环冗余校验(`Cyclic Redundancy Check`)：生成多项式、模2运算、强大检错能力
  - CRC检错性能分析：漏检概率与EDC长度权衡
- **难点**：
  - CRC数学实现：模2除法/多项式长除法的具体计算步骤，容易在运算细节上出错
  - 检错能力 vs 纠错能力：奇偶校验和校验和只能检错，海明码可纠错但开销大
  - 三种方法适用场景对比：链路层多用CRC，网络/运输层多用Checksum

### 6.3 [多路访问协议](../Chapter06_Link_Layer/6.3_Multiple_Access_Protocol.md)
- **核心**：
  - 广播链路(`Broadcast Link`)多路访问问题：多个节点共享信道导致冲突(`collision`)
  - 理想MAC协议四个条件：独占全速率、均分平均速率、完全分布式、简单
  - 信道划分协议：TDMA(`Time Division Multiple Access`)、FDMA(`Frequency Division Multiple Access`)、CDMA(`Code Division Multiple Access`)
  - 随机访问协议：时隙ALOHA(`Slotted ALOHA`)、纯ALOHA(`Pure ALOHA`)、CSMA(`Carrier Sense Multiple Access`)、CSMA/CD、CSMA/CA
  - 轮流协议：轮询(`Polling`)、令牌传递(`Token Passing`)、DOCSIS线缆接入
- **难点**：
  - ALOHA效率公式推导与理解：时隙ALOHA最大效率约37%，纯ALOHA约18%
  - CSMA/CD vs CSMA/CA区别：有线用CD（检测冲突）vs 无线用CA（避免冲突，因隐藏终端问题无法可靠检测）
  - 隐藏终端(`Hidden Terminal`)与暴露终端(`Exposed Terminal`)问题的本质

### 6.4 [LANs](../Chapter06_Link_Layer/6.4_LANs.md)
- **核心**：
  - MAC地址(`MAC Address`)：48bit平面地址，全球唯一，固化在适配器ROM中，与可配置的IP地址分离
  - ARP协议(`Address Resolution Protocol`)：即插即用，广播查询/单播回复，IP-to-MAC映射缓存
  - 以太网帧结构(`Ethernet Frame`)：前导码、MAC地址、类型字段、数据、CRC
  - CSMA/CD协议(`Carrier Sense Multiple Access with Collision Detection`)：二进制指数退避算法(`Exponential Backoff`)
  - 802.11无线局域网(`802.11 WLAN`)：CSMA/CA(`Collision Avoidance`)、RTS/CTS握手、4地址帧格式
  - 交换机(`Switch`)：自学习(`Self-Learning`)建立交换表，过滤/转发/泛洪决策
  - VLAN虚拟局域网(`Virtual LAN`)：逻辑隔离、Trunk端口、802.1Q标签帧格式
- **难点**：
  - 跨网段帧传输中MAC地址每跳重新封装（IP地址始终不变），这是理解ARP跨网段行为的关键
  - 802.11为何必须使用CSMA/CA而非CSMA/CD：无线信号衰减导致无法可靠检测冲突（隐藏终端问题）
  - 交换机泛洪(`Flooding`)与广播的区别：泛洪是未知目的MAC时的有选择性扩散，广播是目的MAC为FF-FF-FF-FF-FF-FF

### 6.5 [链路虚拟化：MPLS](./6.5_Link_Virtualization_MPLS.md)
- **核心**：
  - MPLS(`Multiprotocol Label Switching`)本质：在IP网络之上构建标签转发层，将MPLS网络虚拟成链路
  - 标签交换：入口LER(`Label Edge Router`)Push标签、中间LSR(`Label Switching Router`)Swap标签、出口LER Pop标签
  - 标签交换路径LSP(`Label Switched Path`)：基于精确标签匹配转发，查表速度远快于IP前缀匹配
  - 垫层(`Shim`)格式：20bit Label + 3bit Exp + 1bit S + 8bit TTL = 4字节，位于二层头与IP头之间
  - 显式路由ER-LSP(`Explicitly Routed LSP`)：源端指定路径，支持流量工程(`Traffic Engineering`)
  - MPLS优点：快速转发、流量工程、VPN支持、带宽资源分配、Fast Reroute快速重路由
- **难点**：
  - MPLS与IP的关系是"增强"而非"替代"：IP地址始终保留，MPLS仅在域内用标签转发
  - 标签栈嵌套（S位支持）：外层标签用于隧道转发，内层标签用于VPN区分，多层标签的叠加逻辑

### 6.6 [数据中心网络](./6.6_Data_Center_Network.md)
- **核心**：
  - 数据中心规模：数万至数十万台主机，密集耦合(`Tightly Coupled`)、距离临近
  - 三大应用场景：电子商务(`E-commerce`)、内容服务器(`Content Servers`)/CDN、搜索引擎与数据挖掘
  - 层次化架构：Internet → Border Router → Access Router → Load Balancer → Tier-1 → Tier-2 → TOR → Server Racks
  - 负载均衡器(`Load Balancer`)：应用层路由(`Application Layer Routing`)，接受外部请求、智能分发、隐藏内部结构
  - 丰富互连：ECMP(`Equal Cost Multi-Path`)多路径增加吞吐，冗余设计增加可靠性
  - 东西向流量(`East-West Traffic`) vs 南北向流量(`North-South Traffic`)：数据中心内部服务器间通信往往大于外部访问
- **难点**：
  - 东西向流量大于南北向的反直觉现象：传统网络设计为客户端-服务器模式，数据中心却是服务器-服务器协作为主
  - 同一TCP流的流一致性要求：ECMP哈希需保证同一五元组走同一路径，否则TCP包乱序触发重传
  - TOR(`Top of Rack`)上行带宽是机架级瓶颈：机架内所有服务器共享TOR的上行链路

### 6.7 [Web请求的一天](./6.7_A%20Day_in_the_Life_of_Web_Request.md)
- **核心**：
  - 完整生命周期6步：DHCP获取IP/网关/DNS → ARP解析网关MAC → DNS查询域名到IP → TCP三次握手 → HTTP请求 → HTTP响应
  - 每步协议封装层次：DHCP(DHCP→UDP→IP→Eth)、ARP(ARP→Eth直接封装)、DNS(DNS→UDP→IP→Eth)、TCP(TCP→IP→Eth)、HTTP(HTTP→TCP→IP→Eth)
  - 跨域通信：数据报跨越校园网(`School Network`) → ISP(`Comcast`) → Google网络三个自治域
  - 各层协议协同：DHCP(启动配置)、ARP(MAC解析)、DNS(域名寻址)、TCP(可靠连接)、HTTP(应用内容)、IP(跨网路由)、Eth+Phy(本地传输)
- **难点**：
  - DHCP请求前客户端无IP地址：使用0.0.0.0源IP和广播MAC(FF:FF:FF:FF:FF:FF)发送Discover
  - ARP直接封装在以太网帧中（以太网类型0x0806），不经过IP/UDP层——这是很多学生的误解点
  - TCP三次握手完成前不能传输HTTP数据：SYN不携带应用层数据，握手完成才开启HTTP会话

---

## 🔮 第6章展望

**下一章（第8章）**：
- 网络安全

---

> 🔗 **返回根目录**：[Course Notes Root](../README.md)
