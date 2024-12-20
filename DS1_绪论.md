## 数据结构的基本概念

**<u>数据</u>**

信息的载体，是描述客观事物属性的数、字符以及所有能输入到计算机中并被计算机程序识别和处理的符号的集合。

例如：整数、实数、字符串。

**<u>数据元素</u>**

数据的基本单位，通常作为一个整体进行考虑和处理。

例如：一名学生的记录。

**<u>数据项/数据域</u>**

构成数据元素的不可分割的最小单位。

例如：一名学生的记录由学号、姓名、性别等数据项组成。

**<u>数据对象</u>**

**性质相同**的数据元素的集合，是数据的一个子集。

例如：整数数据对象是集合 N = {0, ±1, ±2, ……}。

**<u>数据类型</u>**

一个值的集合和定义在此集合上的一组操作的总称。

分为：

1）原子类型：其值不可再分的数据类型。

2）结构类型：其值可以再分解为若干成分（分量）的数据类型。

3）抽象数据类型 ADT (Abstract Data Type)：一个数据模型及定义在该数学模型上的一组操作。它通常是对数据的某种抽象，定义了数据的取值范围及其结构形式，以及对数据操作的集合。

**<u>数据结构</u>**

相互之间存在一种或多种特定关系的数据元素的集合。

二元组 (D, S) 表示：D 是数据元素的有限集，S 是 D 上关系的有限集。

三要素：逻辑结构、存储结构/物理结构/映像、数据的运算。

> 可以用 ADT 定义一个完整的数据结构。

**<u>逻辑结构</u>**

指数据元素之间的逻辑关系，即从逻辑关系上描述数据。

数据的逻辑结构分为线性结构和非线性结构。

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20231017130042091.png" width="600px"/></dev>

严蔚敏：由于高级程序设计语言中的数组类型也有随机存取的特性，因此通常都用数组来描述数据结构中的顺序存储结构。

> 多数场合下，数组特别是强调几维数组时，都是指存储结构而非逻辑结构。
>
> 数组也不一定就是顺序存储结构，如静态链表使用的数组就是链式存储结构。

**<u>存储结构/物理结构</u>**

数据结构在计算机中的表示（映像）。

包括：数据元素的表示、关系的表示。

分为：

1）顺序存储

把逻辑上相邻的元素存储在物理位置上也相邻的存储单元中，元素之间的关系由存储单元的邻接关系来体现。

优点：①可随机存取；②存储密度大，每个元素占用最少的存储空间。

缺点：①只能使用相邻的一整块存储单元，因此可能产生较多的外部碎片；②增删元素不方便。

2）链式存储

借助指示元素地址的指针来表示元素之间的逻辑关系。

优点：①不会出现碎片现象，能充分利用所有存储单元；②增删元素方便。

缺点：①每个元素因存储指针而占用额外的存储空间；②只能顺序存取。

3）索引存储

在存储元素信息的同时，还建立附加的索引表。

索引表中的每项称为索引项，索引项的一般形式是 (关键字, 地址)。

优点：检索速度快。

缺点：附加的索引表额外占用空间；增删元素也要修改索引表，因而会花费较多的时间。

4）散列存储/哈希存储

根据元素的关键字直接计算出该元素的存储地址。

散列是算法，散列存储方法本质上是顺序存储方法的拓展，散列表本质上是顺序表的拓展。

优点：检索、增加和删除结点的操作都很快。

缺点：可能出现冲突，而解决冲突会增加时间和空间开销。

> 数据的逻辑结构独立于其存储结构 √
>
> 数据的存储结构独立于其逻辑结构 ×
>
> 数据的存储结构是逻辑结构在计算机上的映射，是用计算机语言实现的逻辑结构（依赖于计算机语言）。

<u>**数据的运算**</u>

包括：运算的定义、实现。

运算的定义针对逻辑结构，指出运算的功能。

运算的实现针对存储结构，指出运算的具体操作步骤。

<u>**随机访问 vs 顺序访问**</u>

随机访问/直接访问：访问某记录所需的时间与该记录所在的位置无关。

顺序访问：按记录的逻辑顺序进行读、写操作的存取。

> 访问 = 存取 = 读 + 写

> 随机访问，random access，翻译为 “随意访问” 感觉更贴切一点。

## 算法和算法评价

<u>**算法 Algorithm**</u>

对特定问题求解步骤的一种描述，它是：

1）指令的有限序列，其中每条指令表示一个或多个操作。

2）由基本运算及规定的运算顺序所构成的完整的解题步骤。

3）按照要求设计好的有限确切的计算序列。

<u>**算法特性**</u>

1）有穷性：有穷步、每一步有穷时间。

2）确定性：每一步有确定定义，无二义性，相同输入只能得到相同的输出。

3）可行性：算法中描述的操作都可通过已实现的基本运算执行有限次来实现。

4）输入：0 或多个。这些输入取自于某个特定的对象的集合。

5）输出：1 或多个。这些输出是与输入有着某种特定关系的量。

<u>**“好” 的算法——算法设计目标**</u>

正确性、可读性、健壮性、高效率、低存储量。

<u>**算法效率的度量**</u>

算法效率的度量是通过时间复杂度和空间复杂度来描述的。

**<u>时间复杂度</u>**

语句频度：该语句在算法中被重复执行的次数。

算法中所有语句的频度之和记为 $T(n)$，它是该算法问题规模 $n$ 的函数。

时间复杂度主要分析 $T(n)$ 的数量级。

算法中基本运算（最深层循环内的语句）的频度 $f(n)$ 与 $T(n)$ 同数量级，因此通常将算法中基本运算的执行次数的数量级作为该算法的时间复杂度。

于是算法的时间复杂度记为 $T(n)=O(f(n))$，其中 $O$ 的含义是 $T(n)$ 数量级。

算法的时间复杂度不仅依赖于问题的规模 $n$，也取决于待输入数据的性质（如输入数据元素的初始状态），因此就有了最坏、最好、平均时间复杂度。一般总是考虑最坏时间复杂度，以保证算法的运行时间不会比它更长。

**<u>空间复杂度</u>**

算法的空间复杂度 $S(n)$ 定义为该算法所需的存储空间，它是问题规模 $n$ 的函数，记 $S(n)=O(g(n))$。

除本身所用的指令、常数、变量和输入数据外，还需要一些对数据进行操作的工作单元和存储一些为实现算法所需信息的辅助空间。

若输入数据所占空间只取决于问题本身，和算法无关，则只需分析除输入和程序之外的额外空间。

原地工作：算法所需的**辅助**空间为常量，即 $O(1)$。

## 刷题总结

+ 逻辑结构 vs 数据结构

  逻辑结构：有序表。

  数据结构：顺序表（线性表的顺序存储）、单链表（线性表的链式存储）、循环队列（环状顺序队列）。

  可根据 <u>是否可以使用多种存储结构进行存储</u> 进行区分。

+ 对于两种不同的数据结构，它们的逻辑结构和物理结构完全有可能相同，比如二叉树和二叉排序树。

  所以说，数据的运算也是数据结构的一个重要方面。

+ 1.2.3 选择 15 与归纳总结。
