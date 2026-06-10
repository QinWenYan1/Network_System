# 第1章 计算机网络和因特网 (Computer Networks and the Internet)

> **章节定位**：计算机网络课程的入门章节，从宏观视角建立 Internet 全貌——涵盖网络边缘/核心/接入网的组成结构、分组交换与电路交换原理、ISP 层级结构、性能指标（延迟/丢失/吞吐量）以及协议层次模型，为后续各层深入学习奠定全局认知框架。

---

## 📋 章节导航与重难点

### 1.1 [什么是Internet](./1.1_What_is_Internet.md)
- **核心**：
  - `Internet` 的两种视角——`组件角度(Components)`（网络边缘、核心、协议）和 `服务角度(Services)`（分布式应用、通信基础设施）
  - `端系统(End Systems/Hosts)`、通信链路、`分组交换机(Packet Switches)`（路由器和链路层交换机）
  - `协议(Protocol)` 的定义——定义了两个或多个通信实体之间交换报文的格式和顺序，以及收发/响应动作
  - `网络的网络(Network of Networks)`——Internet 由无数 ISP 网络互联构成
- **难点**：
  - "网络的网络" 的层级理解——从单一网络到 ISP 互联到全球 Internet 的抽象层次
  - 协议三要素（语法、语义、同步/时序）与编程中"接口/契约"概念的对应

### 1.2 [网络边缘](./1.2_Network_Edge.md)
- **核心**：
  - `端系统(End Systems)`——运行应用程序的主机（PC、手机、IoT 设备等）
  - `客户-服务器(Client-Server)` 模式——客户请求服务，服务器提供服务
  - `P2P(Peer-to-Peer)` 模式——端系统直接通信，兼具客户和服务器角色
  - `接入网(Access Network)` 的概念——将端系统物理连接到其边缘路由器(`Edge Router`)的网络
  - `连接服务`——面向连接服务(`Connection-oriented`) vs 无连接服务(`Connectionless`)
- **难点**：
  - 网络边缘与网络核心的边界——"边缘"是主机和接入网，"核心"是路由器构成的网状网络
  - 面向连接 vs 有连接——面向连接是服务特征（如 TCP），不一定有物理电路，与电路交换不同

### 1.3 [网络核心](./1.3_Network_Core.md)
- **核心**：
  - `分组交换(Packet Switching)`——存储转发、每个分组独立路由、统计复用、可能排队和延迟
  - `电路交换(Circuit Switching)`——预留端到端资源、专用带宽、无排队、时分复用(TDM) / 频分复用(FDM)
  - 分组交换 vs 电路交换——效率、灵活性、性能保证的权衡
  - `网络核心的网状拓扑`——路由器的互联结构，分组逐跳转发
- **难点**：
  - 分组交换的"存储转发"延迟计算——每个分组在每个路由器完整接收后才能转发，逐跳累积
  - 统计复用的原理——多用户共享链路但不同时高峰，实际吞吐量可能高于预留带宽，也可能拥塞
  - 电路交换的 TDM/FDM 与分组交换的统计复用对比——资源预留 vs 按需分配

### 1.4 [接入网和物理媒体](./1.4_Access_Networks_and_Physical_Media.md)
- **核心**：
  - `家庭接入(Home Access)`——`DSL(Digital Subscriber Line)`、电缆(`Cable`)、光纤(`FTTH`)、`WiFi`、`以太网(Ethernet)`
  - `企业/机构接入(Enterprise Access)`——局域网(LAN)连接边缘路由器
  - `无线接入(Wireless Access)`——`WLAN(Wireless LAN)`、蜂窝移动网络(4G/5G)
  - `物理媒体(Physical Media)`——双绞线(`Twisted Pair`)、同轴电缆(`Coaxial Cable`)、光纤(`Fiber Optic`)、无线/卫星(`Wireless/Satellite`)
  - `导引型媒体(Guided Media)` vs `非导引型媒体(Unguided Media)`
- **难点**：
  - 各种接入技术的速率、带宽、共享/独占特性对比——DSL 独占但受距离限制，Cable 共享总带宽但速率高
  - 物理媒体的实际传输特性——双绞线的抗干扰、光纤的全反射原理、无线信号的衰减和干扰

### 1.5 [Internet 结构和 ISP](./1.5_Internet_Structure_and_ISP.md)
- **核心**：
  - `ISP(Internet Service Provider)`——提供 Internet 接入服务的组织
  - `Tier-1 ISP`——全球覆盖、无提供商（如 Level 3、Sprint、AT&T），直接互联形成 Internet 骨干
  - `Tier-2 ISP`——区域覆盖，连接 Tier-1 ISP 获取全球连通性
  - `Tier-3 ISP`——本地 ISP，接入网提供商，连接 Tier-2
  - `IXP(Internet Exchange Point)`——ISP 对等互联的交换点，减少上游流量费用
  - `内容提供商网络(Content Provider Networks)`——Google、Microsoft 等私有网络直接与低层 ISP 或 IXP 互联，绕过高层 ISP
- **难点**：
  - ISP 层级结构的商业关系——提供商-客户(`Provider-Customer`) vs 对等(`Peer`)关系的费用和流量结算逻辑
  - 内容提供商私有网络的经济逻辑——绕过高层 ISP 以降低成本和延迟，改变传统 ISP 金字塔结构

### 1.6 [分组延迟、丢失和吞吐量](./1.6_Packet_Delay_Loss_and_Throughput.md)
- **核心**：
  - 四种延迟类型——`处理延迟(Processing Delay)`、`排队延迟(Queuing Delay)`、`传输延迟(Transmission Delay)`、`传播延迟(Propagation Delay)`
  - `总延迟(Total Delay)` = 处理 + 排队 + 传输 + 传播
  - `传输延迟` vs `传播延迟`——前者是"发完一个分组的时间"（分组长度/链路速率），后者是"比特在链路上跑的时间"（距离/传播速度）
  - `排队延迟` 的统计特性——流量强度 `Traffic Intensity = La/R`，接近1时延迟剧增，大于1时队列无限增长
  - `分组丢失(Packet Loss)`——队列满时路由器丢包，由端系统或上层协议恢复
  - `吞吐量(Throughput)`——实际端到端数据传输速率，取决于瓶颈链路(`Bottleneck Link`)
- **难点**：
  - 传输延迟和传播延迟的区分——经典类比：车队过收费站（传输延迟=发车队时间） vs 车队在高速上跑（传播延迟=跑时间），两者独立计算
  - 端到端吞吐量的瓶颈分析——`min(R1, R2, ..., Rn)`，文件传输时间 = 文件大小 / 吞吐量
  - 流量强度 `La/R` 的物理含义——`L` 分组长度(bit)，`a` 分组到达率(分组/秒)，`R` 链路速率(bit/s)，无量纲比值，>1 意味着到达快于发送

### 1.7 [协议层次和服务模型](./1.7_Protocol_Layers_and_Service_Models.md)
- **核心**：
  - `分层(Layering)` 思想——将复杂系统分解为可管理的层次，每层实现一种服务，通过层间接口交互
  - `五层协议栈`——`应用层(Application)`、`传输层(Transport)`、`网络层(Network)`、`链路层(Link)`、`物理层(Physical)`
  - `OSI 七层模型`——在五层基础上增加 `表示层(Presentation)` 和 `会话层(Session)`
  - `封装(Encapsulation)`——上层数据向下传递时添加头部信息，每层封装一次；解封装在接收端逆向进行
  - `服务(Service)`、`接口(Interface)`、`协议(Protocol)` 的区分——服务是层提供的功能，接口是层间交互方式，协议是层内对等实体通信规则
- **难点**：
  - 封装过程的逐层理解——每层添加什么头部？各层头部的作用？（以太网帧头、IP 头、TCP/UDP 头、应用层报文）
  - 服务、接口、协议的三元组区分——容易混淆"协议"和"服务"，协议是层内对等实体间通信规则，服务是层对上层提供的功能
  - OSI 表示层和会话层在实际 Internet 中的缺失——为什么 TCP/IP 五层模型更实用

### 1.8 [Internet 历史](./1.8_History_of_Internet.md)
- **核心**：
  - `ARPANET` 起源——1969 年美国国防部高级研究计划局，第一个分组交换网络
  - `TCP/IP` 协议的发展——1974 Vint Cerf 和 Bob Kahn 提出 TCP，后来分离为 TCP/IP
  - `NSFNET`——1980s 美国国家科学基金会的网络，推动了 Internet 的学术扩展
  - `Web 的诞生`——1989 Tim Berners-Lee 在 CERN 提出 WWW，1990s  Mosaic 浏览器推动大众普及
  - `商业化`——1990s 初 NSF 退出主干网运营，私人 ISP 接入，Internet 商业化爆发
  - `移动互联网与社交媒体`——2000s 后智能手机、云计算、社交网络、视频流媒体
- **难点**：
  - 历史事件的时序和因果关系——分组交换思想如何推动 ARPANET，TCP/IP 如何统一异构网络，Web 如何改变 Internet 使用模式
  - 技术演进与社会应用的互动——先有技术基础（分组交换+TCP/IP），后有应用创新（Web/Email），再反推基础设施发展（带宽、无线接入）

---

## 🔮 第1章展望

**下一章（第2章）**：
- 从宏观网络结构进入具体应用层协议
- `应用层(Application Layer)`——HTTP、FTP、DNS、P2P、CDN、套接字编程
- 理解"网络边缘"的应用如何通过网络核心提供的通信服务实现功能

---

> 🔗 **返回根目录**：[Course Notes Root](../README.md)
