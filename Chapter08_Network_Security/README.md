# 第8章 网络安全 (Network Security)

> **章节定位**：聚焦网络通信中的安全威胁与防护机制——从密码学基础（加密、认证、完整性）到各层安全协议实现，再到边界防御（防火墙、IDS）和攻击对策，是网络体系中最关键的横切主题。

---

## 📋 章节导航与重难点

### 8.1 [什么是网络安全 ](./8.1_What_Is_Network_Security.md)
- **核心**：
  - 安全三大属性：`机密性(Confidentiality)`、`可认证性(Authentication)`、`报文完整性(Message Integrity)`
  - 安全场景：`安全电子邮件(Secure E-mail)`、`SSL`、`IPsec`、`802.11`
  - 安全参与方：`Alice`、`Bob`、`Trudy`（攻击者）的交互模型
- **难点**：
  - 区分"可认证性"和"完整性"——前者确认身份，后者确认内容未被篡改，二者常混淆
  - 理解"安全的定义是相对的"——不同场景需求不同（邮件 vs 无线 vs 网络层）

### 8.2 [加密原理](./8.2_Principles_of_Encryption.md)
- **核心**：
  - `对称加密(Symmetric Encryption)`：`DES`、`3DES`、`AES` 的代换-置换网络结构
  - `公开密钥加密(Public Key Encryption)`：`RSA` 基于大数分解难题
  - `RSA` 的数学基础：模幂运算、密钥生成流程、加密解密过程
- **难点**：
  - RSA 中 "公开密钥加密、私钥解密" 与 "私钥签名、公钥验证" 的反向使用——极易混淆
  - 对称加密和公钥加密的适用场景和效率对比——何时用哪个

### 8.3 [认证协议](./8.3_Authentication_Protocols.md)
- **核心**：
  - `ap4.0`：`不重数(Nonce)` 机制——通过大随机数防止重放攻击
  - `ap5.0`：使用 `公钥加密` 和 `数字签名` 实现双向认证
  - `中间人攻击(Man-in-the-Middle Attack)`：`Trudy` 伪装成双方分别通信
  - 中间人攻击的本质：`公钥分发` 环节缺乏认证导致
- **难点**：
  - 中间人攻击的"双向欺骗"逻辑——为什么即使使用公钥加密也会被攻破
  - 理解 "ap4.0 到 ap5.0 的演进" 中密钥分发问题的核心地位

### 8.4 [报文完整性](./8.3_Authentication_Protocols.md)
- **核心**：
  - `散列函数(Hash Function)`：`MD5`、`SHA-1`、`SHA-256`——输入任意长度，输出固定长度摘要
  - `报文鉴别码(MAC)`：`HMAC` 结合散列和密钥，提供认证+完整性
  - `数字签名(Digital Signature)`：私钥签哈希值，公钥验证——实现源端认证+完整性+不可抵赖
- **难点**：
  - 散列、MAC、数字签名三者的能力边界——谁提供认证？谁提供完整性？谁提供不可抵赖？
  - 区分 "MAC 需要共享密钥" 和 "数字签名需要非对称密钥对" 的使用场景差异

### 8.5 [密钥分发和证书](./8.5_Key_Distribution_and_Certificates.md)
- **核心**：
  - `对称密钥分发`：KDC（Key Distribution Center）和 `Kerberos` 认证协议
  - `公钥分发`：PKI（Public Key Infrastructure）体系
  - `数字证书(Digital Certificate)`：CA（Certificate Authority）签名绑定公钥和身份
  - `证书验证链`：根 CA → 中间 CA → 终端证书的信任传递
- **难点**：
  - KDC 的 "可信任第三方" 角色——为什么需要 TGS 和 AS 两级分离
  - 证书链验证的逻辑——为什么需要根 CA 预装，中间 CA 如何传递信任

### 8.6 [各个层次的安全性](./8.6_Security_At_Each_Layer.md)
- **核心**：
  - `安全电子邮件`：混合加密（对称加密报文+公钥加密会话密钥）+ 数字签名
  - `SSL/TLS`：三阶段握手（认证+交换 MS）→ 密钥导出（4 keys）→ 加密数据传输
  - `IPsec`：`AH`（认证+完整，协议号51）和 `ESP`（加密+认证+完整，协议号50）
  - `802.11i` 对 `WEP` 的改进：AES 加密 + 动态密钥分发 + 独立认证服务器（AS）
- **难点**：
  - SSL 的 "4 个 keys"（E_B, E_A, M_B, M_A）——区分加密密钥和 MAC 密钥，区分双向
  - `WEP` 的破解原理：24-bit IV 明文传输导致密钥流复用，流密码+XOR=已知明文即破解
  - `AH` 和 `ESP` 的能力对比——一个仅认证，一个加密+认证，考试常考

### 8.7 [访问控制：防火墙](./8.7_Access_Control_Firewalls.md)
- **核心**：
  - `分组过滤(Packet Filtering)`：无状态（逐包独立）vs 有状态（维护连接状态表）
  - `ACL(Access Control List)`：top→bottom 顺序匹配，默认 deny all
  - `应用网关(Application Gateway)`：代理模式，检查应用层数据内容
  - `IP Spoofing` 与入口过滤（Ingress Filtering）——路由器拒绝非法源地址
- **难点**：
  - 有状态 vs 无状态防火墙的规则差异——无状态需要写双向规则，有状态响应自动放行
  - 应用网关的 "代理中继" 模式——为什么不是透明转发，而是作为端点重建连接
  - 防火墙的折中：安全级别 vs 通信自由度，UDP 的 "全过或全不过" 困境

### 8.8 [攻击和对策](./8.8_Attacks_And_Countermeasures.md)
- **核心**：
  - `IDS(Intrusion Detection System)`：深度分组检查 + 分组间相关性分析（检测端口扫描、DoS）
  - `网络映射(Network Mapping)`：踩点、ping、端口扫描、nmap——攻击前置侦察
  - `分组嗅探(Packet Sniffing)`：广播介质 + 混杂模式 NIC，对策是交换式网络 + 加密
  - `DoS` 对策：`SYN cookies` 用加密 cookie 代替半开连接表项，防止 SYN flooding
- **难点**：
  - IDS vs 防火墙 vs IPS 的职能区分——检测、防御、检测+防御
  - DoS 对策的困境："throw out good with bad"——过滤泛洪会误伤正常请求
  - 入口过滤的局限：只能阻止外部伪造内部地址，不能全网覆盖



---

> 🔗 **返回根目录**：[Course Notes Root](../README.md)
