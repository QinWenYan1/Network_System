# 第3章 传输层 (Transport Layer)

> **章节定位**：传输层是网络协议栈的核心层次，负责端到端的可靠/不可靠数据传输。本章从传输层服务概述出发，深入讲解多路复用、UDP、可靠数据传输原理、TCP协议及拥塞控制机制。

---

## 📋 章节导航

| 小节 | 内容 | 笔记链接 |
|:---:|------|:--------:|
| **3.1** | 概述和传输层服务 (Overview and Transport Layer Services) | [笔记](./3.1_Transport_Layer_Overview.md) |
| **3.2** | 多路复用与解复用 (Multiplexing and Demultiplexing) | [笔记](./3.2_Multiplexing_and_Demultiplexing.md) |
| **3.3** | 无连接传输：UDP (Connectionless Transport: UDP) | [笔记](./3.3_UDP_User_Datagram_Protocol.md) |
| **3.4** | 可靠数据传输的原理 (Principles of Reliable Data Transfer) | [笔记](./3.4_Principles_of_Reliable_Data_Transfer.md) |
| **3.5** | 面向连接的传输：TCP (Connection-Oriented Transport: TCP) | [笔记](./3.5_TCP_Connection_Oriented_Transport.md) |
| **3.6** | 拥塞控制原理 (Principles of Congestion Control) | [笔记](./3.6_Principles_of_Congestion_Control.md) |
| **3.7** | TCP 拥塞控制 (TCP Congestion Control) | [笔记](./3.7-TCP拥塞控制.md) |

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

## 🏁 学习路径建议

```
3.1 传输层服务概述 → 3.2 多路复用/解复用 → 3.3 UDP协议
    ↓
3.4 可靠数据传输原理（rdt1.0 → rdt2.0 → rdt2.1 → rdt2.2 → rdt3.0）
    ↓
3.4 流水线 + 滑动窗口（GBN / SR 协议）
    ↓
3.5 TCP协议（报文结构、序号/确认号、RTT估计）
    ↓
3.6 拥塞控制原理 → 3.7 TCP拥塞控制
```

---

## 📚 重点难点标记

🔴 **核心重点**
- rdt状态机演变：rdt1.0 → rdt2.0 → rdt2.1 → rdt2.2 → rdt3.0
- 滑动窗口协议：GBN (Go-Back-N) vs SR (Selective Repeat)
- TCP序号与确认号机制
- TCP拥塞控制：慢启动、拥塞避免、快速恢复

🟡 **理解难点**
- 发送窗口 vs 接收窗口的互动过程
- GBN与SR在异常情况下的差异
- TCP往返时间(RTT)估计与超时设置
- AIMD拥塞控制算法的动态行为

---

> 🔗 **返回根目录**：[Network System Note](../README.md)
