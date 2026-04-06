# 📡 Network-Interview-Notes

> 计算机网络秋招面试复习笔记 | 中科大郑烇/杨坚视频课程 + Kurose实验

---

## 🎯 项目简介

本仓库用于系统学习计算机网络，为秋招面试做准备。

**核心资源**：
- 📺 **视频课程**：中科大郑烇、杨坚《计算机网络》（B站 BV1JV411t7ow）
- 📚 **配套教材**：《计算机网络：自顶向下方法》第7版
- 🔬 **实验练习**：Kurose官网 Wireshark Labs

---

## 🗺️ 学习路线图

```
阶段1：理论学习（2周）        阶段2：动手练习（穿插）        阶段3：面试冲刺（持续）
    │                              │                           │
    ▼                              ▼                           ▼
┌─────────────┐              ┌─────────────┐              ┌─────────────┐
│ 看中科大视频  │ ────────▶   │ 做Kurose Lab │ ────────▶   │ 背诵八股文   │
│ 整理笔记     │              │ 验证理解     │              │ 面试复盘     │
└─────────────┘              └─────────────┘              └─────────────┘
```

### 时间规划

| 章节 | 预计时间 | 重要程度 | 对应Lab |
|------|----------|----------|---------|
| Chapter01 | 1天 | ⭐⭐ | - |
| Chapter02 | 2天 | ⭐⭐⭐⭐⭐ | Lab2-HTTP |
| Chapter03 | 3天 | ⭐⭐⭐⭐⭐ | Lab3-TCP |
| Chapter04 | 2天 | ⭐⭐⭐⭐ | - |
| Chapter05 | 1天 | ⭐⭐⭐ | - |
| Chapter06 | 1天 | ⭐⭐⭐ | - |
| Chapter07-08 | 1天 | ⭐⭐ | - |

**总计**：约2周完成理论学习 + Lab练习

---

## 📁 仓库结构

```
Network-Interview-Notes/
│
├── 📄 README.md                                    ← 【本文件】总导航
├── 📄 .gitignore
│
├── 📁 Chapter01-Computer-Networks-and-Internet/    ← 第1章
│   ├── 📄 README.md                                ← 本章导航
│   ├── 📄 1.1-What-is-Internet.md                  ← 小节笔记
│   ├── 📄 1.2-Network-Edge.md
│   ├── 📄 1.3-Network-Core.md
│   └── 📁 Lab/                                     ← 本章练习
│
├── 📁 Chapter02-Application-Layer/                 ← 第2章
│   ├── 📄 README.md                                ← 本章导航
│   ├── 📄 2.1-Principles-of-Network-Apps.md
│   ├── 📄 2.2-The-Web-and-HTTP.md                  ⭐
│   ├── 📄 2.3-FTP.md
│   ├── 📄 2.4-Electronic-Mail.md
│   ├── 📄 2.5-DNS.md                               ⭐
│   └── 📁 Lab/
│       └── 📄 Lab2-HTTP-Wireshark.md               ← Kurose Lab2报告
│
├── 📁 Chapter03-Transport-Layer/                   ← 第3章 ⭐⭐⭐
│   ├── 📄 README.md                                ← 本章导航
│   ├── 📄 3.1-Introduction-and-Transport-Layer-Services.md
│   ├── 📄 3.2-Multiplexing-and-Demultiplexing.md
│   ├── 📄 3.3-Connectionless-Transport-UDP.md
│   ├── 📄 3.4-Principles-of-Reliable-Data-Transfer.md
│   ├── 📄 3.5-Connection-Oriented-Transport-TCP.md ⭐
│   ├── 📄 3.6-Principles-of-Congestion-Control.md
│   └── 📁 Lab/
│       └── 📄 Lab3-TCP-Wireshark.md                ← Kurose Lab3报告
│
├── 📁 Chapter04-Network-Layer-Data-Plane/          ← 第4章
│   ├── 📄 README.md
│   └── 📁 Lab/
│
├── 📁 Chapter05-Network-Layer-Control-Plane/       ← 第5章
│   ├── 📄 README.md
│   └── 📁 Lab/
│
├── 📁 Chapter06-Link-Layer-and-LANs/               ← 第6章
│   ├── 📄 README.md
│   └── 📁 Lab/
│
├── 📁 Chapter07-Wireless-and-Mobile-Networks/      ← 第7章
│   ├── 📄 README.md
│   └── 📁 Lab/
│
├── 📁 Chapter08-Security-in-Computer-Networks/     ← 第8章
│   ├── 📄 README.md
│   └── 📁 Lab/
│
├── 📁 99-Interview-Eight-Part/                     ← 八股文汇总
│   └── 📄 README.md
│
└── 📁 99-PPT-Materials/                            ← 原始PPT资料
    ├── 📁 Original/                                ← 老师给的原始PPT
    └── 📁 Annotated/                               ← 你的标注版本
```

---

## 📚 资源链接

### 视频课程
- **B站**：https://www.bilibili.com/video/BV1JV411t7ow
- **课程名**：中科大郑烇、杨坚《计算机网络（自顶向下方法 第7版）》

### 实验资源
- **Kurose官网**：https://gaia.cs.umass.edu/kurose_ross/index.php
- **Wireshark Labs**：https://gaia.cs.umass.edu/kurose_ross/wireshark.php

### 参考教材
- 《计算机网络：自顶向下方法》第7版，James F. Kurose & Keith W. Ross

### 面试资源
- JavaGuide计算机网络：https://javaguide.cn/cs-basics/network/
- 小林Coding计网：https://xiaolincoding.com/network/

---

## 🚀 快速开始

### 1. 放入PPT资料
将中科大老师给的PPT放入：
```
99-PPT-Materials/Original/
```

### 2. 学习流程
```bash
# 第1步：进入对应章节
cd Chapter02-Application-Layer/

# 第2步：查看本章导航
cat README.md

# 第3步：看中科大视频该章节

# 第4步：根据视频和PPT整理小节笔记
# 创建：2.1-XXX.md, 2.2-XXX.md ...

# 第5步：做对应Lab（如有）
# 在 Lab/ 目录下创建实验报告

# 第6步：更新本章导航 README.md
```

### 3. 笔记命名规范
- 格式：`节号-小节英文标题.md`
- 示例：`2.2-The-Web-and-HTTP.md`
- 用英文标题方便排序和识别

---

## 📝 各章节导航

| 章节 | 标题 | 进度 | Lab |
|------|------|------|-----|
| [Chapter01](./Chapter01-Computer-Networks-and-Internet/) | 计算机网络和因特网 | ☐ | - |
| [Chapter02](./Chapter02-Application-Layer/) | 应用层 | ☐ | Lab2-HTTP |
| [Chapter03](./Chapter03-Transport-Layer/) | 传输层 | ☐ | Lab3-TCP |
| [Chapter04](./Chapter04-Network-Layer-Data-Plane/) | 网络层：数据平面 | ☐ | - |
| [Chapter05](./Chapter05-Network-Layer-Control-Plane/) | 网络层：控制平面 | ☐ | - |
| [Chapter06](./Chapter06-Link-Layer-and-LANs/) | 链路层和局域网 | ☐ | - |
| [Chapter07](./Chapter07-Wireless-and-Mobile-Networks/) | 无线网络和移动网络 | ☐ | - |
| [Chapter08](./Chapter08-Security-in-Computer-Networks/) | 网络安全 | ☐ | - |

---

## 💡 笔记整理建议

### 笔记内容应包含：
1. **概念解释** - 用自己的话概括
2. **老师强调** - 视频中重点讲解的内容
3. **面试考点** ⭐ - 标注重要程度和常见问题
4. **图示** - 关键流程图、结构图
5. **与Lab的关联** - 对应哪个实验

### 示例笔记结构：
```markdown
# 2.2 The Web and HTTP

## 概念
...

## 老师强调
> "三次握手面试必考！"

## 面试考点 ⭐⭐⭐
**Q: HTTP和HTTPS的区别？**
答：...

## 图示
...

## 关联Lab
- Lab2-HTTP
```

---

## ✅ 学习检查清单

- [ ] Chapter01 完成（笔记 + 导航更新）
- [ ] Chapter02 完成 + Lab2-HTTP
- [ ] Chapter03 完成 + Lab3-TCP
- [ ] Chapter04 完成
- [ ] Chapter05 完成
- [ ] Chapter06 完成
- [ ] Chapter07 完成
- [ ] Chapter08 完成
- [ ] 八股文整理完成

---

## 🎓 秋招目标

完成本仓库学习后，你应该能自信回答：

- ✅ OSI七层模型和TCP/IP五层模型
- ✅ TCP三次握手/四次挥手细节及原因
- ✅ HTTP/HTTPS区别、HTTP版本演进
- ✅ DNS解析过程
- ✅ 从输入URL到页面显示的完整过程
- ✅ Cookie和Session的区别
- ✅ TCP拥塞控制算法
- ✅ Wireshark抓包分析能力

---

> 🕊️ *"计算机网络是后端开发的基石，花2周系统学习，秋招受益无穷。"*

---

**开始学习吧！** 🚀
