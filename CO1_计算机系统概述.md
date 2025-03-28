## 计算机发展历程*

本节内容已从大纲删除

### 计算机硬件的发展
#### 计算机的四代变化

**<u>第一代计算机 —— 电子管时代（1946—1957）</u>**

逻辑元件：电子管。

主存：延迟线/磁鼓，容量极小。

编程语言：机器语言。

运算速度：较低，一般只有几千次到几万次每秒。

体积庞大，成本高。

**<u>第二代计算机 —— 晶体管时代（1958—1964）</u>**

逻辑元件：晶体管。

主存：磁芯存储器。

编程语言：开始出现高级语言，如 FORTRAN。

软件：有了操作系统的雏形。

运算速度：提升到几万次到几十万次每秒。

**<u>第三代计算机 —— 中小规模集成电路时代（1965—1971）</u>**

逻辑元件：中小规模集成电路。

存储器：半导体存储器开始取代磁芯存储器。

编程语言：高级语言发展迅速。

软件：操作系统进一步发展，开始有了分时操作系统。

**<u>第四代计算机 —— 超大规模集成电路时代（1972—至今）</u>**

逻辑元件：大规模集成电路和超大规模集成电路，产生了微处理器。

诸如并行、流水线、高速缓存和虚拟存储器等概念用在了这代计算机中。

> 1~4 代都采用冯·诺依曼体系结构（控制器、存储器、运算器、输入输出设备）。

**<u>第五代计算机 —— 智能计算机</u>**

具备人工智能。

运算速度极快。

软件系统能够处理知识信息。

神经网络计算机是智能计算机的重要代表。

**<u>第六代计算机 —— 生物计算机与量子计算机</u>**

未来计算机发展的方向和趋势。

#### 计算机元件的更新换代

**<u>摩尔定律</u>**

当价格不变时，集成电路上可容纳的晶体管数约每 18 个月翻一番，性能也将提升一倍。

**<u>半导体存储器的发展</u>**

至今半导体存储器发展了 11 代：单芯片 1 KB → 4 KB → 16 KB → …… → 1 GB（4 倍增长）。

**<u>微处理器的发展</u>**

第一个微处理器 Intel 4004，经历 Intel 8008（8 位）、Intel 8086（16 位）、Intel 80386（32 位）、Pentium（32 位）、Pentium Ⅲ（64 位）、Pentium 4（64 位）、Core i7（64 位）等。

> 这里的位数指的是机器字长。

微型计算机的发展以微处理器的技术为标志。

**<u>系列机</u>**

具有基本相同的体系结构，使用相同基本指令系统的多个不同型号的计算机组成的一个产品系列。其基本特性是，指令系统向后兼容（指时间上向后兼容，即新机器兼容使用以前机器的指令系统）。

### 计算机软件的发展
计算机语言的发展经历了面向机器的机器语言和汇编语言、面向问题的高级语言。

高级语言的发展真正促进了软件的发展，它经历了从科学计算和工程计算的 FORTRAN、结构化程序设计的 PASCAL 到面向对象的 C++ 和适应网络环境的 Java。

直接影响计算机系统性能提升的各种系统软件也有了长足的发展，特别是操作系统，如 Windows、UNIX、Linux 等。

### 计算机的分类与发展方向

<u>**按能够处理信号分类**</u>
1. 数字计算机

   只能处理离散信号。

   其按用途又可分为：专用计算机、通用计算机。

   通用计算机又可分为巨型机、大型机、中型机、小型机、微型机和单片机 6 类。它们的体积、功耗、性能、数据存储量、指令系统的复杂程度和价格依次递减。

2. 电子模拟计算机

   处理连续信号。

<u>**按指令和数据流分类**</u>
1. 单指令流和单数据流系统 SISD

   即冯·诺伊曼体系结构。

2. 单指令流和多数据流系统 SIMD

   包括阵列处理器和向量处理器系统。

3. 多指令流和单数据流系统 MISD

   不存在。

4. 多指令流和多数据流系统 MIMD

   包括多处理器和多计算机系统。

<u>**计算机的发展趋势 —— 向 “两极” 分化**</u>

微型机向更微型化、网格化、高性能、多用途方向发展。

巨型机向更巨型化、超高速、并行处理、智能化方向发展。

## 计算机系统层次结构

### 计算机系统的组成

计算机系统 = 硬件系统 + 软件系统

**<u>硬件与软件</u>**

+ 计算机系统性能的好坏，很大程度上是由软件的效率和作用来表征的，而软件性能的发挥又离不开硬件的支持。
+ 硬件实现实现具有更高的执行速度，软件实现具有更好的灵活性。
+ 硬件能执行的只能是机器语言（二进制编码）。
+ 执行频繁、硬件实现代价不是很大的功能通常由硬件实现，可以提高效率。
+ 对某一功能来说，若其既可以用软件实现，又可以用硬件实现，则称为软/硬件在**逻辑**功能上是等价的。

软件和硬件的分界面是系统结构设计者的任务。

> 貌似所有功能既可由软件实现也可由硬件实现。至少软件能实现的功能也能由硬件实现（来源：王道操作系统 P33 选择 17 解析）。

**<u>固件</u>**

固件指将程序固定在 ROM 中组成的部件，是软硬件结合的产物，性能指标介于硬件和软件之间。

执行速度快于软件，灵活性优于硬件，算是吸取了软硬件各自的优点。

目前操作系统已实现了部分固化（把软件永恒地存储于只读存储器中）。

**<u>计算机体系结构 vs 计算机组成</u>**

计算机体系结构是指机器语言或汇编语言程序员所看得到的传统机器的属性，包括指令集、数据类型、存储器寻址技术等，大都属于抽象的属性。

计算机组成是指如何实现计算机体系结构所体现的属性，它包含对许多程序员来说透明的硬件细节。

例如，指令系统属于结构的问题，但指令的实现即如何取指令、分析指令、取操作数、如何运算等都属于组成的问题。

> :raising_hand:联想
>
> 计算机网络的体系结构是指计算机网络的各层及其协议的集合。换言之，计算机网络的体系结构就是这个计算机网络及其所应完成的功能的精确定义。这些功能究竟是用硬件或软件完成的，是一个遵循这种体系结构的实现问题。
>
> 体系结构是抽象的。

### 计算机硬件

#### 冯·诺依曼机
**<u>“存储程序” 的思想</u>**

将事先编制好的程序和原始数据送入主存后才能执行，一旦程序被启动执行，就无须操作人员的干预，计算机会自动逐条执行指令，直至程序执行结束。

“存储程序” 的思想奠定了现代计算机的基本结构，目前绝大多数现代计算机仍遵循冯·诺伊曼的 “存储程序” 思想。

**<u>冯·诺依曼机</u>**

以 “存储程序” 思想为基础的各类计算机统称为冯·诺依曼机。

**<u>冯·诺伊曼机的特点</u>**

1. 工作方式：“存储程序”

   基本工作方式：控制流驱动

2. 计算机硬件系统五大部件：运算器、控制器、存储器、输入设备、输出设备。

   硬件系统五大部件也可以划分为两大部分：控制部件、执行部件。控制部件是控制器，而运算器、存储器和外围设备相对控制器而言都是执行部件。

3. 指令和数据以同等地位存储在存储器中，并可按地址寻访。

   指令和数据形式上没有区别，但计算机应能区分它们（CPU 区分数据和指令的依据：指令周期的不同阶段）。

4. 指令和数据均用二进制代码表示。

5. 指令由操作码和地址码组成。操作码指出操作的类型，地址码指出操作数的地址。

6. 指令在存储器内按顺序存放。

   通常指令是顺序执行的，当然在特定条件下也可根据运算结果或设定的条件改变执行顺序。

7. 以**运算器**为中心，输入/输出设备通过运算器与存储器传送数据（现代计算机以存储器为中心）。

>  冯·诺依曼结构计算机中数据采用二进制编码表示的主要原因：
>
> 1）二进制运算规则简单。
>
> 2）制造两个稳态的物理器件较容易。
>
> 3）便于用逻辑门电路实现算术运算。

**<u>典型的冯·诺依曼计算机结构</u>**

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20221128195847080.png" width="520px"/></dev>

#### 现代计算机组织结构

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20221128200439507.png" width="520px"/></dev>

以**存储器**为中心，使 I/O 操作尽可能绕过 CPU，直接在 I/O 设备和存储器之间完成，以提高系统的整体运行效率。

#### 计算机的功能部件
传统冯·诺依曼计算机与现代计算机的结构虽然有所不同，但功能部件是一致的。

**<u>输入设备</u>**

主要功能：将程序和数据以机器所能识别和接受的信息形式输入计算机。

常见输入设备：键盘、鼠标、扫描仪、摄像机等。

**<u>输出设备</u>**

主要功能：将计算机处理的结果以人们所能接受的形式或其他系统所要求的信息形式输出。

常见输出设备：显示器、打印机等。

**<u>存储器</u>**

计算机的存储部件，用来存放程序和数据。

+ 主存储器/主存/内存储器/内存

  <div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/onzxpD8Td2UpMjp.png" width="350px"/></dev>

  CPU 能够直接访问，也可以和高速缓冲存储器 Cache 及辅助存储器交换数据。

  工作方式：按存储单元的地址进行存取，称为按地址存取方式。

  特点：容量较小、存取速度较快、每位价格较高。

  存储体由许多存储单元组成，每个存储单元包含若干存储元件，每个存储元件存储一位二进制。因此存储单元可存储一串二进制代码，称这串代码为**存储字**，存储字的位数为**存储字长**，存储字长可以是 1B 或是字节的偶数倍。

  <u>MAR</u>：用于寻址，存放访存地址，经过地址译码后找到所选的存储单元。其位数/长度反映**最多**可寻址的存储单元的个数（如 MAR 为 10 位，则最多有 $2^{10}$ 个存储单元）。MAR 的长度和 PC 的长度相等。

  <u>MDR</u>：用于暂存要从存储器中读或写的信息，其位数通常和存储字长相等，一般为字节的 2 次幂的整数倍。

  MAR 和 MDR 理论上属于主存，但现代计算机绝大多数集成于 CPU 中。

  <u>时序控制逻辑</u>：用于产生存储器操作所需的各种时序信号。

+ 辅助存储器/辅存/外存储器/外存

  帮助主存记忆更多的信息（主存的后援存储器），用来存放当前暂时不用的程序和数据，以及一些需要永久性保存的信息。

  特点：容量较大、存取速度较慢、每位价格较低。

  辅存中的信息必须调入主存后才能为 CPU 访问。

+ 相联存储器

  既可以按地址寻址，又可以按内容（通常是某些字段）寻址。

  为与传统存储器区别，又称按内容寻址的存储器。

  基本原理：把存储单元所存内容的某一部分作为检索项（即关键字项）去检索该存储器，并将存储器中与该检索项符合的存储单元内容进行读出或写入。

  价格较为昂贵，一般用来制作 TLB、相联 Cache 等。

> CPU 存取速度：寄存器 ＞ Cache ＞ 内存。

**<u>运算器</u>**

计算机的执行部件，用于进行算术运算（加、减、乘、除）和逻辑运算（与、或、非、异或、比较、移位等）。

核心：算术逻辑单元 ALU (Arithmetic and Logical Unit)。

包含若干通用寄存器，用于暂存操作数和中间结果，如：累加器 ACC、乘商寄存器 MQ、操作数寄存器 X、变址寄存器 IX、基址寄存器 BR 等（前 3 个必备）。

还有程序状态寄存器/标志寄存器 PSW，用于存放 ALU 运算得到的一些标志信息或处理机的状态信息，如结果是否溢出、有无产生进位或错位、结果是否为负等。

另外还有暂存寄存器、移位器、计数器等（详见中央处理器一章）。

**<u>控制器</u>**

计算机的指挥中心，由其 “指挥” 各部件自动协调地进行工作

主要由程序计数器 PC、指令寄存器 IR 和控制单元 CU 组成，可再细分为：PC + IR + MAR + MDR + ID + 时序系统 + 微操作信号发生器。

PC：存放当前欲执行指令的地址，可自动加 “1”（1 条指令长度）以形成下一条指令的地址，与主存的 MAR 之间有一条直接通路。

IR：存放当前指令，其内容来自 MDR。指令中的操作码 OP(IR) 送至 CU，用以分析指令并发出各种微操作指令序列；地址码 Ad(IR) 送往 MAR，用以取操作数。

------

一般运算器和控制器集成到同一个芯片上，称为中央处理器 CPU。

CPU 和主存共同构成主机，除主机外的其他硬件装置（外存、I/O 设备等）统称为外部设备，简称外设。

**<u>冯·诺依曼结构的模型机</u>**

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/RbFRwo27PWWMEek.png" width="600px"/></dev>

图中从控制器送出的虚线就是控制信号，它可以：控制如何修改 PC 以得到下一条指令的地址、控制 ALU 执行什么运算、控制主存是进行读操作还是写操作（读/写控制信号）。

CPU 和主存之间通过一组总线（地址、控制和数据 3 组信号线）相连。MAR 中的地址信息会直接送到地址线上，用于指向读/写操作的主存存储单元；控制线中有读/写信号线，指出数据是从 CPU 写入主存还是从主存读出到 CPU，根据是读操作还是写操作来控制是将 MDR 中的数据直接送到数据线上还是将数据线上的数据接收到 MDR 中。

### 计算机软件

#### 系统软件和应用软件

**<u>系统软件</u>**

一组保证计算机系统高效、正确运行的基础软件，通常作为系统资源提供给用户使用。

主要有：操作系统 OS、**数据库管理系统** DBMS、语言处理程序、分布式软件系统、网络软件系统、标准库程序、服务性程序等。

> 数据库 DB：长期存储在计算机内、有组织的、可共享的大量数据的集合。
>
> 数据库管理系统 DBMS：位于用户与操作系统之间的一层数据管理软件。
>
> 数据库系统 DBS：一般由数据库、数据库管理系统（及其开发工具）、数据库应用系统 DBAS 和数据库管理员 DBA 构成。

**<u>应用软件</u>**

指用户为解决某个应用领域中的各类问题而编制的程序。

如：各种科学计算类程序、工程设计类程序、数据统计与处理程序等。

------

在本学科范畴内，编写诸如操作系统、编译程序等各种系统软件的人员称为系统程序员；利用计算机及所支持的系统软件来编写解决具体应用问题的人员称为应用程序员。

#### 三个级别的语言

**<u>机器语言/二进制代码语言</u>**

计算机唯一可以直接识别和执行的语言。

**<u>汇编语言</u>**

用英文单词或其缩写代替二进制的指令代码。

在不同的设备中，汇编语言对应着不同的机器语言指令集。特定的汇编语言与特定的机器语言指令集是一一对应的:warning:，不同平台之间不可直接移植。

汇编语言和机器语言都与计算机系统结构相关。

机器语言和汇编语言统称为机器级语言。用机器指令表示的机器语言程序和用汇编指令表示的汇编语言程序统称为机器级程序，它是对应高级语言程序的机器级表示。任何一个高级语言程序一定存在一个与之对应的机器级程序，而且是不唯一的。因此，如何将高级语言程序生成对应的机器级程序并在时间和空间上达到最优，是编译优化要解决的问题。

**<u>高级语言</u>**

为方便程序设计人员写出解决问题的处理方案和解题过程的程序。

机器语言和汇编语言与机器指令对应，而高级语言不与指令直接对应，具有较好的可移植性。

**<u>翻译程序</u>**

+ 编译程序/编译器（高级 → 汇编/**机器**:warning:）

  GCC 可以直接产生机器语言代码，也可以先产生汇编语言代码，然后再通过汇编程序将汇编语言代码转换为机器语言代码。

+ 汇编程序/汇编器（汇编 → 机器）

+ 解释程序/解释器（高级 → 机器）

  将源程序中的语句按执行顺序逐条翻译成机器指令并立即执行（翻译一句执行一句，**不会生成目标程序**:warning:），一般（运行）速度较编译程序慢（但编译程序要需要先一次性完整编译并生成目标程序后再运行）。

> :seedling: Java 和 Python 都需要把代码编译成字节码，再由虚拟机解释运行，为什么 Python 算解释型语言而 Java 不算呢？
>
> 现在很多语言到底是解释型还是编译型都没分的那么开了，因为现在的语言编译器基本都是会先由前端生成 IR，再决定之后是翻译成 native，还是 JIT 执行，还是全部解释执行，都是可选的。要说由源代码生成为 IR，那基本所有语言都有这个过程，比如 Java 翻译成字节码就是，然后由 JVM 自己决定要怎么对待字节码，是全部解释？还是全部编译？还是用 JIT 边解释执行边编译部分热点以及进行运行时优化？
>
> 所以纠结解释型还是编译型这个属实没啥意思。

#### 软件和硬件的逻辑功能等价性

对某一功能来说，既可由硬件实现又可由软件实现，从用户的角度看，它们在功能上是等价的。这一等价性被称为软/硬件逻辑功能的等价性。

硬件实现的往往是最基本的算术和逻辑运算功能，而其他功能大多通过软件的扩充得以实现。

软件和硬件功能界面的划分是由设计目标、性能价格比、技术水平等综合因素决定的。

### 计算机系统的层次结构

> 关于计算机系统层次结构的分层方式，目前尚无统一的标准。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/kIgBcxjX0VL8ndv.png" width="700px"/></dev>


上层实现对下层的功能扩展，下层是实现上层的基础。

虚拟机器只对该层的观察者存在，对于某层的观察者来说，只能通过该层的语言来了解和使用计算机，而不必关心下层是如何工作的。

在高级语言层之上，还可以有应用程序层，它由解决实际问题的处理程序组成。

软/硬件交界面就是<u>指令集体系结构 ISA</u>，ISA 定义了一台计算机可以执行的所有指令的集合，每条指令规定了计算机执行什么操作，以及所处理的操作数存放的地址空间和操作数类型。ISA 是指软件能感知到的部分，也称软件可见部分。

软/硬件交界面的划分也不是绝对的：随着超大规模集成电路的不断发展，部分软件功能将由硬件实现。

> 本门课程主要讨论传统机器 M1 和微程序机器 M0 的组成原理和设计思想。

### 计算机系统的工作原理

#### “存储程序” 工作方式

“存储程序” 工作方式规定，程序执行前，需要将程序所含的指令和数据送入主存储器，一旦程序被启动执行，就无须操作人员的干预，自动逐条完成指令的取出和执行任务。

一个程序的执行就是周而复始地执行一条一条指令的过程。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20240803232852766.png" width="300px"/></dev>

#### 从源程序到可执行文件

通过程序编辑软件，得到 hello.c 文件。以下是 hello.c 的 C 语言源程序代码：

```c
#include <stdio.h>
int main()
{
    printf("hello, world\n");
}
```

hello.c 在计算机中以 ASCII 字符方式存放。通常把用 ASCII 码字符或汉字字符表示的文件称为文本文件(text fle)，源程序文件都是文本文件，是可显示和可读的。

将 hello.c 进行预处理、编译、汇编和链接，最终生成可执行目标文件。例如，在 UNIX 系统中，可用 GCC 编译驱动程序进行处理。

从 hello.c 到可执行文件 hello 的转化过程如下：

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20241124154512788.png" width="700px"/></dev>

1. 预处理阶段

   预处理器 cpp (C Preprocessor) 对源程序中各种预处理命令进行处理，包括对头文件的包含、宏定义的扩展、条件编译的选择等，例如，对 #include 指示的处理结果，就是将相应 .h 文件内容插入到源程序文件中。

   预处理程序的输出结果还是一个源程序文件（可显示的文本文件），以 .i 为扩展名。

2. 编译阶段

   编译器 ccl 对预处理后的源程序进行编译，生成一个汇编语言源程序文件。

   C 编译器在进行具体的程序翻译之前，会先对源程序进行词法分析、语法分析和语义分析，然后根据分析的结果进行代码优化和存储分配，最终把 C 语言源程序翻译成汇编语言程序。

   编译器通常采用对源程序进行多次扫描的方式进行处理，每次扫描集中完成一项或几项任务，也可以将一项任务分散到几次扫描去完成。例如，可以按照以下四趟扫描进行处理：第一趟扫描进行词法分析；第二趟扫描进行语法分析；第三趟扫描进行代码优化和存储分配；第四趟扫描生成代码。

   因为汇编语言与具体的机器结构有关，所以，对同一台机器来说，不管何种高级语言，编译转换后的输出结果都是同一种机器语言对应的汇编语言源程序。

   GCC 可以直接产生机器语言代码，也可以先产生汇编语言代码，然后再通过汇编程序将汇编语言代码转换为机器语言代码。

3. 汇编阶段

   汇编器 as 将汇编语言源程序翻译成机器语言指令，并把这些指令打包成一个称为可重定位目标文件的二进制文件。

   因为通常最终的可执行目标文件由多个不同模块对应的机器语言目标代码组合而形成，所以，在生成单个模块的机器语言目标代码时，不可能确定每条指令或每个数据最终的地址，也即，单个模块的机器语言目标代码需要重新定位，因此，通常把汇编生成的机器语言目标代码文件称为可重定位目标文件。

3. 链接阶段

   链接器 ld 将多个可重定位目标文件和标准库函数合并为一个可执行目标文件（简称可执行文件）。
   

最终生成的可执行文件被保存在磁盘上，可以通过某种方式启动一个磁盘上的可执行文件。

#### 可执行文件的启动和执行

对于一个存放在磁盘上的可执行文件，可以在操作系统提供的用户操作环境中，采用双击对应图标或在命令行中输入可执行文件名等多种方式来启动执行。

在 UNIX 系统中，可以通过 shell 命令行解释器来执行一个可执行文件。例如，对于上述可执行文件 hello，通过 shell 命令行解释器启动执行的结果如下：

```shell
unix> ./hello
hello, world

unix>
```
shell 命令行解释器会显示提示符 `unix>`，告知用户它准备接收用户的输入，此时，用户可以在提示符后面输入需要执行的命令名，它可以是一个可执行文件在磁盘上的路径名。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20230623104933155.png" width="700px"/></dev>

① shell 程序将用户从键盘输入的每个字符逐一读入 CPU 寄存器；

② 然后保存到主存中，在主存的缓冲区形成字符串 “./hello”；

③ 接收到 Enter 键时，shell 通过调用 execve 系统调用函数启动加载器(loader)，由加载器来加载磁盘上的可执行文件 hello 到主存中；

④ 内核加载完可执行文件中的代码和数据（这里是字符串 "hello, world\n"）后，将 hello 的第一条指令的地址送至 PC，CPU 随后开始执行 hello 程序，它将已加载到主存的字符串 "hello, world\n" 中的每个字符从主存取到 CPU 的寄存器中；

⑤ 将 CPU 寄存器中的字符送到显示器上显示出来。

从上述过程可以看出，一个用户程序被启动执行，必须依靠操作系统的支持，包括提供人机接口环境（如外壳程序）和内核服务例程。例如，shell 命令行解释器是操作系统外壳程序，它为用户提供了一个启动程序执行的环境，用来对用户从键盘输入的命令进行解释，并调出操作系统内核来加载用户程序（用户从键盘输入的命令所对应的程序）。显然，用来加载用户程序并使其从第一条指令开始执行的操作系统内核服务例程也是必不可少的。

此外，在上述过程中，涉及键盘、磁盘和显示器等外部设备的操作，这些底层硬件是不能由用户程序直接访问的。此时，也需要依靠操作系统内核服务例程的支持，例如，用户程序需要调用内核的 read 系统调用服务例程读取磁盘文件，或调用内核的 write 系统调用服务例程把字符串 “写” 到显示器等。

程序的执行过程就是数据在 CPU、主存储器和 I/O 模块之间流动的过程，所有数据的流动都是通过总线、I/O 桥接器等进行的。数据在总线上传输之前，需要先缓存在存储部件中，因此，除了主存本身是存储部件以外，在 CPU、 I/O 桥接器、设备控制器中也有存放数据的缓冲存储部件，例如，CPU 中的通用寄存器，设备控制器中的数据缓冲寄存器等。

#### 指令执行过程的描述

以取数指令（送至运算器的 ACC 中）为例：

1. 取指令：(PC) → MAR → M → MDR → IR

   根据 PC 取指令到 IR：将 PC 内容送 MAR，MAR 内容直接送地址线，同时 CU 将读信号送读/写信号线，主存根据地址线上的地址和读信号，从指定存储单元读出指令，送到数据线上，MDR 从数据线接收指令信息，并传送到 IR 中。

2. 分析指令：OP(IR) → CU/ID

   指令译码并送出控制信号：CU/ID 根据 IR 中指令的操作码，生成相应的控制信号，送到不同的执行部件。

   在本例中，IR 中是取数指令，因此读控制信号被送到总线的控制线上。

3. 执行指令：Ad(IR) → MAR → M → MDR → ACC

   取数操作：将 IR 中指令的地址码送 MAR，MAR 内容送地址线，同时控制线将读信号送读/写信号线，从主存读出操作数，并通过数据线送 MDR，再传送到 ACC 中。

每取完一条指令，(PC) + 1 → PC。

## 计算机性能指标

### 字和字长

**<u>字 word</u>**

“字” 用来表示被处理信息的单位，用来度量各种数据类型的宽度。

通常系统结构设计者必须考虑一台机器将提供哪些数据类型，每种数据类型提供哪几种宽度的数，这时就要给出一个基本的 “字” 的宽度。例如 x86 处理器中把一个字定义为 16 位，所提供的数据类型中，就有单字宽度的无符号整数和带符号整数（16 位）、双字宽度的无符号数和带符号数（32 位）等。

:warning:字的长/宽度 ≠ 字长。字长是机器字长的简称。“字” 和 “字长” 的长度可以一样，也可以不一样。例如在 Intel 微处理器中，从 80386 开始就至少都是 32 位机器了，即字长至少为 32 位，但其字的宽度都定义为 16 位，32 位称为双字。

**<u>机器字长</u>**

简称字长，指计算机进行一次整数运算（即定点整数运算）所能处理的二进制数据的位数（CPU 中定点运算的内部数据通路宽度）。

反映计算机处理信息的能力。

通常与 CPU 的寄存器位数、加法器有关，一般等于内部寄存器的大小，通常选定为字节的整数倍。

机器字长越长，数的表示范围越大、计算精度越高。

通常所说的 “某 16 位或 32 位机器”，其中的 16、32 指的就是机器字长。

机器字长会影响硬件的造价。

**<u>数据字长</u>**

数据总线一次能并行传送信息的位数（外部数据通路带宽），等于 MDR 的位数。

$n$ 位 CPU 有时也可指数据字长（王道 P208 选择 06），因为数据字长通常也等于运算器寄存器位数。

> 袁：数据线的宽度与 MDR 的宽度相同，地址线的宽度与 MAR 的宽度相同。

**<u>存储字长</u>**

一个存储单元中的二进制代码的位数。

数据线的位数通常等于存储字长，因此 MDR 的位数通常等于存储字长；若数据线的位数不等于存储字长，则 MDR 的位数由数据线的位数决定。

**<u>指令字长</u>**

一个指令字中包含的二进制代码的位数。

单字长指令：指令字长度等于**机器字长**:warning:的指令。类似的还有半字长指令、双字长指令。

一般取存储字长的整数倍。若指令字长等于存储字长的 2 倍，则需要 2 个访存周期来取出一条指令；若指令字长等于存储字长，则取指周期等于机器周期。

**<u>数据字长 vs 存储字长 vs 指令字长</u>**

早期计算机一般数据字长 = 存储字长 = 指令字长，故访问一次主存便可取一条指令或一个数据。

随着计算机应用范围的不断扩大，解题精度的不断提高，往往要求指令字长是可变的，数据字长也要求可变，为了适应指令和数据字长的可变性，其长度不由存储字长来确定，而由字节的个数来表示。此时，存储字长、数据字长、指令字长三者可各不相同，但它们必须是字节的整数倍。

指令字长取决于操作码的长度、操作数地址的长度和操作数地址的个数，与机器字长没有必然的联系，但为了硬件设计方便，指令字长一般取字节或存储字长的整数倍。

> 貌似只有 <u>①MDR 位数和数据字长相等</u> <u>②MAR 位数和主存储器地址线数相等</u> 是确定的。

**<u>按字寻址</u>**

“字” 一般指数据字长。需要结合具体题目来确定。

### 数据通路带宽

**外部**:warning:数据总线一次所能**并行**传送信息的位数。

外部数据总线宽度与 CPU 内部的数据总线宽度（内部寄存器的大小）有可能不同。

数据通路：各个子系统通过数据总线连接形成的数据传送路径。

### 主存容量

主存储器所能存储信息的最大容量

通常以字节来衡量，也可用字数 × 字长来表示（如 512K × 16 位）。其中，字数（存储单元个数）= $2^{MAR\ 位数}$，MAR 的位数反映可寻址范围的最大值；字长即存储字长。

### 运算速度

**<u>吞吐量</u>**

系统在单位时间内处理请求的数量。

主要取决于**主存的存取周期**。

优化数据通路可以有效提高吞吐量。

**<u>响应时间</u>**

从用户发出一个请求，到系统对该请求作出响应并获得所需结果的等待时间。

通常包括 CPU 执行时间（运行一个程序所花费时间）和等待时间（用于磁盘访问、存储器访问、I/O 操作、操作系统开销等时间）。

**<u>主频（CPU 时钟频率）</u>**

机器内部主时钟的频率（CPU 内数字脉冲信号振荡的速度），即时钟周期的倒数。

CPU 的一切操作都是在系统时钟的控制下按节拍有序进行的。

通常以 Hz 为单位，常见 CPU 主频有 1.8 GHz、2.4 GHz、2.8 GHz。

主频最直观的理解就是每秒有多少个时钟周期。

对于同一个型号的计算机，其主频越高，完成指令的一个执行步骤所用的时间越短，执行指令的速度越快。

为了节省功耗或临时提升性能，当今的处理器可以调整时钟频率。例如，Intel Core i7 处理器可以临时将时钟频率提高 10%，Intel 称之为涡轮增压模式(Turbo mode)。

主频并不是性能的体现，也不能直接代表运算速度，在一定情况下很可能会出现主频较高的 CPU 实际运算速度较低的现象。

<u>时钟脉冲信号</u>：由机器脉冲源发出的脉冲信号经整形和分频后形成。

**<u>CPU 时钟周期</u>**

机器内部主时钟脉冲信号的宽度，即主频的倒数。

CPU 中最小的基本时间计量单位，执行指令的每个动作至少需要一个时钟周期。

时钟周期以相邻状态单元间组合逻辑电路的最大延迟为基准确定，也以指令流水线的每个流水线的最大延迟时间确定。

**<u>CPI (Clock cycles Per Instruction)</u>**

执行一条指令所需的时钟周期数。

不同指令需要的时间可能不同。因此对于一个程序或一台机器来说，其 CPI 指该程序或该机器指令集中的全部指令执行所需的平均时钟周期数。

系统结构、指令集、计算机组织会影响 CPI。时钟频率不会影响 CPI，但可加快指令的执行速度。

理想情况下，单周期 CPU 和基本流水线 CPU 的 CPI 为 1。

<u>IPC (Instruction Per Clock cycle)</u>：每个时钟周期执行多少条指令。有些处理器在每个时钟周期是可以对多条指令取指并执行的，所以 CPI 可能小于 1，因而有些设计者反过来用 IPC 来代替 CPI（但不意味着指令周期可以小于时钟周期。每个指令周期一定大于或等于一个 CPU 时钟周期）。

<u>IPS (Instruction Per Second)</u>：每秒执行多少条指令。

**<u>CPU 执行时间</u>**

运行一个程序所花费时间。

CPU 执行时间 = $\frac{\text{CPU 时钟周期数}}{\text{主频}}$ = $\frac{\text{指令条数 } \times \text{ CPI}}{\text{主频}}$

上式表明，CPU 性能（即 CPU 执行时间）取决于三个要素：主频、CPI、指令条数。三者相互制约，例如，更改指令集可以减少程序所含的指令条数，但同时可能引起 CPU 结构的调整，从而可能会增加时钟周期的宽度（降低主频）。

**<u>每秒百万条指令 MIPS (Million Instruction Per Second)</u>**

即每秒执行多少百万条指令。

MIPS = $\frac{\text{指令条数}}{\text{执行时间 }\times 10^6}$ = $\frac{\text{主频}}{\text{CPI }\times 10^6}$

MIPS 对不同机器进行性能比较是有缺陷的，因为不同机器的指令集不同，指令的功能也就不同，比如在机器 M1 上某条指令的功能也许在机器 M2 上要用多条指令来完成。不同机器的 CPI 和时钟周期也不同，因而同一条指令在不同机器上所用的时间也不同。即使在同一台计算机上，不同程序也会有不同的 MIPS。

**<u>每秒执行多少次浮点运算 FLOPS (Floating-point Operations Per Second)</u>**

该参数用来描述计算机的浮点运算性能（用于科学计算的计算机主要评估浮点运算的性能）。

MFLOPS (Million FLOPS) 每秒执行多少百万次浮点运算，MFLOPS = $\frac{\text{浮点操作次数}}{\text{执行时间 }\times10^6}$

GFLOPS (Giga FLOPS) 每秒执行多少十亿次浮点运算，GFLOPS = $\frac{\text{浮点操作次数}}{\text{执行时间 }\times10^9}$

TFLOPS (Tera FLOPS) 每秒执行多少万亿次浮点运算，TFLOPS = $\frac{\text{浮点操作次数}}{\text{执行时间 }\times10^{12}}$

PFLOPS (Peta FLOPS) 每秒执行多少千万亿次浮点运算，PFLOPS = $\frac{\text{浮点操作次数}}{\text{执行时间 }\times10^{15}}$

EFLOPS (Exa FLOPS) 每秒执行多少百亿亿次浮点运算，EFLOPS = $\frac{\text{浮点操作次数}}{\text{执行时间 }\times10^{18}}$

ZFLOPS (Zetta FLOPS) 每秒执行多少十万京次浮点运算，ZFLOPS = $\frac{\text{浮点操作次数}}{\text{执行时间 }\times10^{21}}$

**<u>基准程序(Benchmarks)</u>**

专门用来进行性能评价的一组程序。

通过在不同机器上运行相同的基准程序来比较在不同机器上的运行时间，从而评测其性能。

对于不同的应用场合，应该选择不同的基准程序。

缺陷：基准程序的性能可能与某一小段的短代码密切相关，而硬件系统设计人员或编译器开发者可能针对这些代码片段进行特殊的优化，使得执行这段代码的速度非常快，以至于得不到准确的性能评测结果。

> 提高主频、扩大主存容量等硬件上的优化对性能的提升是有限度的。
> 采用并行处理技术是当前实现高性能计算的重要途径。

## 刷题

+ 字长也可用于评价计算机系统性能的指标。

+ CPU 运行时间 = 花费的 CPU 时钟周期数 × 时钟周期 = 指令条数 × CPI ÷ 主频

  运行时间相关计算（如比值）比值就记住：运行时间和指令条数、CPI 成正比，和主频成反比。

+ 怎么老把 G 当成 $10^6$ 算呢？

+ 算 MIPS 就是算 IPS，不要紧张。

+ 两块 CPU 芯片的片内逻辑电路完全相同（指令集体系结构相同），意味着平均每条指令的时钟周期数（平均 CPI）也相同。