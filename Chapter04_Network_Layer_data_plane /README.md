# 第4章 网络层：数据平面 (Network Layer: Data Plane)

> **章节定位**：聚焦网络层数据平面——每个路由器本地如何将到达的分组转发到合适的输出端口，涵盖路由器内部组成、IP协议（数据报格式、分片、编址、NAT、IPv6）以及SDN通用转发机制，为第5章控制平面做铺垫。

---

## 📋 章节导航与重难点

### 4.1 [导论](./4.1_Introduction.md)
- **核心**：
  - `转发(Forwarding)` 与 `路由(Routing)` 的区分——本地动作 vs 网络范围路径决策
  - `数据平面(Data Plane)` 与 `控制平面(Control Plane)` 的分离——本地转发 vs 全局路由
  - 两种控制平面实现：`传统Per-Router控制平面` vs `SDN逻辑集中控制平面`
- **难点**：
  - 理解转发和路由的边界——转发是数据平面功能，路由是控制平面功能，二者容易混淆
  - SDN "逻辑集中" 不等于 "物理集中"——远程控制器与本地控制代理(CA)的交互关系

### 4.2 [路由器组成](./4.2_Router_Composition.md)
- **核心**：
  - `输入端口(Input Port)`——查找转发表、最长前缀匹配、TCAM硬件实现
  - `交换结构(Switching Fabric)`——内存交换、总线交换、互联网络交换三种方式
  - `输出端口(Output Port)`——缓存、排队、调度机制
  - `HOL阻塞(Head-of-the-Line Blocking)`——输入队列中队首分组阻塞后续分组
- **难点**：
  - `最长前缀匹配(Longest Prefix Matching)` 的原理与TCAM实现——为什么不是精确匹配
  - 三种交换结构的性能差异和适用场景——内存 vs 总线 vs 互联网络的带宽限制
  - HOL阻塞的产生原因——即使交换结构有空闲，队首分组被阻塞导致后续分组无法转发

### 4.3 [IP: 因特网协议](./4.3_Internet_Protocol.md)
- **核心**：
  - `IP数据报格式`——20字节固定头部（版本、头部长度、TOS、总长、标识、标志、片偏移、TTL、上层协议、校验和、源/目的地址）
  - `分片与重组(Fragmentation & Reassembly)`——因MTU差异分片，仅在最终目的主机重组
  - `IPv4编址`——分类编址（A/B/C/D/E类）与 `CIDR(Classless Inter-Domain Routing)` a.b.c.d/x
  - `NAT(Network Address Translation)`——私有地址与公网地址转换，利用16位端口支持6万+并发连接
  - `IPv6`——128位地址、固定40字节头部、不允许分片、移除头部校验和
- **难点**：
  - IP分片机制的具体过程——标识(Identification)、标志(Flags)、片偏移(Fragment Offset)的协作逻辑
  - NAT端口映射与NAT穿越技术挑战——内网主机如何被外网主动访问
  - IPv6与IPv4的主要差异——为什么IPv6不允许分片、移除校验和

### 4.4 [通用转发和SDN](./4.4_Generalized_Forwarding_and_SDN.md)
- **核心**：
  - `匹配(Match)`——基于多个头部字段（不仅是目的IP），如OpenFlow的流表匹配
  - `行动(Action)`——转发、丢弃、修改字段等多种操作
  - `OpenFlow`——流表(Flow Table)实现通用转发的具体实例
  - `SDN架构`——控制平面与数据平面分离，远程控制器集中管理
- **难点**：
  - SDN与传统路由的架构差异——传统路由的控制平面分布在每台路由器，SDN集中控制
  - 通用转发的 "匹配+行动" 范式与传统最长前缀匹配转发的区别——字段更多、动作更灵活

---

## 🔮 第4章展望

**下一章（第5章）**：
- 离开网络层的`数据平面(Data Plane)`，深入网络层的`控制平面(Control Plane)`
- 路由算法：`链路状态(LS)`与`距离向量(DV)`
- Internet路由协议：`RIP`、`OSPF`、`BGP`
- SDN控制平面与`ICMP`协议

---

> 🔗 **返回根目录**：[Course Notes Root](../README.md)
