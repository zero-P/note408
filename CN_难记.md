## 绪论

+ 资源共享：软件、硬件、数据。

+ 协议数据单元 PDU，服务数据单元 SDU，协议控制信息 PCI

  n-SDU + n-PCI = n-PDU = (n-1)-SDU

+ 服务访问点 SAP

  指在同一系统中‍‍相邻两层的实体交换信息的逻辑接口，用于区分不同的服务类型。

  <u>**各层 SAP**</u>：

  数据链路层：帧的 “类型” 字段

  网络层：IP 数据报首部中的 “协议” 字段

  运输层：“端口号” 字段
  
+ 可靠服务：指网络具有**<u>纠错</u>**、**<u>检错</u>**、**<u>应答</u>**机制，能保证数据正确、可靠地传送到目的地。

  不可靠服务：指网络只是尽量让数据正确、可靠地传送到目的地，是一种尽力而为的服务。

  对于提供不可靠服务的网络，其网络的正确性、可靠性要由应用或用户来保障。

  对于误码率较低的信道，如以太网，数据链路层只需提供无确认、无连接的不可靠服务即可，数据传输的可靠性由高层负责

  有连接一定要有确认，无连接可以有确认可以无确认。

  如果是面向连接，那么应有用于建立连接的字段。

+ 两种 “点对点”

  点对点与端到端（通信方式）

  点对点与广播（传输技术）

+ 时延带宽积（以比特为单位的链路长度）

  传播时延 × 信道带宽

+ 在一段时间内链路中有多少比特取决于带宽（传输速率），而 1 比特 “跑” 了多远取决于传播速率。

+ 带宽

  在模拟信号系统中，带宽（又称频率带宽）用来表示频率范围，即最高频率和最低频率之差，单位 Hz。

  1）信号带宽：（模拟）信号所占据的频带宽度，单位 Hz。

  2）信道带宽：能够有效通过该（模拟）信道的（模拟）信号的最大频带宽度。

  在计算机网络中，带宽常用作<u>数字</u>信道所能传送的 “最高数据传输速率” 的同义语，即数字信道带宽，单位 b/s。
  
  为了与模拟信道带宽进行区分，数字信道带宽一般直接用波特率来描述。

## 物理层

+ 基带信号

  信源发出的没有经过调制（进行频谱搬移和变换）的原始电信号。

  其特点是频率较低，信号频谱从零频附近开始，具有低通形式。

  根据原始电信号的特征，基带信号可分为数字基带信号和模拟基带信号（相应地，信源也分为数字信源和模拟信源）。

  由于在近距离范围内基带信号的衰减不大，从而信号内容不会发生变化。因此在传输距离较近时，计算机网络都采用基带传输方式。如从计算机到监视器、打印机等外设的信号就是基带传输的。大多数的局域网使用基带传输，如以太网、令牌环网。常见的网络设计标准 10BaseT 使用的就是基带信号。

+ 基带调制/编码

  仅对基带信号的波形进行转化，使其能与信道特性相适应，调制后的信号仍是基带信号。

  由于基带调制是把数字信号转换为另一种形式的数字信号，人们通常将这个过程称为编码。

+ 载波

  指被调制以传输信号的波形，一般为正弦波。

  一般要求正弦载波的频率远远高于调制信号的带宽，否则会发生混叠，使传输信号失真。

+ 载波调制/带通调制

  利用高频载波信号携带低频基带信号，是一种将数字信息转换为模拟信号的通信技术。

+ 带通信号

  经过载波调制的信号称为带通信号，即仅在一段频率范围内能够通过信道。

+ 基带传输：传输基带信号。

  频带传输：传输带通信号。

  宽带传输：借助频带传输，将链路分解为两个或多个信道，每个信道可携带不同的信号。
  
+ 码元

  在通信系统中，常用一个固定时长的信号波形（数字脉冲）表示一位 $k$ 进制数字，代表不同离散数值的基本波形就称为码元。

  码元是数字通信中<u>数字信号</u>的计量单位，这个时长内的信号称为 $k$ 进制码元，而该时长称为码元宽度。

  码元既可以是多进制的，也可以是二进制的。

+ 码元传输速率/波特率/调制速率/符号率

  单位时间内数字通信系统所传输的码元数，单位波特 Baud。

  码元速率与进制数无关。

+ 信息传输速率/比特率

  单位时间内数字通信系统传输的二进制码元数（即比特数），单位 b/s。

+ 波特和比特是两个不同的概念，但波特率与比特率在数量上又有一定的关系。

  若用 $V$ 表示每个码元的离散数值/电平数目（即有 $V$ 种不同的码元），一个码元便携带 $\log_2{V}$ 比特的信息量，则波特率 $M$ Baud 对应的比特率为 $M\log_2{V}$ b/s。

  1 个码元携带 $n$（$n>1$）个比特时才适用 $n = \log_2{V}$ 的算法，$m$ 个码元携带 1 比特时即波特率是比特率的 $m$ 倍。

## 数据链路层

**<u>最大传送单元</u>**

每种链路层协议都会规定的帧的数据部分的长度上限，是权衡传输效率、传输差错概率、重传代价、传送单个数据报时延等的结果。

**<u>透明传输</u>**

指不论所传数据是什么样的比特组合（如和帧定界符相同的比特组合），都能按原样无差错地在这个数据链路上传输。

**<u>数据链路层为网络层提供的三种服务</u>**

1. 无确认的无连接服务（实时、不可靠）

   数据传输的可靠性由高层负责。

   适用于误码率较低的信道，如以太网。

2. 有确认的无连接服务（一般可靠）

   适用于误码率较高的信道，如无线通信。

3. 有确认的有连接（特别可靠）

   适用于可靠性要求较高的场合。

### 差错控制

#### 检错编码

**<u>奇偶校验码</u>**

奇校验码、偶校验码

**<u>循环冗余码</u>**

生成多项式 G(x)、帧检验序列 FCS

发送方的 FCS 生成和接收方的 CRC 检验都是由硬件实现的

若在传输过程中无差错，则经过 CRC 检验后得出的余数 R 肯定为 0。但是，若出现误码，则余数 R 仍为 0 的概率极低。因此，通过 CRC 检错技术，可以近似地认为 “凡是接收方数据链路层接受的帧均无差错”。也就是说，凡是接收方数据链路层接受的帧，我们都能以非常接近 1 的概率认为这些帧在传输过程中未产生差错。

CRC 具有纠错功能，但数据链路层仅使用了它的检错功能，检测到帧出错则直接丢弃，是为了方便协议的实现。

#### 纠错编码

**<u>海明码</u>**

实质是多重奇偶校验码（目前只看到多重偶校验）。在有效信息位中加入 n 个校验位组成海明码，n 个校验位能将海明码分成 n 组。分别对这 n 组进行奇偶校验，不但能检错，还能指出错位的位置，为自动纠错提供依据。

设 n 为有效信息的位数，k 为校验码的位数，则有 $\text{k} \geqslant \log_2(\text{n+k+1})$。

再加一位校验位（第 0 位）用于全校验，可实现检二纠一（不加只能检一纠一）

1. 全校验成功，组校验失败 → 检出两位错，重传
2. 全校验失败，组校验失败 → 检出一位错，纠正

检 n 位错，海明距 n + 1；纠 n 位错，海明距 2n + 1。

### 流量控制与可靠传输

**<u>可靠传输</u>**

指发送方发送的数据都能被接收方正确地接收。

通常采用**<u>确认</u>**和**<u>超时重传</u>**两种机制来实现。

① 确认：指接收方每次收到发送方发来的数据帧，都要向发送方发回一个确认帧，表示**<u>已正确收到</u>**该数据帧。

② 超时重传：指发送方在发送一个数据帧后就启动一个计时器，若在规定时间内没有收到所发送数据帧的确认帧，则重发该数据帧，直到发送成功为止。

使用这两种机制的可靠传输协议称为自动重传请求 ARQ，它意味着重传是自动进行的，接收方不需要对发送方发出重传请求。

在 ARQ 协议中，数据帧和确认帧都必须**<u>编号</u>**，以区分确认帧是对哪个帧的确认，以及哪些帧还未确认。

ARQ 协议分为三种：停止-等待 S-W 协议、后退 N 帧 GBN 协议、选择重传 SR 协议。这三种可靠传输协议的基本原理并不仅限于数据链路层，还可应用到其上各层。

有线网络的链路误码率较低，为了降低开销，并不要求数据链路层向其上层提供可靠传输服务，即使出现了误码，可靠传输的问题也由其上层处理。

无线网络的链路易受干扰，因此要求数据链路层必须向其上层提供可靠传输服务。

> 若一个协议使用确认机制对传输的数据进行确认，则可以认为它是一个可靠的协议。

**<u>数据链路层流量控制 vs 传输层流量控制</u>**

相同点：都用到了滑动窗口协议

不同点：

1）数据链路层控制的是相邻结点之间的流量；传输层控制的是端到端的流量。

2）数据链路层的控制手段是接收方收不下就不返回确认（收到的帧落在接收窗口之外则一律简单丢弃）；传输层的控制手段接收方通过确认报文段中的窗口值来调整发送方的发送窗口。

3）在数据链路层的滑动窗口协议中，窗口大小在传输过程中是固定的，而在传输层的滑动窗口协议中，发送窗口是可以动态调整的。

**<u>单帧滑动窗口与停止-等待协议 S-W</u>**（$W_T=1$，$W_R=1$）

有序接收。

没有与请求重发技术结合。

1 比特编号，发送的数据帧交替用 0 和 1 标识，确认帧分别用 ACK0 和 ACK1 表示。

为了超时重传和判定重复帧的需要，发送方和接收方都需要设置一个**<u>帧缓冲区</u>**。

接收方：①收到错误数据帧：简单丢弃  ②收到重复数据帧：丢弃 + 重传该数据帧的确认帧。

发送方：超时重传。

发送方会超时重传（没有按时收到确认帧）的情况：数据帧丢失/出错、确认帧丢失/出错。

接收方会收到重复数据帧的情况：确认帧丢失/出错。

**<u>多帧滑动窗口与后退 N 帧协议 GBN</u>**（$W_T>1$，$W_R=1$）

$W_R=1$ 可保证按序接收数据帧。

滑动窗口与请求重发技术的结合。

允许发送方在未收到确认帧的情况下，将序号在发送窗口内的多个数据帧全部发送出去。

允许接收方**<u>累积确认</u>**（可结合捎带确认）。

接收方只按序接受数据帧。

接收方：①收到出错数据帧：简单丢弃。②收到未按序（包含重复）的数据帧：丢弃 + 重发最后一个确认帧。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20240910101434621.png" width="600px"/></dev>

$1 < W_T < 2^n-1$（$n$ 比特编号）。

$W_R=1$ 可保证按序接收数据帧。

GBN 一方面因连续发送数据帧而提高了信道利用率，另一方面在重传时又必须重传原来已正确到达的帧（仅因这些帧的前面有一帧出错），因此这种做法会降低传送效率。当误码率较大时，GBN 不一定优于 S-W。

**<u>多帧滑动窗口与选择重传协议 SR</u>**（$W_T>1$，$W_R>1$）

为了进一步提高信道利用率，设法只重传出现差错和计时器超时的数据帧，此时必须加大接收窗口，以便先收下失序但正确到达且序号扔落在接收窗口内的那些数据帧，等到所缺序号的数据帧收齐后，再一并送交上层。

无序接收。

滑动窗口与请求重发技术的结合。

为了使发送方仅重传出错的帧，接收方不能再采用累积确认，而要对每个正确接收的数据帧逐一进行确认（单帧确认）。

接收方需设置数目等于接收窗口大小的帧缓冲区以暂存失序但正确到达且序号落在接收窗口内的数据帧。

每个发送缓冲区对应一个计时器。

接收方检出错帧：丢弃 + 发送**<u>否定帧 NAK</u>**，要求发送方立即重传 NAK 指定的数据帧。

① $W_T+W_R \leq 2^n$ ② $W_R \leq W_T$ $\rightarrow$ 一般 $W_T=W_R=2^{n-1}$。

**<u>信道利用率的分析</u>**

信道利用率是指信道的效率，从时间角度看，信道效率是对发送方而言的，是指发送方在一个发送周期（从发送方开始发送分组到收到第一个确认分组所需的时间）内，有效发送数据的时间与整个发送周期之比。

1）S-W 协议的信道利用率

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20240910112536514.png" width="600px"/></dev>

信道利用率 $U=\frac{T_{\mathrm{D}}}{T_{\mathrm{D}}+\mathrm{RTT}+T_{\mathrm{A}}}$（$T_{\mathrm{A}}$ 很短，默认忽略不计，看考题有没有说明）。

当 RTT 大于分组发送时延 $T_{\mathrm{D}}$ 时，信道利用率就非常低。

2）连续 ARQ 协议的信道利用率

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20240910112958501.png" width="600px"/></dev>

连续 ARQ 协议采用流水线传输，即发送方可连续发送多个分组，只要发送窗口足够大，就可使信道上有数据持续流动。

显然这种方式能获得很高的信道利用率。

假设连续 ARQ 协议的发送窗口大小为 $n$，即发送方可连续发送 $n$ 个分组，分为两种情况：

① $n T_{\mathrm{D}}<T_{\mathrm{D}}+\mathrm{RTT}+T_{\mathrm{A}}$（即在一个发送周期内可以发送完 $n$ 个分组）

信道利用率 $U=\frac{T_{n\mathrm{D}}}{T_{\mathrm{D}}+\mathrm{RTT}+T_{\mathrm{A}}}$。

② $n T_{\mathrm{D}} \geq T_{\mathrm{D}}+\mathrm{RTT}+T_{\mathrm{A}}$（即在一个发送周期内可以发不完或刚好发完 $n$ 个分组）

只要不发生差错，发送方就可不间断地发送分组，信道利用率为 1。

**<u>信道平均(实际)数据传输速率/信道吞吐率</u>**

= 信道利用率 × 信道带宽（最大数据传输速率）= 发送周期内发送的数据量/发送周期

### 信道划分介质访问控制

#### 时分复用 TDM

**<u>必须满足的条件</u>**

1. 介质的位速率（即每秒传输的二进制位数）大于单个信号的位速率。
2. 介质的带宽（即所能传输信号的最高频率与最低频率之差）大于结合信号的带宽（即所有信号经过调制后形成的复合信号的带宽）。

### 随机访问介质访问控制

#### ALOHA 协议

**<u>纯 ALOHA 协议</u>**

首次发送：自由发送，不进行任何检测。

冲突判断：在一段时间内未收到确认。

冲突重传：等待一段随机时间。

**<u>时隙 ALOHA 协议</u>**

每次发送：只能在每个时隙开始时才能发送帧。发送一帧的时间必须小于或等于时隙的长度。

每个帧到达后，一般都要在缓存中等待一段小于一个时隙的时间，才能发送出去。

冲突重传策略与纯 ALOHA 协议情况相似。

#### CSMA 协议

载波监听多路访问 CSMA (Carrier Sense Multiple Access)

每个站点在发送前先监听公用信道，发现信道空闲后再考虑发送。

**<u>1-坚持 CSMA</u>**

信道空闲：立即发送。

信道忙：继续坚持监听。

**<u>非坚持 CSMA</u>**

信道空闲：立即发送。

信道忙：放弃监听，等待一个随机时间后，再重新监听。

**<u>p-坚持 CSMA</u>**

信道空闲：以概率 $p$ 发送数据，以概率 $1-p$ 推迟到下一个时隙再继续监听。

信道忙：持续监听（等到下一个时隙再继续监听）。

#### CSMA/CD 协议

载波监听多路访问/冲突检测 CSMA/CD (Carrier Sense Multiple Access/Collision Detection)

先听后发，边听边发，冲突停发，随机重发。

信道空闲：立即发送，并坚持监听。

信道忙：坚持监听。

冲突判断：在争用期内检测到冲突。

冲突重传：采用截断二进制指数退避算法确定重传时机。重传 16 次仍不能成功，则停止重传并向上报错。

争用期/冲突窗口：以太网的端到端往返时间 2$\tau$。

以太网规定最短帧长为 64B，争用期长度为 51.2μs。

#### CSMA/CA 协议

载波监听多路访问/冲突避免 CSMA/CA (Carrier Sense Multiple Access/Collision Avoidance)

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20240926213440549.png" width="600px"/></dev>


### 轮询访问

在随机访问介质访问控制的基础上，限定了有权发送数据的结点只能有一个。

### 802.11 的 MAC 层

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241002213905644.png" width="400px" height="205px"/></dev>

1. 分布协调功能 DCF (Distributed Coordination Function)

   DCF 不采用任何中心控制，而是在每一个结点使用 CSMA 机制的分布式接入算法，让各个站通过争用信道来获取发送权。因此 DCF 向上提供争用服务。802.11 协议规定，所有的实现都必须有 DCF 功能。

2. 点协调功能 PCF (Point Coordination Function)

   PCF 是选项，是用接入点 AP 集中控制整个 BSS 内的活动，因此自组网络就没有 PCF 子层。PCF 使用集中控制的接入算法，用类似于探询的方法把发送数据权轮流交给各个站，从而避免了碰撞的产生。对于时间敏感的业务，如分组话音，就应使用提供无争用服务的点协调功能 PCF。

### 以太网

关键词：最流行的有线局域网技术、IEEE 802.3、逻辑总线、物理星形、广播、CSMA/CD、无连接、不可靠、曼彻斯特编码、违规编码法

<u>**MAC 地址**</u>

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/uttyuPasted-96.png" width="600px"/></dev>

两种记法都是按照字节的顺序发送，但每一个字节中先发送哪一位则不同：第一种记法先发送最高位，第二种记法先发送最低位。

局域网全球地址的法定管理机构 —— IEEE 的注册管理机构 RA (Registration Authority) 负责分配 6 字节地址字段中的前 3 个字节（即高位 24 位），称为组织唯一标识符 OUI (Organizationally Unique Identifier)，也叫公司标识符(company_id)。所有生产局域网适配器的厂家都必须向 IEEE 购买 OUI。

IEEE 规定地址字段第一个字节的最低位为 I/G 位(Individual/Group)，为 1 时表示组地址（用来多播），为 0 时表示单站地址。因此实际上 IEEE 只分配前 23 位。

地址字段第一个字节的最低第二位规定为 G/L 位（以太网几乎不理会），为 0 时是全球管理（保证在全球没有相同的地址），厂商向 IEEE 购买的 OUI 都属于全球管理。为 1 时是本地管理，用户可任意分配网络上的地址，采用 2 字节地址字段时全都是本地管理。

地址字段后 3 个字节（即低位 24 位）由厂家自行指派，称为扩展标识符(extended identifier)，只要保证没有重复即可。

一个公司可能有几个 OUI，也可能有几个公司合买一个 OUI。

## 网络层

### IPv4

**<u>IP 地址</u>**

实际上 IP 地址是标志一台主机/路由器和一条链路的接口。

路由器总是具有两个或两个以上的 IP 地址。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241110153907657.png" width="630px"/></dev>

**<u>IPv4 分组格式</u>**

与分片和重组有关的字段：标识、标志、片偏移。

不考虑 NAT，在整个传输过程中，IP 数据报中的源地址和目的地址都不会发生变换。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/jZKKwFByT4LrUZ5.png" width="480px"/></dev>

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241110153219828.png" width="600px"/></dev>

<u>**ICMP 相关**</u>

ICMP 被封装在 IP 数据报中发送，但 ICMP 不是高层协议，而是网络层协议。

常见需要发送 ICMP 报文的情况：

+ 若分组长度超过 MTU 而 DF = 1 时，则丢弃该分组，并向源主机发送 ICMP 差错报告报文（终点不可达）。

+ 路由器在转发分组前，先将 TTL 减 1，若 TTL 被减为 0，则丢弃该分组，并向源主机发送 ICMP 差错报告报文（时间超过）。

  或者说：路由器收到一个 TTL 值为 1 的 IP 数据报时

+ 路由器因拥塞而丢弃分组时，要向源主机发送 ICMP 差错报告报文（源点抑制）。

+ 若接收方 UDP 发现收到的报文中的目的端口号不正确（即不存在对应于端口号的应用进程），则丢弃该报文，并向发送方发送 ICMP 差错报文（端口不可达）。

不需要发送 ICMP 报文的情况：

+ 首部检验和错误

  只是简单丢弃。IP 协议（网络层）不保证可靠传输，并且此时源 IP 地址不一定正确。

<u>**DHCP**</u>

可以和 ARP 对比记忆。

### IPv6

**<u>与 IPv4 相比的更改</u>**

把首部中不必要的功能取消，字段数减少到只有 8 个（但长度增大了一倍，因为地址长度增大到 128 位）

1. 取消首部长度字段

   因为首部长度固定（40 字节）。

2. 取消区分服务字段

   其功能由优先级和流标号字段实现。

3. 取消总长度字段

   改用有效载荷长度字段。

4. 取消标识、标志和片偏移字段

   这些功能已包含在分片扩展首部中。

5. TTL 字段改称为跳数限制字段。

6. 取消协议字段

   改用下一个首部字段

7. 取消检验和字段

   精简网络层的差错检测，加快路由器处理数据报的速度。

8. 取消选项字段

   用扩展首部来实现选项功能。

**<u>扩展首部</u>**

IPv6 将 IPv4 数据报首部的选项功能放在扩展首部中，并把扩展首部留给路径两端的源点和终点的主机来处理。

RFC 2460 定义了六种扩展首部：逐跳选项、路由选择、分片、鉴别、封装安全有效载荷、目的站选项。使用多个扩展首部时，按以上的先后顺序出现。

每一个扩展首部都由若干个字段组成，字段长度各不相同。

所有扩展首部第一个字段都是 8 位的 “下一个首部” 字段。

**<u>冒号十六进制记法</u>**

+ 每 16 位二进制用 4 位十六进制（域），各域间用冒号分隔。

+ 各域数字前面连续的 0 可以省略，但域至少有一位数字。

+ 零压缩(zero compression)

  连续的 0 值域可以用一对冒号所取代。任一地址中只能使用一次。

  因为 0 值域的个数没有编码，所以需要从指定的域的个数来推算。

+ 可结合使用点分十进制记法的后缀（最后两个域）
  
  如 68E6 : 8C64 :: 18 : 128.10.2.1，在 IPv4 向 IPv6 的转换阶段特别有用。
  
+ CIDR 斜线表示法仍然可用。

### 从 IPv4 向 IPv6 过渡

**<u>思路</u>**

1. 只能逐步演进
2. IPv6 系统必须能够向后兼容（能够接收转发 IPv4 分组且能为其选择路由）

**<u>双协议栈</u>**(dual stack)

在完全过渡到 IPv6 前，使一部分主机/路由器装有双协议栈。

如果一台路由器的不同接口上分别配置了 IPv4 地址和 IPv6 地址，那么它很可能分别连接了 IPv4 网络和 IPv6 网络；如果一台主机装有双协议栈，则它将同时拥有 IPv4 地址和 IPv6 地址，并具备同时处理这两个协议地址的功能。

使用域名系统 DNS 查询目的主机采用哪种地址。

链路两端使用 IPv6，而路径存在 IPv4 网络，则需要使用首部转换方法，但最后恢复出的 IPv6 首部中的某些字段无法恢复（例如流标号，只能变为空缺）。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/fFCrNze1KtJOWY14.png" width="600px"/></dev>

**<u>隧道技术(tunneling)</u>**

IPv6 数据报要进入 IPv4 网络时，把 IPv6 数据报封装成 IPv4 数据报，使得整个 IPv6 数据报变成 IPv4 数据报的数据部分。

IPv4 数据报首部协议字段的值要设置为 41，从而使得双协议栈的主机知晓 IPv4 数据报里面封装的数据是一个 IPv6 数据报。

IPv4 数据报的源地址和目的地址要设置为隧道两端的路由器。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/dLyG3RU7irslHwK.png" width="600px"/></dev>

### OSPF

**<u>区域(area)</u>**

OSPF 将一个 AS 再划分为若干更小的区域。

目的：为了使 OSPF 能够用于规模很大的网络。

好处：把交换信息的范围局限于每一个区域而不是整个 AS，减少了整个网络上的通信量。

缺点：使交换信息的种类增多，同时也使 OSPF 协议更加复杂。

每个区域都有一个 32 位的区域标识符。

区域不能太大，在一个区域内的路由器最好不要超过 200 个。

使用层次结构的区域划分：

+ 上层区域叫做主干区域(backbone area)，标识符为 0.0.0.0，作用是用来连通其他在下层的区域。

+ 主干路由器(backbone router)：在主干区域内的路由器。

+ 自治系统边界路由器：主干区域内的一个专门和本 AS 外的其他 AS 交换路由信息的路由器。

+ 每个区域至少有一个区域边界路由器(area border router)，负责概括从其他区域来的信息。

  一个主干路由器可以同时是区域边界路由器。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/kwJsDq1MrTDOSM1.png" width="550px"/></dev>

会发送 LSU 的情况：

1. 邻站向自己请求某些链路状态项目的详细信息时。
2. 邻站的链路状态发生变化时。

### BGP

BGP 可以很容易的解决距离向量路由选择算法中的 “坏消息传播得慢” 的问题：

1. 当某个路由器或链路出故障时，由于 BGP 发言人可以从不止一个邻站获得路由信息，因此很容易选出新的路由。
2. 距离向量算法往往不能给出正确的选择，是因为这些算法不能指出哪些邻站到目的站的路由是独立的。

### IP 多播

**<u>IP 多播的分类</u>**

1. 只在本局域网上进行硬件多播。
2. 在互联网的范围进行多播。

**<u>IP 多播需要的两种协议</u>**

+ 网际组管理协议 IGMP

  让连接在本地局域网上的多播路由器知道本局域网上是否有主机（的某个进程）参加或退出了某个多播组。

+ 多播路由选择协议

  用来在多播路由器之间传播路由信息。

**<u>多个单播仿真多播</u>**

多个单播可以仿真多播，但是一个多播所需要的带宽要小于多个单播带宽之和；用多个单播仿真一个单播时，路由器的时延将很大，而处理一个多播分组的时延是很小的。

#### 在局域网上进行硬件多播

**<u>以太网多播地址范围</u>**（01-00-5E-00-00-00 到 01-00-5E-7F-FF-FF）

IP 多播之父 Steve Deering 在还是研究生的时候，为了要实际操作 IP 多播的验证雏型，需要专用的 MAC 地址来给多播数据报封包，在局域网上传输时使用。一开始他希望从 IEEE 申请分配 16 个连续的 OUI 作为 IP 多播对应的 MAC 地址使用（各自 28 位一一对应）。但 Steve 的经理 Jon Poste 不愿花 16000 美金购买 16 个 OUI，只购买了一个 OUI 即 00-00-5E，且只分配其中一半的地址提供给 Steve 用于研究。这样，多播 MAC 地址空间就只有 23 位。

I/G 位为 1 时为多播地址。

多播 IP 地址（28 位）与多播 MAC 地址（23 位）映射关系不唯一。

多播 IP 地址的数据包到达以太网，就要使用多播 MAC 地址进行封装。

多播 MAC 地址使用多播 IP 地址构造：高 25 位是固定的，而低 23 位是由 IP 多播地址的低 23 位直接映射而来；
同一个以太网可能存在多播 MAC 地址相同的多播组（这种情况要避免）。这些多播的成员在收到多播数据报时，还要在 IP 层利用软件进行过滤，把不是要接收的数据报丢弃。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/4Aojd8ewt0XWX3u.png" width="550px"/></dev>

#### IGMP

多播路由器不需保存组成员关系的准确记录（因为向局域网上的组成员转发数据使用硬件多播）。多播路由器只需知道网络上是否至少有一台主机是本组成员即可。实际上，对询问报文每一个组都只需有一台主机发送响应。

#### 多播路由选择协议

**<u>多播转发树</u>**

多播路由选择实际上就是要找出以源主机为根节点的多播转发树。

在多播转发树上，每一个多播路由器向树的叶节点方向转发收到的多播数据报。

多播转发树上的路由器不会收到重复的多播数据报（即多播数据报不应在互联网中兜圈子）。

不同的多播组对应于不同的多播转发树；同一个多播组对不同的源点也会有不同的多播转发树。

**<u>转发多播数据报时使用的三种方法</u>**

1. 洪泛与剪除

   <div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/TAeKvf4RU1MRQj3.png" width="400px"/></dev>

   适合较小的广播组。

   一开始使用洪泛法。

   为避免兜圈子，再采用反向路径广播 RPG(Reverse Path Broadcasting)策略：路由器收到多播数据报时，先检查该数据报是否是从源点经最短路径传送来的（看反向最短路径第一个路由器是否就是刚才把数据报送来的路由器）。若是则继续洪泛转发，若不是则丢弃。若存在多条最短路径，则选择这几条最短路径中的相邻路由器的 IP 地址最小的那条。

   剪除：多播转发树上的某路由器发现它的下游树枝已没有该多播组的成员，则应把它和下游树枝一起剪除。

   嫁接：当某个树枝有新增加的组成员时，可以再接入到多播转发树上。

2. 隧道技术(tunneling)/IP-in-IP

   适用于多播组的位置在地理上很分散的情况。

   多播数据报要通过不支持多播的网络时，由路由器对其进行再次封装，即再加上普通数据报首部，使之成为向单一目的站发送的单播数据报。

   通过 “隧道” 后，再由路由器剥去其首部，使它又恢复成原来的多播数据报，继续向多个目的站转发。

3. 基于核心的发现技术

   这种方法对于多播组的大小在较大范围内变化都合适。

   对每一个多播组 G 指定一个核心 (core) 路由器，并给出它的 IP 单播地址。

   核心路由器按照前面讲过的两种方法创建出对应于多播组 G 的转发树（核心路由器为根节点）。注意是为一个多播组构建一棵转发树，而不是为每个（源，组）组合构建一棵转发树。

   如果有一个路由器 R1 向核心路由器发送数据报，那么它在途中经过的每一个路由器都要检查其内容。当数据报到达参加了多播组 G 的路由器 R2 时，R2 就处理这个数据报。如果 R1 发出的是一个多播数据报，其目的地址是 G 的组地址，R2 就向 G 的成员转发这个多播数据报。如果 R1 发出的数据报是一个请求加入多播组 G 的数据报，R2 就把这个信息加到它的路由中，并用隧道技术向 R1 转发每一个多播数据报的副本。

**<u>一些建议使用的多播路由选择协议</u>**

+ 距离向量多播路由选择协议DVMRP (Distance Vector Multicast Routing Protocol)

+ 开放最短通路优先的多播扩展 MOSPF (Multicast extension to OSPF)

+ 基于核心的转发树 CBT (Core Based Tree)

+ 协议无关多播 PIM (Protocol Independent Multicast)

  使用和 CBT 同样的方法构成多播转发树。

  “协议无关”：在建立多播转发树时是使用单播数据报来和远程路由器联系的，但并不要求使用特定的单播路由选择协议。

  可以建立在任何路由器协议之上。

  又分为协议无关多播-稀疏方式 PIM-SM (Sparse Mode)、协议无关多播-密集方式 PIM-DM (Dense Mode)。

### 路由器

**<u>输入、输出端口</u>**

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241110152017790.png" width="500px"/></dev>

把帧的首尾部剥去后，分组被送入网络层处理。若是路由器之间交换路由信息的分组（如 RIP 或 OSPF 分组等）则交送给路由选择处理机；若是数据分组则按照分组首部中的目的地址查找转发表，根据结果经过交换结构到达合适的输出端口

输入/输出队列产生溢出时只能丢弃，造成分组丢失。

输入端口中的查找和转发功能在路由器的交换功能中最为重要。

交换结构分组传送速率＞输出链路发送速率，来不及发送的分组必须暂存在队列中。

<u>**常用的交换方法**</u>

1. 通过存储器

   <div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/fTqMeuZFXndz98D.png" width="250px"/></dev>

   最早使用的路由器利用普通计算机的 CPU 作为路由选择处理机，这样路由器的输入输出端口的功能和传统 OS 中的 I/O 设备一样。

   路由器交换速率一定小于存储器带宽（读/写）的一半。

2. 通过总线

   <div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/dqSMXARuZFEGLQ4.png" width="230px"/></dev>

   不需要路由选择处理机的干预。

   总线共享，被阻塞则需要排队等待，因此路由器转发带宽受总线速率的限制。

   现代技术已将总线带宽提高到每秒吉比特的速率，因此许多路由器产品都采用通过总线的交换方式。

3. 通过纵横交换结构(crossbar switch fabric)

   <div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/OoZX5EwO1xFfpQo.png" width="350px"/></dev>

   这种交换机构常称为互连网络。

   分为水平总线和垂直总线。

   有 2N 条总线，可使 N 个输入端口和 N 个输出端口相连接（这取决于相应的交叉结点是使水平总线和垂直总线接通还是断开）。

## 传输层

### UDP

<u>**UDP 检验**</u>

发送方：

1. 全 0 放检验和字段。

2. 添伪首部。

3. 数据部分补全 0 字节（非偶时）。

4. 2B 串依次二进制求和。最高位若有进位则需要回卷。

5. 求和结果取反，写入检验和字段。

   若检验和结果恰好为 0，则改置为全 1。

6. 伪首部和补上的全 0 字节（若有）不发送。

接收方：

1. 添伪首部。

2. 数据部分补全 0 字节（非偶时）。

3. 2B 串依次二进制求和。最高位若有进位则需要回卷。

4. 求和结果取反。

5. 无差错时检验和结果应为全 1。

   有差错时一般直接丢弃；也可以交付上层处理，但需要附上错误报告。 

> 伪首部 (12B)：源 IP (4B) + 目的 IP (4B) + 全 0 (1B) + 协议 17D (1B) + UDP 长度 (2B)

### TCP

<u>**TCP 检验**</u>

同 UDP 检验，只需将伪首部协议字段改为 6，UDP 长度字段改为 TCP 长度。

#### TCP 连接管理

SYN 报文段不能携带数据，但要消耗掉一个序号。

FIN 报文段即使不携带数据，也要消耗掉一个序号。

服务器进入 CLOSE-WAIT 状态，意味着 TCP 连接处于半关闭状态，从客户机到服务器这个方向的连接就释放了。

服务器端的资源是在完成第二次握手时分配的，而客户端的资源是在完成第三次握手时分配的，这就使得服务器易于收到 SYN 洪泛攻击。

**<u>采用三次而非两次握手建立连接的原因</u>**

1. 防止旧的重复连接启动造成混淆

   两次握手可能会使得服务器在收到已失效的连接请求时去建立一个历史连接，即服务器在第一次握手时就进入 ESTABLISHED 状态，这意味着导致服务器会自顾自地白白发送数据，这就造成了服务器的资源被浪费。

   在三次握手机制下，客户端在收到服务器连接接受报文后，可以根据自身的上下文，判断这是一个历史连接（序列号过期或超时），客户端就会发送 RST 报文给服务端，表示中止这一次连接。

2. 同步双方初始序列号

   序列号在 TCP 连接中占据着非常重要的作用，所以当客户端发送携带「初始序列号」的 SYN 报文的时候，需要服务端回一个 ACK 应答报文，表示客户端的 SYN 报文已被服务端成功接收，那当服务端发送「初始序列号」给客户端的时候，依然也要得到客户端的应答回应，这样一来一回，才能确保双方的初始序列号能被可靠的同步。

   四次握手其实也能够可靠的同步双方的初始化序号，但由于第二步和第三步可以优化成一步，所以就成了「三次握手」。

**<u>建立连接时不能每次都选择相同的或固定的初始序号的原因</u>**

工作在新的 TCP 连接的主机可能会接收在旧的连接传送的、已无意义、过时的 TCP 报文段（这些 TCP 报文段的序号有可能正好处在当前新连接所用的序号范围中），结果产生错误。因此，必须使得迟到的 TCP 报文段的序号不处在新连接所用的序号范围中。

<u>**第四次挥手必须等待 2MSL 后才进入 CLOSED 状态的原因**</u>

1. 若 A 的第四次挥手报文段中途丢失，B 会超时重传第三次挥手报文段，A 可在第四次挥手发送后的 2MSL 内收到这个重传报文段。

2. 防止已失效的连接请求报文段出现

   A 发送最后一个确认报文段后，再经过 2MSL 可保证本连接持续的时间内所产生的所有报文段从网络中消失。

#### TCP 拥塞控制

发送方是如何知道网络发生了拥塞呢？我们知道，当网络发生拥塞时，路由器就要丢弃分组。因此只要发送方没有按时收到应当到达的确认报文，也就是说，只要出现了超时，就可以猜想网络可能出现了拥塞。现在通信线路的传输质量一般都很好，因传输出差错而丢弃分组的概率是很小的（远小于 1%）。因此，判断网络拥塞的依据就是出现了超时。

乘法减小 MD (Multiplicative Decrease)：一旦出现超时或 3 个重复的确认，就要把门限值设置为当前拥塞窗口值的一半，并大大减小拥塞窗口的数值。

加法增大 AI (Additive Increase)：拥塞避免阶段，拥塞窗口按照线性规律增大。

二者合在一起就是所谓的 AIMD 算法。

**<u>TCP 拥塞控制的流程</u>**

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241111210314710.png" width="600px"/></dev>

**<u>慢开始</u>**

慢开始算法的思路是这样的：当主机开始发送数据时，由于并不清楚网络的负荷情况，所以如果立即把大量数据字节注入到网络，那么就有可能引起网络发生拥塞。经验证明，较好的方法是先探测一下，即由小到大逐渐增大发送窗口，也就是说，由小到大逐渐增大拥塞窗口数值。

旧的规定是这样的：在刚刚开始发送报文段时，先把初始拥塞窗口 cwnd 设置为 1 至 2 个发送方的最大报文段 SMSS(Sender Maximum Segment Size) 的数值，但新的 RFC 5681 把初始拥塞窗口 cwnd 设置为不超过 2 至 4 个SMSS 的数值。具体的规定如下：

+ 若 SMSS > 2190 字节，则设置初始拥塞窗口 cwmd = 2 x SMSS 字节，且不得超过 2 个报文段。
+ 若 1095 字节 < SMSS ≤ 2190 字节，则设置初始拥塞窗口 cwnd = 3 x SMSS 字节，且不得超过 3 个报文段。
+ 若 SMSS ≤ 1095 字节，则设置初始拥塞窗口 cwnd = 4 x SMSS 字节，且不得超过 4 个报文段。

慢开始规定，在每收到一个对新的报文段的确认后，可以把拥窗口增加最多一个 SMSS 的数值。更具体些，就是拥塞窗口 cwnd 每次的增加量 = min(N, SMSS)，其中 N 是原先未被确认的、但现在被刚收到的确认报文段所确认的字节数。不难看出，当 N < SMSS 时，拥塞窗口每次的增加量要小于 SMSS。

虽然实际上 TCP 是用字节数作为窗口大小的单位。但为叙述方便起见，课本用报文段的个数作为窗口大小的单位，这样可以使用较小的数字来阐明拥塞控制的原理。

发送方每收到一个对新报文段的确认（重传的不算在内）就使发送方的拥塞窗口加 1，故每经过一个传输轮次，拥塞窗口 cwnd 就加倍。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241111175336160.png" width="500px"/></dev>

一个传输轮次所经历的时间其实就是往返时间 RTT（请注意，RTT 并非是恒定的数值）。使用 “传输轮次” 是更加强调：把拥塞窗口 cwnd 所允许发送的报文段都连续发送出去，并收到了对已发送的最后一个字节的确认。例如，拥塞窗口 cwnd 的大小是 4 个报文段，那么这时的往返时间 RTT 就是发送方连续发送 4 个报文段，并收到这 4 个报文段的确认，总共经历的时间。

顺便指出，图 5-24 只是为了说明慢开始的原理。在 TCP 的实际运行中，发送方只要收到一个对新报文段的确认，其拥塞窗口 cwnd 就立即加 1，并可以立即发送新的报文段，而不需要等这个轮次中所有的确认都收到后（如图 5-24 所示的那样）再发送新的报文段。

<u>**拥塞避免**</u>

慢开始门限 ssthresh 的用法如下：

+ 当 cwnd < ssthresh 时，使用上述的慢开始算法。
+ 当 cwnd > ssthresh 时，停止使用慢开始算法而改用拥塞避免算法
+ 当 cwnd = ssthresh 时，既可使用慢开始算法，也可使用拥塞避免算法。

拥塞避免算法的思路是让拥塞窗口 cwnd 缓慢地增大，即每经过一个往返时间 RTT 就把发送方的拥塞窗口 cwnd 加 1，而不是像慢开始阶段那样加倍增长。因此在拥塞避免阶段就有 “加法增大” AI (Additive Increase) 的特点。这表明在拥塞避免阶段，拥塞窗口 cwnd 按线性规律缓慢增长，比慢开始算法的拥塞窗口增长速率缓慢得多。

> 请注意，因为现在是讲原理，把窗口的单位改为报文段的个数。实际上应当是 “拥塞窗口仅增加一个 MSS 的大小，单位是字节”。在具体实现拥塞避免算法的方法时可以这样来完成：只要收到一个新的确认，就使拥塞窗口 cwnd 增加 MSS x MSS/cwnd 个字节。例如，假定 cwnd 等于 10 个 MSS 的长度，而 MSS 是 1460 字节。发送方可一连发送 14600 字节（即 10 个报文段）。假定接收方每收到一个报文段就发回一个确认。于是发送方每收到一个新的确认，就把拥塞窗口稍微增大一些，即增大 0.1 MSS = 146 字节。经过一个往返时间 RTT（或一个传输轮次）后，发送方共收到 10 个新的确认，拥塞窗口就增大了 1460 字节，正好是一个 MSS 的大小。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241111204954185.png" width="700px"/></dev>

**<u>快重传</u>**

有时，个别报文段会在网络中丢失，但实际上网络并未发生拥塞。如果发送方迟迟收不到确认，就会产生超时，就会误认为网络发生了拥塞。这就导致发送方错误地启动慢开始，把拥塞窗口 cwnd 又设置为 1，因而降低了传输效率。

采用快重传算法可以让发送方尽早知道发生了个别报文段的丢失。

快重传算法首先要求接收方不要等待自己发送数据时才进行捎带确认，而是要立即发送确认，即使收到了失序的报文段也要立即发出对已收到的报文段的重复确认。

快重传算法规定，发送方只要一连收到 3 个重复确认，就知道接收方确实没有收到报文段 M2，因而应当立即进行重传（即 “快重传”），这样就不会出现超时，发送方也不就会误认为出现了网络拥塞。使用快重传可以使整个网络的吞吐量提高约 20%。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241111211227022.png" width="500px"/></dev>

注意，发送方共收到了接收方的 4 个对 M2 的确认，其中后 3 个是重复确认。

**<u>快恢复</u>**

在图 5-25 中的点，发送方知道现在只是丢失了个别的报文段。于是不启动慢开始，而是执行快恢复算法。这时，发送方调整门限值 ssthresh = cwnd/2 = 8（乘法减小），同时设置拥塞窗口 cwnd = ssthresh = 8（见图 5-25 中的点 6），并开始执行拥塞避免算法。

也有的快恢复实现是把快恢复开始时的拥塞窗口 cwnd 值再增大一些（增大 3个报文段的长度），即等于新的 ssthresh + 3 x MSS。这样做的理由是：既然发送方收到 3 个重复的确认，就表明有 3 个分组已经离开了网络。这 3 个分组不再消耗网络的资源而是停留在接收方的缓存中（接收方发送出 3 个重复的确认就证明了这个事实）。可见现在网络中并不是堆积了分组而是减少了 3 个分组。因此可以适当把拥塞窗口扩大些。

## 应用层

### DNS

**<u>域名</u>**

从语法上讲，每一个域名都由标号(label)序列组成，而各标号之间用点隔开。

国家顶级域名可以使用一个国家自己的文字。例如，中国可以有 “.cn”、“.中国” 和 “.中國” 这三种不同形式的域名。

**<u>域名服务器</u>**

一个服务器所负责管辖的（或有权限的）范围叫做区(zone)。各单位根据具体情况来划分自己管辖范围的区。但在一个区中的所有节点必须是能够连通的。每一个区设置相应的权限域名服务器(authoritative name server)，用来保存该区中的所有主机的域名到 IP地址的映射。总之，DNS 服务器的管辖范围不是以 “域” 为单位，而是以 “区” 为单位。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241112220845973.png" width="600px"/></dev>

不难看出，区是 “域” 的子集。区可能等于或小于域，但一定不能大于域。

到 2016 年 2 月，全世界已经在 588 个地点（地点数值还在不断增加）安装了根域名服务器，但这么多的根域名服务器却只使用 13 个不同 IP 地址的域名，即 a.rootservers.net, b.rootservers.net , … ,m.rootservers.net。每个域名下的根域名服务器由专门的公司或美国政府的某个部门负责运营。但请注意，虽然互联网的根域名服务器总共只有 13 个域名，但这不表明根域名服务器是由 13 台机器所组成（如果仅仅依靠这 13 台机器，根本不可能为全世界的互联网用户提供令人满意的服务）。实际上，在互联网中是由 13 套装置构成这 13 组根域名服务器。每一套装置在很多地点安装根域名服务器（也可称为镜像根服务器），但都使用同一个域名。为了提供更可靠的服务，在每一个地点的根域名服务器往往由多台机器组成（为了安全起见，有些根域名服务器的具体地点还是保密的）。现在世界上大部分 DNS 域名服务器，都能就近找到一个根域名服务器查询 IP 地址（这些根域名服务器都已增加了 IPv6 地址）。

由于根域名服务器采用了任播(anycast)技术，因此当 DNS 客户向某个根域名服务器的 IP 地址发出查询报文时，互联网上的路由器就能找到离这个DNS客户最近的一个根域名服务器。这样做不仅加快了DNS 的查询过程，也更加合理地利用了互联网的资源。

### FTP

<u>**工作流程**</u>（主动模式）

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/6-19111215063rfdfrfr924.png" width="420px"/></dev>

1. 建立控制连接

   该阶段是 FTP 客户端通过 TCP 三次握手与 FTP 服务器端进行建立控制连接。

   客户端向 FTP 服务器发出建立控制连接请求，FTP 服务器对请求进行应答。如果 FTP 服务器上的 21 端口是启用的，可以接受的请求，给出应答 220，表示服务就绪，即告诉客户端需要的 FTP 服务已经准备好了。

   返回应答以后，FTP 服务器需要客户端进行身份认证，向客户端发送身份认证请求。

2. 身份认证

   身份认证是指客户端需要向 FTP 服务提供登录所需的用户名和密码。FTP 服务器对客户端输入的用户名和密码都会给出相应的应答。如果客户端输入的用户名和密码正确，将成功登录 FTP 服务器，此时进入 FTP 会话。

3. 命令交互与数据传输

   客户端打开一个随机端口，并将该端口号（实际是 IP + 端口号）随着 PORT 命令通过控制连接发送给服务器。服务器收到这个命令后，使用 20 号端口建立一个 TCP 连接（数据连接）到客户端指定的端口，以便开始数据传输。

   用户可以执行多种 FTP 命令进行文件传输，如查看目录信息、上传或下载文件等。客户端输入要执行的 FTP 命令后，服务器同样会给出应答。如果输入的命令正确，服务器会将命令的执行结果返回给客户端。执行结果返回完成后，服务器继续给出应答。

4. 断开连接

   数据传输完毕后，数据连接最先释放，控制连接最后释放。

**<u>采用带外传送的原因/好处</u>**

使用两条独立的连接可使 FTP 变得更加简单、更容易实现、更有效率。同时在文件传输过程中还可以利用控制连接控制传输过程，如客户可以请求终止、暂停传输等。

### HTTP

**<u>面向事务</u>**

所谓事务(transaction)就是指一系列的信息交换，而这一系列的信息交换是一个不可分割的整体，也就是说，要么所有的信息交换都完成，要么一次交换都不进行。

**<u>状态码</u>**

```assembly
1xx 表示通知信息,如请求收到了或正在进行处理
2xx 表示成功,如接受或知道了
3xx 表示重定向,如要完成请求还必须采取进一步的行动
4xx 表示客户的差错,如请求中有错误的语法或不能完成
5xx 表示服务器的差错,如服务器失效无法完成请求
```

常见状态码：

```assembly
200 OK                      请求成功       一般用于GET与POST请求
204	No Content              无内容         服务器成功处理,但未返回内容,在未更新网页的情况下,可确保浏览器继续显示当前文档
301	Moved Permanently       永久性重定向
302	Found	                临时性重定向
400 Bad Request             请求错误       客户端请求的语法错误,服务器无法理解
403 Forbidden	            不被允许的请求  服务器理解请求客户端的请求,但是拒绝执行此请求
404	Not Found               找不到         所请求的资源无法找到
500	Internal Server Error	服务器内部错误  无法完成请求,也可能是web应用存在bug或某些临时故障
502 Bad Gateway             网关错误       通常是服务器作为网关或代理时返回的错误码
503	Service Unavailable	    服务不可用      由于超时或系统维护,服务器暂时的无法处理客户端的请求
```

若请求的网页从 http://www.zerooop.top/index.html 转移到了一个新的地址，则响应报文的状态行和一个首部行就是下面的形式：

```assembly
HTTP/1.1 301 Moved Permanently            {永久性地转移了}
Location: http://www.zerooop.top/ee/index.html {新的URL}
```

**<u>请求方法</u>**

+ HEAD 方法

  HEAD 方法跟 GET 方法类似，只不过服务器响应时不会返回消息体。即一个 HEAD 请求的响应中，HTTP 头中包含的元信息应该和一个 GET 请求的响应消息相同。即只请求资源的首部。

  用处：检查超链接的有效性；检查网页是否被修改；多用于自动搜索机器人获取网页的标志信息，获取 rss 种子信息，或者传递安全认证信息等。

+ POST 方法

  新增或提交数据，侧重数据的增加。不是幂等的。

+ PUT 方法

  侧重数据的修改；幂等。

### 电子邮件

#### MIME

<u>**SMTP 的缺点**</u>

1. 不能传送可执行文件或其他的二进制对象。

2. 限于传送 7 位的 ASCII 码，许多其他非英语国家的文字就无法传送。

3. SMTP 服务器会拒绝超过一定长度的邮件。

4. 某些 SMTP 的实现并没有完全按照 SMTP 的互联网标准。常见的问题如下：

   1）回车、换行的删除和增加；

   2）超过 76 个字符时的处理：截断或自动换行；

   3）后面多余空格的删除；

   4）将制表符 tab 转换为若干个空格。

<u>**新增的邮件首部字段**</u>

+ MIME-Version：标志 MIME 的版本。现在的版本号是 1.0。若无此行，则为英文文本。
+ Content-Description：这是可读字符串，说明此邮件主体是否是图像、音频或视频。
+ Content-ld：邮件的唯一标识符。
+ Content-Transfer-Encoding：在传送时邮件的主体是如何编码的。
+ Content-Type：说明邮件主体的数据类型和子类型。

#### SMTP 通信

发送方邮件服务器 A（SMTP 客户）向接收方邮件服务器 B（SMTP 服务器）发送邮件。

SMTP 不使用中间的邮件服务器。

<u>**连接建立**</u>

+ UA 将发件人的邮件发送到 A 的邮件缓存。

+ A 每隔一定时间对缓存扫描一次，如发现有邮件，就与 B 建立 TCP 连接（端口号 25）。

+ 连接建立后，B 发出 “220 Service ready”（服务就绪）。
+ A 向 B 发送 HELO 命令，附上发送方的主机名。
+ B 若有能力接收邮件，则回答 “250 OK”，表示已准备好接收；若B 不可用，则回答 “421 Service not available”（服务不可用）。

**<u>邮件传送</u>**

+ 邮件的传送从 MAIL 命令开始。

  MAIL 命令后面有发件人的地址。如 MAIL FROM: \<xiexiren@tsinghua.org.cn>。若 B 已准备好接收邮件，则回答 “250 OK”。否则，返回一个代码，指出原因。如 451 (处理时出错)，452 (存储空间不够)，500 (命令无法识别) 等。

+ 下面跟着一个或多个 RCPT 命令，取决于把同一个邮件发送给一个或多个收件人。

  其格式为 RCPT TO: <收件人地址>。每发送一个 RCPT命令，都应当有相应的信息从 B 返回，如 “250 OK”，表示指明的邮箱在接收方的系统中，或 “550 No such user here” (无此用户)，即不存在此邮箱。

+ 再下面就是 DATA 命令，表示要开始传送邮件的内容了。

  B 返回的信息是 “354 Start mail input; end with \<CRLF>.\<CRLF>”。这里 \<CRLF> 是 “回车换行” 的意思。若不能接收邮件，则返回 421 (服务器不可用)，500 (命令无法识别) 等。

+ 接着 A 就发送邮件的内容。发送完毕后，再发送 \<CRLF>.\<CRLF>（两个回车换行中间用一个点隔开）表示邮件内容结束。实际上在服务器端看到的可打印字符只是一个英文的句点。若邮件收到了，则 B 返回信息 “250OK”，或返回差错代码。

**<u>连接释放</u>**

邮件发送完毕后，A 应发送 QUIT 命令。B 返回的信息是 “221 (服务关闭)”，表示 SMTP 同意释放 TCP连接。

邮件传送的全部过程即结束。

