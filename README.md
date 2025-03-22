# 再谈素数

大家都知道素数是乘法世界的基础，素数奇怪和不可捉摸的性质，比如素数产生没有规律，素数的数量是无限的。

这里想和大家从素数的定义再来看看素数的性质。

## 明确一下文章的定义

1. 素数：就是我们通常规则立即中的素数；
2. 伪素数：文章中满足特定条件下的素数，素数必然会从伪素数中产生；
3. 伪孪生素数：文章中满足特定条件下的孪生素数。
4. 大部分伪素数最终都会变成合数。

## 构造素数规则

### 选取第一个素数

在一堆自然数列表中，我们删掉所有型为 $2n$ 的数会形成如下表格，其中被删掉的用灰色表示，剩余的用绿色表示，后续的 **素数必然在绿色** 中构造，这里称为伪素数：

![t2](src/02.png)

从素数2向后看，除了2本身之外，所有的伪素数必然可以写成： $\{2m + 1 | m \in \mathbb{Z} \}$ 的形式，这就是我们常见的奇数。

后续伪素数产生的概率为： $\frac{1}{2}$ 。

### 选取素数3

选取剩余的数中的第一个3，做为我们的新素数，删掉所有型为 $3n$ 的数，更新表格如下：

![t3](src/03.png)

剩下的所有素数均在绿色的区域产生，**所以除了2、3本身，所有的伪素数必然可以写成： $(6m - 1) 或 (6m +1)$ 。**

$$
\{ 2k + 1 | k \in \mathbb{Z} \} \setminus \{ 3j | j \in \mathbb{Z} \}
 = \{ (6m \pm 1) | m \in \mathbb{Z} \}
$$

后续伪素数产生的概率为： $\frac{1}{3}$ ， 对于伪孪生素数仅仅考虑其中的最小素数参数，其概率为： $\frac{1}{6}$。

在引入新的素数之前，伪素数产生的位置是有规律的，2和3过滤之后，所有的剩余的数均按照孪生素数的行为排列，这是 **孪生素数产生的基础** 。


### 选取素数5

继续确认素数，选取剩余的数中的第一个5，删掉 $5n$ 的数，更新表格如下：

![t5](src/05.png)

其实到这一步我们要说的素数生成规则已经全部展现了，这是从自然数2开始拿掉第一个绿色数的倍数数字，不断让所有的表格中的绿色变成其它颜色。

**从自然数5开始引入的素数，让剩余伪素数选取规律不在那么明显，且越往后越无序**。

当引入素数5之后，自然数中素数存在的概率变更低，但是伪素数的出现的可能形式变得更加多了，**所以除了2，3，5本身外**，所有的伪素数必然可以写成：

$$
\{ (6k \pm 1) | k \in \mathbb{Z} \}  \setminus \{ 5j | j \in \mathbb{Z} \} = \{ (30m \pm 13) \cup (30m \pm 11) \cup (30m \pm 7) \cup (30m \pm 1) | m \in \mathbb{Z} \}
$$ 

后续伪素数产生的概率为： $\frac{4}{15}$ ，伪孪生素数的概率为： $\frac{1}{10}$ 。

这种概率减少总类增加的性质加速了下一个素数位置的随机性，这也是素数定义本身来的的规律，但在产生随机性的同时，也有一些规律性。

在引入了7之后，所有的伪素数必然可以写成如下形式之一：

$$
\begin{gather}     
    \{     
        (210m \pm 1), (210m \pm 11), (210m \pm 13), (210m \pm 17),   \\
        (210m \pm 19), (210m \pm 23), (210m \pm 29), (210m \pm 31),  \\
        (210m \pm 37), (210m \pm 41), (210m \pm 43), (210m \pm 47),  \\
        (210m \pm 53), (210m \pm 59), (210m \pm 61), (210m \pm 67),  \\
        (210m \pm 71), (210m \pm 73), (210m \pm 79), (210m \pm 83),  \\
        (210m \pm 89), (210m \pm 97), (210m \pm 101),(210m \pm 103)  \\
        | m \in \mathbb{Z}     \} 
\end{gather}
$$

后续伪素数产生的概率为： $\frac{8}{35}$ ，伪孪生素数的概率为： $\frac{1}{14}$ 。

在这一步之后，我们可以得到一个明确结论：**伪素数的特性传递**，什么意思呢？

$$
无论是引入2之后的\{ 2k + 1 | k \in \mathbb{Z} \}特性还是引入3之后的\{ (2 \cdot 3 \cdot m \pm 1) | m \in \mathbb{Z} \}，将会永远传递下去，\\
总是会存在 \{ (2 \cdot 3 \ldots p \cdot m \pm 1) | m \in \mathbb{Z} \}，\\
依次类推，所有新引入素数p产生的其它特性都会传递。
$$

**这个性质不能用于寻找素数，因为特性传递的速度远远大于素数产生的速度**，但在引入素数 $p$ 之后，特性将会向前筛选，就是特性的发散的目标总是尝试规避已知素数的规律。

当表格中所有的绿色全部消失后，这个表看起来像这样：

![t7+](src/7+.png)

我们总结一下素数特性传播的规律：

1. 素数 $p$ 的特性是所有已知的素数序列 $2 \cdot 3 \cdot 5 \ldots p_l \cdot p$ 中 $p_l$ 的特性和最后素数 $p$ 倍数的差集；
2. 对于已知素数序列： $2 \cdot 3 \cdot 5 \ldots p$ ，特性 $\{ (2 \cdot 3 \ldots p \cdot m \pm k) | m \in \mathbb{Z} , k 为 1 \ldots n,n+2 \ldots 等 \}$ ，对区间 $p$ 到 $(p+2)^2$ 或 $(p+4)^2$ 之间(分别命中 $6m-1$ 和 $6m+1$ )的素数预期准确率为100%；
2. 对于已知素数序列： $2 \cdot 3 \cdot 5 \ldots p$ ，特性 $\{ (2 \cdot 3 \ldots p \cdot m \pm k) | m \in \mathbb{Z} , k 为 1 \ldots n,n+2 \ldots  等 \}$ ，在不考虑后续素数产生的情况下，伪素数的预期准确率为100%（因为不考虑新素数必然互质）；
3. 引入新素数后，老素数产生的特性不会消失；
4. 每引入一个新素数之后，特性交替发散叠加向后传播，速度远大于素数生成的速率；

## 为什么孪生素数的特性永不消失？

考虑素数序列由 $2,3,5 \ldots p$ 扩充为 $2,3,5 \ldots p \cdot p_n$ 时，由于 $p$ 的特性中存在 $\{ (2 \cdot 3 \ldots p \cdot m \pm 1) | m \in \mathbb{Z} \}$ ，而 $p_n$ 与 $(2 \cdot 3 \ldots p)$ 互质，那么 $\{ (2 \cdot 3 \ldots p \cdot m) | m \in \mathbb{Z} \} \equiv 0,1 \ldots p_n -1 \pmod{p_n}$ ，在新特性 $\{ (2 \cdot 3 \ldots p \cdot p_n\cdot m \pm k) | m \in \mathbb{Z} , k 为 1 \ldots n,n+2 \ldots 等 \}$ 中，除了模数为 $1,p_n-1$ 两个位置，其余的 $p_n-2$ 个由 $\{ (2 \cdot 3 \ldots p \cdot m \pm 1) | m \in \mathbb{Z} \}$ 产生的伪孪生素数对必然会保留下来。

举例来说明：

$$
\begin{gather}
当素数序列：2,3,5,7 扩充到 2,3,5,7,11时，除了 \\
2 \cdot 3 \cdot 5 \cdot 7 \equiv 1 \pmod{11} 和  \\
2 \cdot 3 \cdot 5 \cdot 7 \cdot 10 \equiv 10 \pmod{11} \\
对应的伪素数特性对会被破坏，其余均会保留。
\end{gather}
$$

## 孪生素数是无限的吗？

我们都知道素数是无限的，因为我们总是可以构造一个 $p_1 \cdot p_2 \cdot p_3 \ldots p_n + 1, (其中 p_1，p_2, p_3, \ldots , p_n 为所有已知素数列表)$ ， 那 **孪生素数或者是多胞胎素数** 呢？

“从直观感受上来看，孪生素数的减少是因为新产生素数的倍数规则消掉了以 $2 \cdot 3$ 预留的 **可能素数产生位** ， 考虑到所有素数是互质的，那么 $(2 \cdot 3)  和 (5 \cdot 7 \cdot 9 \cdot 11 \ldots \ p_n)$ 也互质，当数足够大之后，**100%** 同时命中 $(6m - 1 ) 或 (6m + 1)$ 是矛盾的，即 $gcd(2 \cdot 3 , 5 \cdot 7 \cdot 9 \cdot 11 \ldots \ p_n) > 1$ , 这个结论是违背我们素数的定义的”。

上面的结论其实无法证明，当素数增加时，遮盖 $(6m - 1) 或 (6m + 1)$ 的概率也越来越大，但永远达不到 **100%（孪生素数出现概率趋近于0）** ,暂时无法证明是不是会出现后面素数交替覆盖而达到让孪生素数不出现的情况。

### 能用反证法吗？

可以，在明确素数特性100%传递的基础之上，假如在达到一个非常大的素数 $p$ 之后，不再出现新的孪生素数，那么那么我们考虑这个数列的实际情况：

1. 如果素数 $p$ 之后不再有孪生素数了，那么 $2,3,5,7 \ldots p$ 的倍数必然命中后面所有的 $\{6m - 1 | m \in \mathbb{Z}\}$ 或 $\{6m + 1 | m \in \mathbb{Z}\}$ ；
2. 那么 $2,3,5, \ldots p , p_m , p_n , p_k$ 必然在 $p$ 之后不存在 $\{ (2 \cdot 3 \ldots p \cdot m \pm k) | m \in \mathbb{Z} , k 为 1 \ldots n,n+2 \ldots 等 \}$ 这个特性（因为被条件1必然命中了）；
3. 而我们上面已经证明过，孪生素数的特性必然不会丢失；
4. 这个和我们前面的证明产生了矛盾；
5. **故不存在最大的孪生素数对**。


由于素数的规律，不可能出现一个规律性的公式能够绝对匹配素数，但素数特性传递的规律又像在证明一个事实：

$$
    凡是可能出现，必然会出现。
$$