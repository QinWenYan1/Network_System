# 第3章 传输层 (Transport Layer)

> **章节定位**：传输层是网络协议栈的核心层次，负责端到端的可靠/不可靠数据传输。本章从传输层服务概述出发，深入讲解多路复用、UDP、可靠数据传输原理、TCP协议及拥塞控制机制。

---

## 📋 章节导航

| 小节 | 内容 | 笔记链接 |
|:---:|:---|:---:|
| **3.1** | 概述和传输层服务 (Overview and Transport Layer Services) | [笔记](./3.1_Transport_Layer_Overview.md) |
| **3.2** | 多路复用与解复用 (Multiplexing and Demultiplexing) | [笔记](./3.2_Multiplexing_and_Demultiplexing.md) |
| **3.3** | 无连接传输：UDP (Connectionless Transport: UDP) | [笔记](./3.3_UDP_User_Datagram_Protocol.md) |
| **3.4** | 可靠数据传输的原理 (Principles of Reliable Data Transfer) | [笔记](./3.4_Principles_of_Reliable_Data_Transfer.md) |
| **3.5** | 面向连接的传输：TCP (Connection-Oriented Transport: TCP) | [笔记](./3.5_TCP_Connection_Oriented_Transport.md) |
| **3.6** | 拥塞控制原理 (Principles of Congestion Control) | [笔记](./3.6_Principles_of_Congestion_Control.md) |
| **3.7** | TCP 拥塞控制 (TCP Congestion Control) | [笔记](./3.7_TCP_Congestion_Control.md) |

---

## 🎯 核心概念速览

### 传输层两大协议
- **TCP** (Transmission Control Protocol) — 面向连接、可靠传输、流量控制、拥塞控制
- **UDP** (User Datagram Protocol) — 无连接、不可靠、低开销、无拥塞控制

### 关键机制
| 机制 | 作用 |
|------|------|
| 多路复用/解复用 (Multiplexing/Demultiplexing) | 将多个应用的数据流整合到同一传输层通道，并在接收端正确分发给对应应用 |
| 可靠数据传输 (rdt) | 通过校验和、确认、重传、序号等机制在不可靠信道上实现可靠传输 |
| 流水线 (Pipelining) | 允许发送方连续发送多个分组而不等待确认，提高信道利用率 |
| 滑动窗口 (Sliding Window) | 控制发送/接收的分组范围，实现流量控制和可靠传输 |
| 拥塞控制 (Congestion Control) | 防止过多数据注入网络导致性能下降，TCP采用AIMD、慢启动等机制 |


---

## 📝 PPT 章节总结

### 一、传输层提供的服务
- **应用进程间的逻辑通信**
  - Vs 网络层提供的是**主机到主机**的通信服务
- **互联网上传输层协议**：UDP、TCP
  - 特性对比（见上表）

### 二、多路复用和解复用
- **端口**：传输层的 SAP（Service Access Point，服务访问点）
- **无连接**的多路复用和解复用
- **面向连接**的多路复用和解复用

### 三、实例1：无连接传输层协议 — UDP
- 多路复用解复用
- UDP 报文格式
- 检错机制：**校验和 (Checksum)**

### 四、可靠数据传输原理
- **问题描述**：如何在不可靠信道上实现可靠传输
- **停止等待协议**：
  - rdt 1.0 → 理想可靠信道
  - rdt 2.0 → 比特差错信道（停等 + ACK/NAK）
  - rdt 2.1 → ACK/NAK 也可能出错
  - rdt 2.2 → 无 NAK 的协议（只用 ACK）
  - rdt 3.0 → 比特差错 + 丢包信道（引入超时重传）
- **流水线协议**：
  - GBN（Go-Back-N，回退N帧）
  - SR（Selective Repeat，选择重传）

### 五、实例2：面向连接的传输层协议 — TCP
- **概述**：TCP 特性（面向连接、可靠、字节流）
- **报文段格式**
  - 序号 (Sequence Number)、确认号 (Acknowledgment Number)
  - 超时机制及时间（RTT 估计）
- **TCP 可靠传输机制**
- **重传、快速重传 (Fast Retransmit)**
- **流量控制 (Flow Control)**：滑动窗口
- **连接管理**
  - **三次握手**（建立连接：SYN → SYN-ACK → ACK）
  - **对称连接释放**（四次挥手 + TIME_WAIT）

### 六、拥塞控制原理
- **网络辅助的拥塞控制**
- **端到端的拥塞控制**

### 七、TCP 的拥塞控制
- **AIMD**（Additive Increase Multiplicative Decrease，加性增乘性减）
- **慢启动 (Slow Start)**
- **超时之后的保守策略**

---

## 📚 重点难点标记

🔴 **核心重点**
- rdt 状态机演变：rdt1.0 → rdt2.0 → rdt2.1 → rdt2.2 → rdt3.0
- 滑动窗口协议：GBN (Go-Back-N) vs SR (Selective Repeat)
- TCP 序号与确认号机制
- TCP 拥塞控制：慢启动、拥塞避免、快速恢复

🟡 **理解难点**
- 发送窗口 vs 接收窗口的互动过程
- GBN 与 SR 在异常情况下的差异
- TCP 往返时间 (RTT) 估计与超时设置
- AIMD 拥塞控制算法的动态行为

---

## 🔮 第三章展望

**下一章**：
- 离开网络 **"边缘"**（应用层和传输层）
- 深入到网络的 **"核心"**
- **2 个关于网络层的章节**：
  - 数据平面 (Data Plane)
  - 控制平面 (Control Plane)

---

> 🔗 **返回根目录**：[Network System Note](../README.md)
