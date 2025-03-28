## 总线概述

早期计算机的各部件之间是通过单独的连线互连的，这种方式称为<u>分散连接</u>。但是，随着 IO 设备的种类和数量越来越多，为了更好地解决 IO 设备和主机之间连接的灵活性，计算机的结构从分散连接发展为总线连接。为了进一步简化设计，又提出了各类总线标准。

### 总线基本概念

**<u>总线定义</u>**

一组能为多个部件**分时共享**的公共信息传送线路。

分时和共享是总线的两个特点：

+ **分时**：同一时刻只允许有一个部件向总线发送信息，若系统中有多个部件，则它们只能分时地向总线发送信息。

+ **共享**：总线上可以挂接多个部件，各个部件之间互相交换的信息都可通过这组线路分时共享。在某一时刻只允许有一个部件向总线发送信息，但多个部件可同时从总线上接收相同的信息。

**<u>总线设备</u>**

总线上所连接的设备，按其对总线有无控制功能可分为主设备和从设备两种：

+ **主设备**：获得总线控制权的设备。

+ **从设备**：被主设备访问的设备。只能响应从主设备发来的各种总线命令。

同一时刻只能有一个主设备控制总线的传输操作，可以有一个或多个从设备从总线接收数据。

**<u>总线特性</u>**

+ 机械特性：尺寸、形状、管脚数、排列顺序。

+ 电气特性：传输方向和有效的电平范围。

+ 功能特性：每根传输线的功能（地址、数据、控制）。

+ 时间特性：信号和时序的关系。

**<u>猝发传输</u>**

在一个总线周期内传输存储地址连续的多个数据字的总线传输方式。

主设备只需发送一次地址，就能在从设备上进行以该地址为始的连续数据字的传输。

**<u>引入总线结构的好处</u>**

1. 简化系统结构，便于系统设计制造。
2. 大大减少了连线数目，便于布线，减小体积，提高系统的可靠性。
3. 便于接口设计，所有与总线连接的设备均采用类似的接口。
4. 便于系统的扩充、更新与灵活配置，易于实现系统的模块化。
5. 便于设备的软件设计，所有接口的软件对不同的接口地址进行操作。
6. 便于故障诊断和维修，同时也能降低成本。

计算机使用总线结构便于增减外设，同时减少信息传输线的条数。但相对于专线结构，其实际上也降低了信息传输的并行性及信息的传输速度。

### 总线分类

#### 按数据传输格式

**<u>串行总线</u>**

只有一条双向传输或两条单向传输的数据线，数据按比特位串行顺序传输，通常采用差模信号。

适宜于远距离传送，可以从几米到数千千米。

总线工作频率可以很高（RS-232C 没有采用差模信号，所以它即使是串行但还是慢）。

通常采用异步定时方式。

优点：成本低廉，广泛应用于长距离运输；应用于计算机内部时，可以节省布线空间。

缺点：数据在发送和接收时要进行拆卸和装配，要考虑串并行转换的问题。

现在的串行总线通常基于包传输，如 80bit 为一个数据包，包与包之间有先后关系，因此可以用多个数据通路分别串行传输多个数据包。某种程度上现在的串行总线也有 “并行” 的特点。

> :mortar_board:<u>差分传输与差模信号</u>
>
> 差分传输是一种信号传输的技术，区别于传统的一根信号线一根地线的做法，差分传输在两根线上都传输信号，这两个信号的振幅相等、相位相反。在这两根线上传输的信号就是差分信号。
>
> 差分信号又称差模信号，是相对共模信号而言的。一个差分信号作用在两个导体上，信号值是两个导体间的电压差。
>
> 从严格意义上来讲，所有电压信号都是差分的，因为一个电压只能是相对于另一个电压而言的。简而言之，共模关注的是信号线与地线间的关系而差模关注的是信号线间的关系。
>
> 抗干扰能力强：干扰噪声一般会等值、同时的被加载到两根信号线上，而其差值为 0，即噪声对信号的逻辑意义不产生影响。
>
> 差分信号一定要走两根等长、等宽、紧密靠近、且在同一层面的线。

**<u>并行总线</u>**

用 $m$ 条数据线每次传送 $m$ 个比特，用高/低电平表示 1/0。

适宜于近距离的数据传输，通常小于 30m。

由于线间信号干扰，因此总线工作频率不能太高。

通常采用同步定时方式。

各条线不能有长度差，长距离并行传输时工艺难度大。

优点：总线的逻辑时序比较简单，电路实现起来比较容易；效率比串行总线更高。

缺点：信号线数量多，占用更多的布线空间；远距离传输成本高昂；由于工作频率较高时，并行的信号线之间会产生严重干扰，对每条线等长的要求也越高，所以无法持续提升工作频率；各条数据线的传输特点可能存在一些差异，比如有的信息位可能会延迟。

:warning:并行总线并不一定比串行总线快

虽然在工作频率相同时，串行总线传输速度比并行总线慢，但并行总线的工作频率无法持续提高：并行总线由于是多个数据位同时传输，需要考虑数据的协同性，以及线路之间的相互干扰。而串行总线可以通过不断提高工作频率来提高传输速度，使其速度最终超过并行总线的速度。

#### 按总线功能

**<u>片内总线</u>**

芯片内部的总线，用于 CPU 芯片内部寄存器与寄存器之间、寄存器与 ALU 之间的连接。

位数一般与机器字长相等。

**<u>系统总线</u>**

计算机系统内各功能部件（CPU、主存、I/O 接口）之间相互连接的总线。

按**传输信息内容**的不同，又可分为：

1. 数据总线（双向）

   用来在各部件之间传输数据信息，包括指令、操作数、中断类型号等。

   数据总线的位数（根数）即数据字长，等于 CPU 外部数据通路位数，与机器字长、存储字长有关，可以不等于 MDR 的位数。

   数据总线的位数反映一次能传送的数据的位数。

2. 地址总线（单向）

   用来指出数据总线上源数据或目的数据所在的主存单元或 I/O 端口的地址。

   地址总线的位数（根数）与主存地址空间及设备数量有关，和 MAR 位数相等。

   地址总线的位数反映主存地址空间的最大可寻址范围。

3. 控制总线（双向）

   用来传输各种命令、反馈和定时信号。

   典型的控制信号包括时钟（用于总线同步）、复位（初始化设备）、总线请求/允许、中断请求/回答、存储器读/写、I/O 读/写、传输确认等。
   
   > 有时候控制总线上传输的信号可统称为控制信号，有时候又分为控制信号、状态信号、响应信号等，看题目的意思。细分后的各个信号是单向传输的（总体上控制总线还是双向传输的），需要注意。

:punch:数据总线 vs 数据通路

各个功能部件通过**数据总线**连接形成的数据传输路径称为数据通路（CPU 外部数据通路）。

数据通路表示的是数据流经的路径，而数据总线是承载的媒介。

**<u>I/O 总线</u>**

主要用于连接中低速的 I/O 设备，通过 I/O 接口与系统总线相连接。

目的是将低速设备和高速总线分离，以提升总线的系统性能。

常见的有 USB 总线、PCI 总线。

**<u>通信总线/外部总线</u>**

用于计算机系统之间或计算机系统与其他系统（如远程通信设备、测试设备）之间信息传送的总线。

USB 总线也属于通信总线。

> CPU 和主存通过 I/O 总线和 I/O 接口连接，I/O 接口通过通信总线和外设连接，即：
> CPU 和主存 — I/O 总线 — I/O 接口 — 通信总线（电缆）— 外设

#### 按时序控制方式

**<u>同步总线</u>**

总线上连接的部件或设备通过统一的时钟进行同步，在规定的时钟节拍内进行规定的总线操作，来完成部件或设备之间的信息传输。

**<u>异步总线</u>**

总线上连接的部件或设备没有统一的时钟，而以信号握手的方式来协调各部件或设备之间的信息传输，总线操作时序不是固定的。

### 系统总线的结构

#### 单总线结构

CPU、主存、I/O 设备（通过 I/O 接口）都连接在**一组**系统总线上（单总线并不是指只有一根信号线），允许 I/O 设备之间、I/O 设备和 CPU 之间、CPU 和主存之间或 I/O 设备与主存之间直接交换信息，而无须经过中间设备的干预。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241025160123959.png" width="430px"/></dev>

优点：结构简单，成本低，易于接入新的设备。

缺点：带宽低、负载重，多个部件只能争用唯一的总线，且不支持并发传送操作。

#### 双总线结构

**<u>存储总线—I/O 总线</u>**（以 CPU 为中心）

会影响 CPU 的工作效率。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241025213020255.png" width="450px"/></dev>

<u>**系统总线—存储总线**</u>（以存储器为中心）

在单总线基础上开辟出的一条 CPU 与主存之间的总线。这组总线速度高，只供主存与 CPU之间传输信息。这样既提高了传输效率，又减轻了系统总线的负担，还保留了 I/O 设备与存储器交换信息时不经过 CPU 的特点。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241025212424781.png" width="500px"/></dev>

**<u>存储总线—I/O 总线</u>**（带通道）

1. 主存总线：用于 CPU、主存和通道之间进行数据传送。
2. I/O 总线：用于多个外部设备与通道之间进行数据传送。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241025212316189.png" width="380px"/></dev>


优点：将低速 I/O 设备从原单总线上分离出来，实现存储器总线和 I/O 总线分离；支持猝发传输。

缺点：需要增加通道等硬件设备。


#### 三总线结构


在计算机系统各部件之间采用 3 条各自独立的总线来构成信息通路：

1. 主存总线：用于在 CPU 和内存之间传送地址、数据和控制信息。

2. I/O 总线：用于在 CPU 和各类外设之间通信。

3. 直接内存访问 DMA 总线：用于在内存和高速外设之间（通过 DMA 接口）直接传送数据。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20231114144623266.png" width="400px"/></dev>

优点：提高了 I/O 设备的性能，使其更快地响应命令，提高系统吞吐量。

缺点：系统工作效率较低，**同一时刻只有一个总线工作**:warning:。主存总线与 DMA 总线不能同时对主存进行存取，I/O 总线也只有在 CPU 执行 I/O 指令时才能用到，而只有主存空闲（即主存总线和 DMA 总线都空闲）时 CPU 才会执行 I/O 指令。

#### 四总线结构

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241025165833449.png" width="1100px"/></dev>

**桥接器**：各总线之间须通过桥接器相连（如上图的北桥芯片、南桥芯片、IOH 芯片），其具有流量交换、数据缓冲、串并行转换和控制功能。

越靠近 CPU 的总线速度越快。

每级总线的设计遵循总线标准。

### 常见的总线标准*

总线标准是国际上公布或推荐的互连各个模块的标准，是把各种不同的模块组成计算机系统时必须遵守的规范。按总线标准设计的接口可视为通用接口，在接口的两端，任何一方只需根据总线标准的要求完成自身方面的功能要求，而无须了解对方接口的要求。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/1DoJuSP8iXecUCu.png" width="600px"/></dev>

不同的总线标准之间的主要区别是总线宽度、带宽、时钟频率、寻址能力、是否支持突发传送等。

注意区分协议、总线、接口。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241024211506238.png" width="600px"/></dev>

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241024211830934.png" width="800px"/></dev>

#### 系统总线

通常与 CPU 直接相连，用于连接 CPU 与北桥芯片或 CPU 与主存等。

**<u>ISA (Industry Standard Architecture, 工业标准体系结构)</u>**（**并行**）

最早出现的微型计算机的系统总线。

缺点是传输速率较低、CPU 占用率高、占用硬件中断资源。

应用在 IBM 的 AT 机上。

> IBM PC AT，AT 为 Advanced Technology 缩写，这是由于它引入了标准的 16 位 ISA 总线以及采用了当时最新的英特尔 80286 处理器。由于软件兼容性的原因，至今最新的 PC 系统都还支持 PC/AT 机的总线结构。

**<u>EISA (Extended Industry Standard Architecture, 扩展的 ISA)</u>**（**并行**）

为配合 32 位 CPU 而设计的扩展总线，对 ISA 完全兼容。

支持多个总线主控器和突发传送。

**<u>FSB (Front Side Bus, 前端总线)</u>**（**串行**）

用于连接 CPU 与北桥芯片。

对于多 CPU 芯片的所处理器系统，则多个 CPU 芯片通过一个 FSB 进行互连，也即多个处理器共享一个 FSB。

**<u>QPI (Quick Path Interconnect, 快速通道互联)</u>**（**串行**）

Intel 推出 Core i7 时，北桥芯片的功能被集成到了 CPU 芯片内，FSB 也随之不再使用，CPU 通过存储器总线（即内存条插槽）直接和内存条相连，而在 CPU 芯片内部的核与核之间、CPU 芯片与其他 CPU 芯片之间，以及  CPU 芯片与 IOH (Input/Output Hub) 芯片之间，则通过 QPI 总线相连。

尽管多数时候被称作 “总线”，但是 QPI 是一种点对点互联结构。

#### 局部总线

没有直接与 CPU 连接，通常用于高速的北桥芯片与很多重要的硬件部件（如显卡、网卡、声卡等）的连接。

高速设备采用局部总线连接，可以节省系统的总带宽。

**<u>VESA (Video Electronics Standards Association, 视频电子标准协会)</u>**（**并行**）

32 位的局部总线，是针对多媒体 PC 要求高速传送活动图像的大量数据而推出的。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3565_1.png" width="350px"/></dev>

**<u>PCI (Peripheral Component Interconnect, 外部设备互连)</u>**（**并行**）

高性能的 32 位或 64 位总线，专为高度集成的外围部件、扩充插板和处理器/存储器系统设计的互连机制。

不依附于某个具体的处理器，是与处理器时钟频率无关的高速外围总线，支持即插即用，支持突发传送。

早期也用来作为系统总线。

目前常用的 PCI 适配器有显卡、声卡、网卡等。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3567_1.png" width="150px"/></dev>

**<u>AGP (Accelerated Graphics Port, 加速图形接口)</u>**（**并行**）

视频接口标准，基于 PCI 2.1 版规范并进行扩充修改而成。

专用于连接主存和图形存储器，用于传输视频和三维图形数据。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3569_1.png" width="250px"/></dev>

**<u>PCI-E (PCI-Express)</u>**（**串行**）

通常称为 PCIe，点对点串行局部总线，支持双向传输模式，可运行全双工模式，支持热插拔。

其传输速率远高于 PCI 和 AGP，是最新的局部总线接口标准，将全面取代 PCI 和 AGP。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/Types-of-PCIe-Slots-1-1.jpg" width="400px"/></dev>

PCIe 的连接是建立在一个单向的序列的（1-bit）点对点连接基础之上，这称之为通道(lane)。两个 PCIe 设备之间以一个链路相连，每个链路可包含多条通道，可能的通道数为 1、2、4、8、16 或 32，PCIe $×n$ 表示具有 $n$ 个通路的 PCIe 链路。 

每条通道由发送和接收数据线构成，在发送和接收两个方向上都各有两根差分信号线，可同时发送和接收数据，即全双工。

在发送和接收过程中，每个数据字节实际上被转换成 10 位信息传输，以保证所有位都含有信号电平的跳变。这是因为在链路上没有专门的时钟信号（PCI-Express 5.0 及之前版本都采用 NRZ 编码），接收器使用锁相环 PLL 从进入的位流 0-1 和 1-0 跳变中恢复时钟。

PCI-Express 1.0 规范支持通路中每个方向的发送或者接收速率为 2.5Gb/s（也即 2.5 GT/s），8b/10b 编码。因此，PCI-Express 1.0 总线的总带宽（双向带宽）计算公式（单位为 GB/s）为：2.5Gb/s × 2 × 通路数 /10(b/B)。根据公式可知，在 PCI-Express 1.0 规范下，PCI-Express ×1 的总带宽为 0.5GB/s，PCI-Express ×2 的总带宽为 1GB/s，PCI-Express ×16 的总带宽为 8GB/s。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/_1585046553_TZOmBePO8Z.jpg" width="600px"/></dev>

PCIe 卡可以安装到一个更宽的插槽。比如在 PCIe x8 插槽已被占用的情况下，可以将 PCIe x8 卡放入 PCIe x16 插槽中，但该卡将始终以 PCIe x8 模式运行。

#### 设备总线

:hamburger:用于设备和设备控制器之间互连的接口标准。

**<u>USB (Universal Serial Bus, 通用串行总线)</u>**（**串行**）

① 即插即用；② 热插拔；③ 连接能力很强（菊花链）；④ 有很好的扩充性，可使用 USB 集线器链式连接 127 个外设；⑤ 高速传输，目前流行的 USB 3.2 数据传输速率可达 20Gbps。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3581_1.png" width="700px"/></dev>

差模信号：根据 2、3 的压差来确定 **1bit** 数据，差模信号的抗干扰能力很强，因此工作频率可以很高。

注意：**USB 每次只能传输 1bit 数据**。

USB 也属于通信总线。

**<u>PCMCIA (Personal Computer Memory Card International Association)</u>**（**并行**）

广泛应用于笔记本电脑的一种接口标准，是一个用于扩展功能的小型插槽，即插即用。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3579_1.png" width="300px"/></dev>

**<u>IDE (Integrated Drive Electronics, 集成设备电路)</u>**（**并行**）

更准确地称为 ATA (Advanced Technology Attachment)，是一种 IDE 接口磁盘驱动器接口类型，硬盘和光驱通过 IDE 接口与主板连接。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3583_1.png" width="250px"/></dev>

**<u>SCSI (Small Computer System Interface, 小型计算机系统接口)</u>**（**并行**）

用于计算机和智能设备之间（硬盘、软驱、光驱、打印机、扫描仪等）系统级接口的独立处理器标准。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3577_1.png" width="200px"/></dev>

**<u>SATA (Serial Advanced Technology Attachment, 串行高级技术附件)</u>**（**串行**）

串行 ATA，负责主板和大容量存储设备（如硬盘及光盘驱动器）之间的数据传输。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3585_1.png" width="500px"/></dev>

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241024211654141.png" width="700px"/></dev>

#### 通信总线

通常由南桥芯片控制。USB 总线也属于通信总线。

**<u>RS-232C</u>**（**串行**）

应用于串行**二进制**交换的数据终端设备(DTE)和数据通信设备(DCE)之间的标准接口。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3575_1.png" width="200px"/></dev>

### 总线的性能指标

**<u>总线时钟周期</u>**

即机器的时钟周期。

计算机有一个统一的时钟，以控制整个计算机的各个部件，总线也要受此时钟的控制。

现在的计算机中，总线时钟周期也有可能由桥接器提供。

**<u>总线传输周期（总线周期）</u>**

一次总线操作所需的时间。

包括申请阶段、寻址阶段、传输阶段和结束阶段。

通常一个总线周期包含多个总线时钟周期，不过有时也会一个总线周期包含一个总线时钟周期、一个总线时钟周期包含多个总线周期。

> 从大小上说，一般存取周期 > 总线周期 > 存取时间，这就使得 CPU 不能连续地存取数据，只能等待。所以说人们一直在寻找减少存取周期的方法，制造商工艺水平提高是一方面，各种设计思路也是一方面，例如若是把多体低位交叉存储器看成一个整体存储器，那么可以达到存取周期 = 总线周期，这样就达到了完美状态。

**<u>总线时钟频率</u>**

即机器的时钟频率，为时钟周期的倒数。

**<u>总线工作频率（总线频率）</u>**

总线上各种操作的频率，为总线周期的倒数。

实际上指 1s 内传送几次数据。若总线周期 = N 个时钟周期，则总线的工作频率 = 时钟频率 / N。

此外，若一个时钟周期可以传送 K 次数据，则总线工作频率是总线时钟频率的 K 倍。

**<u>总线宽度/总线位宽</u>**

总线上同时能够传输的数据位数。

通常指数据总线的根数，如 32 根称为 32 位总线。

**<u>总线带宽</u>**

单位时间内总线上最多可传输数据的位数，即总线的最大数据传输率。

通常用每秒传送信息的字节数来衡量（B/s）。

总线带宽 = 总线频率 × 总线宽度。

> 大部分题计算带宽时有把校验位算进去，但 20 年有道真题没有把校验位算进去；到底算不算校验位，还是根据题目再决定。

**<u>总线复用</u>**

一种信号线在不同的时间传输不同的信息。

例如，有些总线没有单独的地址线，地址信息通过数据线来传送，这种情况称为地址/数据线复用。

可以使用较少的线传输更多的信息，从而节省了空间和成本。

**<u>信号线数</u>**

地址总线、数据总线和控制总线 3 种总线数的总和。

## 总线事务和定时

### 总线事务

**<u>总线事务</u>**

从请求总线到完成总线使用的操作序列称为总线事务，它是在一个总线周期中发生的一系列活动。

典型的总线事务包括请求操作、仲裁操作、地址传输、数据传输、总线释放。

1. 请求阶段

   主设备（CPU 或 DMA）发出总线传输请求，并且获得总线控制权。

2. 仲裁阶段

   总线仲裁机构决定将下一个传输周期的总线使用权授予某个申请者。

3. 寻址阶段

   主设备通过总线给出要访问的从设备地址及有关命令，启动从模块。

4. 传输阶段

   主设备和从模块进行数据交换（单向或双向）。

5. 释放阶段

   主模块的有关信息均从系统总线上撤除，让出总线使用权。

**<u>总线数据传送方式</u>**

+ 非突发传送方式

  每个传送周期内都先传送地址，再传送数据，主、从设备之间通常每次只能传输一个字长的数据。

+ 突发/猝发传送方式

  能够进行连续成组数据的传送。

  其寻址阶段发送的是连续数据单元的首地址，在传输阶段传送多个连续单元的数据，每个时钟周期可以传送一个字长的信息，但是不释放总线，直到一组数据全部传送完毕后，再释放总线。

### 总线定时

总线在双方通信（交换数据）的过程中需要时间上配合关系的控制，这种控制称为总线定时。

实质是一种协议或规则，主要有同步、异步、半同步、分离式四种定时方式。

#### 同步定时方式

系统采用一个统一的时钟信号来协调发送和接收双方的传送定时关系。

在一个总线周期中，发送方和接收方可以进行一次数据传送

因为采用统一的时钟，每个部件或设备发送或接收信息都在固定的总线传送周期中。一个总线的传送周期结束，下一个总线的传送周期开始。

同步控制既可用于 CPU 控制，又可用于高速的外部设备控制。

------

读命令（假设 CPU 作为主设备，某个输入设备作为从设备）：

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3553_1.png" width="500px"/></dev>

+ CPU 在 T1 时刻的上升沿给出地址信息。
+ CPU 在 T2 的上升沿给出读命令（低电平有效），与地址信息相符合的输入设备按命令进行一系列的内部操作，且必须在 T3 的上升沿来之前将 CPU 所需的数据送到数据总线上。
+ CPU 在 T3 内将数据线上的信息传送到其内部寄存器中。
+ CPU 在 T4 上升沿撤销读命令，输入设备不再向数据总线上传送数据，撤销它对数据总线的驱动。

发送方用系统时钟前沿发信号，接收方用系统时钟后沿判断、识别。

------

优点：**传送速度快**，具有较高的传输速率；总线控制逻辑简单。

缺点：主从设备属于强制性同步；不能及时进行数据通信的有效性检验，可靠性较差。

适用：**总线长度较短**及总线所接**部件的存取时间比较接近**的系统（要节奏差不多，不会谁等谁太久）

**<u>同步串行通信方式</u>**

同步串行通信方式是发送方时钟直接控制接收方时钟，使双方完全同步的一种逐位传输的通信方式。

使用同步串行通信时，由于收发双方的时钟严格一致，因此仅在数据块的头尾处添加了开始和结束标记:warning:。

传输速率较高，但实现的硬件设备也更复杂，所以较少采用。

#### 异步定时方式

没有统一的时钟，也没有固定的时间间隔，完全依靠传送双方相互制约的 “握手” 信号来实现定时控制，传送操作由双方按需分配时间。

通常，主设备提出交换信息的 “请求” 信号，经接口传送到从设备；从设备接到主设备的请求后，通过接口向主设备发出 “回答” 信号。

优点：总线周期长度可变，能保证两个工作速度相差很大的部件或设备之间可靠地进行信息交换，自动适应时间的配合。

缺点：比同步控制方式稍复杂一些，速度比同步定时方式慢。

根据 “请求” 和 “回答” 信号的撤销是否互锁，异步定时方式又分为以下 3 种类型：

1. 不互锁方式（速度最快，可靠性最差）

   <div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3555_1.png" width="200px"/></dev>

   主设备发出 “请求” 信号后，不必等到接到从设备的 “回答” 信号，而是经在过一段时间自动撤销 “请求” 信号。

   从设备在接到 “请求” 信号后，发出 “回答” 信号，并经过一段时间后自动撤销 “回答” 信号，不存在互锁关系。

2. 半互锁方式

   <div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3557_1.png" width="200px"/></dev>

   主设备发出 “请求” 信号后，必须在接到从设备的 “回答” 信号后，才撤销 “请求” 信号，有互锁的关系。

   从设备在接到 “请求” 信号后，发出 “回答” 信号，但不必等待获知主设备的 “请求” 信号已经撤销，而是隔一段时间后自动撤销 “回答” 信号，不存在互锁关系。

3. 全互锁方式（最可靠，速度最慢）

   <div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3559_1.png" width="200px"/></dev>

   主设备发出 “请求” 信号后，必须在从设备 “回答” 后才撤销 “请求” 信号。

   从设备发出 “回答” 信号后，必须在获知主设备 “请求” 信号已撤销后，再撤销其 “回答” 信号，双方存在互锁关系。

<u>**同步通信比异步通信具有较高的传输速率的原因**</u>

+ 同步通信不需要应答信号且总线长度较短。

+ 同步通信用一个公共的时钟信号进行同步。

+ 同步通信中，各部件的存取时间较接近。

**<u>异步串行通信方式</u>**

使用异步串行通信时，由于收发双方时钟不严格一致，因此每个字符都要用开始位和停止位作为字符开始和结束的标志:warning:，从而保证数据传输的准确性。

异步串行通信的第一位是开始位，表示字符传送的开始。当通信线上没有数据传送时处于逻辑 “1” 状态，当发送方要发送一个字符时，首先发出一个逻辑 “0” 信号，即开始位。接收方检测到这个逻辑低电平后，就开始准备接收数据位。在字符传送过程中，数据位从最低位开始，一位一位地传输。当字符发送完后，就可以发送奇偶校验位（可选），以用于有限的差错检测。在奇偶位或数据位之后发送的是停止位，表示一个字符数据的结束。

现在越来越多的总线采用异步串行通信方式。

#### 半同步定时方式

这类总线既保留了同步通信的特点，又能采用异步应答方式连接速度相差较大的设备（既采用时钟信号，又采用握手信号）。

半同步定时方式保留了同步定时的特点，如所有地址、命令、数据信号的发出时间都严格参照系统时钟的某个前沿开始，而接收方都采用系统时钟后沿时刻来进行判断识别；同时，又像异步定时那样，允许不同速度的设备和谐地工作。为此增设一条 Wait 响应信号线。例如，某个半同步总线总是从某个时钟开始，在每个时钟到来时，采样 Wait 信号，若无效，则说明数据未准备好，下个时钟到来时，再采样 Wait 信号，直到检测到有效，再去数据线上取数据。

半同步定时适用于系统工作速度不高，但又包含了由许多速度差异较大的各类设备组成的简单系统。

通过在异步总线中引入时钟信号，其就绪和应答等信号都在时钟的上升沿或下降沿有效，而不受其他时间的信号干扰，即握手信号的采样仍由同步时钟控制。

优点：控制方式比异步定时简单，各模块在系统时钟的控制下同步工作，可靠性较高。

缺点：系统时钟频率不能要求太高，所以从整体上来看，系统工作的速度不是很高。

读命令示例：

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/3561_1.png" width="500px"/></dev>

PCI 总线就是一种半同步总线，它的所有时间都在时钟下降沿同步，总线设备在时钟开始的上升沿采样总线信号。

以上三种定时方式都从主设备发出地址和读/写命令开始，直到数据传输结束，在整个传输周期中，总线的使用权完全由主设备及由其选中的从设备占据。其实，从设备在准备数据的阶段，总线纯属空闲等待，为进一步挖掘总线的潜力，又提出了分离式定时方式。


#### 分离式定时方式

分离式定时方式将一个总线事务分解为请求和应答两个子过程：

1. 主设备 A 申请占用总线，获得总线使用权后，将命令、地址等信息发到总线上，经总线传输后由从设备 B 接收。

   此过程占用总线的时间很短，主设备一旦发送完，立即释放总线，以便其他设备使用。

2. 设备 B 收到设备 A 发来的有关命令后，将设备 A 所需的数据准备好后，便由设备 B 申请总线使用权，一旦获准，设备 B 便将相应的数据送到总线上，由设备 A 接收。

上述两个子过程都只有单方向的信息流，每个设备都变为主设备。

特点：

1. 各设备均有权申请占用总线。
2. 采用同步方式通信，不等对方回答。
3. 各设备准备数据时，不占用总线。
4. **总线利用率提高**，充分挖掘系统总线每瞬间的潜力。

优点：在不传送数据时释放总线，使总线可接受其他设备的请求，不存在空闲等待时间。

缺点：控制负责，开销也大。
