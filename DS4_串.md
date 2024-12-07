## 串的定义和实现

<u>**串的定义**</u>

字符串简称串，是由零个或多个字符组成的有限序列。

空串：含 0 个元素的串（长度为 0），用 $\varnothing$ 表示。

空格串：由 1 个或多个空格组成的串。

**<u>串与线性表</u>**

在逻辑结构上：串和线性表即为相似，区别仅在于串的数据对象限定为字符集。

在基本操作上：串和线性表有很大差别。线性表的基本操作主要以单个元素为操作对象，而串的基本操作通常以子串为操作对象。

**<u>串的存储结构</u>**

+ 顺序存储结构 —— 定长顺序存储表示、堆分配存储表示

  串长可以用一个额外变量保存；也可以在串值末尾加一个不计入串长的结束标记字符 '\0'，此时的串长为隐含值。

+ 链式存储结构 —— 块链存储表示

  每个结点可以存放 $n$ 个字符（$n \ge 1$）。每个结点称为块，整个链表称为块链结构。

  <div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20240809154010359.png" width="500px"/></dev>

<u>**串的基本操作**</u>

最小操作子集：赋值、比较、求串长、求子串、串联接。

其他操作：复制、判空、子串定位（模式匹配）、清空、销毁。

> 最小操作子集中的操作不可能由其他串操作来实现；反之，其他串操作（除串清空和串销毁外）均可在该最小操作子集上实现。

## 串的模式匹配

子串的定位操作通常称为串的模式匹配，它求的是子串（常称模式串）在主串中的位置。

### 简单模式匹配算法

即暴力双循环匹配算法。

最坏时间复杂度为 O(mn)，其中 $m$、$n$ 分别为主串和模式串的长度。

### KMP 算法

<u>**next 数组**</u>

`next[k]` 表示模式串 `substr` 的子串 `substr[0…k-1]` 的最大公共前后缀长度（前后缀必须是真子集，自身不算）。

模式串 `substr` 对应的 `next` 数组求解算法：

```c
void getNext(Str substr, int next[]) {
    next[0] = -1;
    int j = 0, k = -1;
    while (j < substr.length) {
        // k在每个j值的首次循环中对应next[j]
        // 如果一个j值有多次循环,则k是得到next[j+1]的中间数据
        if (k == -1 || substr.ch[j] == substr.ch[k])        
            next[++j] = ++k;
        else
            k = next[k];
    }
}
```

因为 `next[0]` 设为 -1，所以求解 `next` 数组可以拆解为 “已知 `next[j]` 求 `next[j+1]`” 问题，可分为以下两种情况：

1. `substr[j] == substr[k]`

   `substr[j+1]` 之前最长公共前后缀的长度能延伸一位，故 `next[j+1]` 等于 `next[j]` + 1，即 `next[++j] = ++k`。

2. `substr[j] != substr[k]`

   此时只能拿 `substr[j]` 去和最大公共前缀的最大公共前缀的后一位（即 `next[k]`）进行比较。如果相等， `next[j+1]` 等于 `next[k]` + 1；如果不等，就继续套娃。若一直比到 `next[0]` 还是不等，`next[j+1]` 就只能等于 0。

有时为了使公式简洁、计算简单，会将 `next` 数组整体加 1，此时下标应视为位序，`next` 数组公式如下：

<div align=left><img src="https://pic-zerooo.oss-cn-beijing.aliyuncs.com/ungee/image-20240809214724619.png" width="600px"/></dev>

> 目前真题都是从 -1 开始。所以后续的笔记都按 -1 开始。

**<u>KMP 算法</u>**

当主串与模式串发生不匹配时，主串指针不回溯，模式串根据 `next` 数组值回溯。

`next[k]` 也即 `substr[0…k-1]` 的最大公共前缀的后一位字符的下标。当 `next[0]` 为 -1，说明模式串指针位于第一个字符时与主串不匹配，此时模式串应右移一位，主串指针后移一位，即从主串的下一个位置与模式串第一个字符继续比较。

KMP 算法代码：

```c
int KMP(Str str, Str substr, int next[]) {
    int i = 0, j = 0;
    while (i < str.length && j < substr.length) {
        if (j == -1 || str.ch[i] == substr.ch[j]) {
            i++;
            j++;
        }
        else
            j = next[j];  // 主串指针不动,模式串指针回溯
    }
    return j == substr.length ? i - substr.length : -1;
}
```

KMP 算法的时间复杂度为 O(m+n)。

**<u>简单模式匹配算法 vs KMP 算法</u>**

尽管简单模式匹配的时间复杂度为 O(mn)，但在一般情况下其实际执行时间近似为 O(m+n)，因此至今仍被采用。

KMP 算法仅在主串与子串有很多 “部分匹配” 时才显得比普通算法快得多，其主要优点是主串不回溯。

### KMP 算法的优化

前面定义的 `next` 数组在某些情况下尚有缺陷：模式串指针回溯前后指向的字符相同时，再次比较必然失败。在 `next` 数组中体现为出现了值连续的子序列（-1 不计）。

因此需要对 `next` 数组进行优化，优化后的数组更名为 `nextVal`，求解算法如下：

```c
void getNextVal(Str substr, int nextVal[]) {
    int j = 0, k = -1;
    nextVal[0] = -1;
    while (j < substr.length) {
        if (k == -1 || substr.ch[j] == substr.ch[k]) {
            ++j; ++k;
            if (substr.ch[j] != substr.ch[k])    
                nextVal[j] = k;
            else  // 相等时指针回溯后还是不匹配,所以再往前跳
                nextVal[j] = nextVal[k]; 
        } else
            k = nextVal[k];
        // 再往前跳肯定不会再相等,因为nextVal数组是从前往后逐个求得,这种情况显然在之前已经排除
    }
}
```

匹配算法不变。
