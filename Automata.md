# Automata Review

## Ch.2 FA

### 2.1 DFA

### 2.2 NFA

### 2.3 DFA与NFA的等价性

### 2.4 $\varepsilon-$NFA

### 2.5 DFA的最小化

#### 2.5.1 从DFA构造NFA

- 设$L$是某个DFA $D=(Q,\Sigma,\delta_{D},q_{0},F)$的语言,则存在一个NFA $N$,满足$L(N)=L(D)=L$

- **证明**

  定义$N=(Q,\Sigma,\delta_{N},q_{0},F)$，其中$\delta_{N}$定义为
  
  - 对$q\in Q$和$a\in \Sigma$，若$\delta_{D}(q,a)=p$，则$\delta_{N}(q,a)=\{p\}$
  
  需要证明：对于任何$w\in\Sigma^{*}$，$\delta_{D}^{'}=p \Leftrightarrow \delta_{N}^{'}=\{p\}$
  
  归纳于$|w|$易证上述命题

#### 2.5.2 从NFA构造DFA(子集构造法)

- 设$L$是某个NFA $N=(Q,\Sigma,\delta_{N},q_{0},F_{N})$的语言,则存在一个DFA $D$,满足$L(D)=L(N)=L$

- **证明**

  定义$D=(Q,\Sigma,\delta_{D},q_{0},F_{D})$，其中$\delta_{D}$定义为

  - $Q_{D}=\{S|S \subseteq Q_{N}\}$
  - 对$S\in Q_{D}$和$a\in\Sigma$，$\delta_{D}(S,a)=\bigcup_{q\in S}\delta_{N}(q,a)$
  - $F_{D}=\{S|S\subseteq Q_{N}\land S\cap F_{N}\ne\phi\}$

  需要证明：对于任何$w\in\Sigma^{*}$，$\delta_{D}^{'}(\{q_{0}\},w)= \delta_{N}^{'}(q_{0},w)$

  归纳于$|w|$可证上述命题

## Ch.3 Regular Expression and Regular Language
### 3.1 正规语言

**语法**

- 联合
  - $L \cup M=\{w | w \in L \vee w \in M\}$
- 连接
  - $\mathrm{L} \cdot \mathrm{M}=\left\{\mathbf{w}_{1} \mathbf{w}_{2} | \mathbf{w}_{1} \in \mathbf{L} \wedge \mathbf{w}_{2} \in \mathbf{M}\right\}$
- 星闭包
  - $L^{*}=\cup_{i} \geq\ \ _0 L^{i}$

算符号优先级

- *，·（连接），+

**正规表达式的派生运算符**

- $L^{*}=L L^{*}=L^{*} L$
- $L^n=LL^{n-1}$
- $L?=\epsilon+L$

**归纳定义**

-  字母表 $\Sigma$ 上的正规语言定义如下：

  - 基础1 ：{$\epsilon$}和 $\phi$是正规语言
  - 基础2:若 $a\in\Sigma$，则f $\{a\}$ 是正规语言

  归纳：

  1. 若L和R是正规语言，则$L\cup R$是正规语言
  2. 若L和R是正规语言，则$LR$是正规语言
  3. 若L是正规语言，则$L^{*}$是正规语言

### 3.2 正规表达式的代数定律

- **交换律和结合律**

  - $L+M=M+L$
  - $(L+M)+N=L+(M+N)$
  - $(LM)N=L(MN)$
- **幺元和零元**

  - $\phi+L=L+\phi=L$
  - $\epsilon L=L\epsilon =L$
  - $\phi L=L\phi=\phi$
- **分配律**

  - $L(M+N)=LM+LN$
  - $(M+N)L=ML+NL$
- **等幂率**

  - $L+L=L$
- **与闭包相关的定律**
  - ${\left(L^{*}\right)^{\star}=L^{*}} $
  - $\phi^{*}=\varepsilon$
  - $\varepsilon^{\star}=\varepsilon$
  - $L^{+}=L L^{*}=L^{*} L$
  - $L^{*}=L^{+}+\varepsilon$
- **与任选运算相关的定律**

  - $L ?=\varepsilon+L$

### 3.3 代数定律的具体化

- 具体化：将正规表达式中的每个变量用单个符号替换
- 一般化：将具体表达式中的单个符号用变量表示

### 3.4 例题

**题海无涯 欢迎补充**

1. $\{xwx^{R}|x,w\in (a+b)^{+}\}$

   这题好像有点问题

2. $\{ w|w\in \{a,b\}^{*}\land \exists x,y(x,y\in \{a,b\}^{*} \land w=xy\land \left|y\right|=3\land y=y^{R})\}$

   $(a+b)^{*}(aaa+aba+bbb+bab)$

3. $\{ w\in\{a,b\}^{*}|w中既不包含子串aa，也不包含子串bb\}$

   $(b+\varepsilon)(ab)^{*}(a+\varepsilon)$

4. $\{ a^{n}b^{m}|n,m\ge0 \land n+m为偶数\}$

   $(aa)^{*}(ab+\varepsilon)(bb)^{*}$

5. $\{ w|w\in \{a,b\}^{*},\left|w\right|\ge1,且w的后20位至少有一个a\}$

   　$(a+b)^{*}a(b+\varepsilon)^{19}$

6. $\{ w|w\in \{a,b\}^{*},\left|w\right|\ge1,且当w以a为结尾时，它的长度为奇数\}$

   $((a+b)^{2})^{*}a+(a+b)^{*}b$

7. $\{ w|w\in \{a,b\}^{*},\left|w\right|\ge2,且w的前5位至少有一个子串aa\}$

   $(a+b+\varepsilon)^{3}aa(a+b)^{*}$

8. $\{ w|w\in \{a,b\}^{*},\left|w\right|\ge1,且w的第2位至第5位至少有一个a\}$

   $(a+b)(b+\varepsilon)^{3}a(a+b)^{*}$ 

9. $\{ w|w\in \{0,1\}^{*},w 至少含有3个1，且倒数第3位为1\}$

   $(0+1)^{*}111+(0+1^{*})1(0+1^{*})1(01+10)+(0+1^{*})1(0+1^{*})1(0+1^{*})100$


## Ch.4 Regular Language的应用
### 4.1. NFA转DFA算法

- 可以观看https://www.youtube.com/watch?v=i-fk9o46oVY&t=199s这个网站（需要使用vpn）。最好是将他的关于nfa转dfa的视频全部都观看一遍。

### 4.2  $\varepsilon-NFA$转化成 DFA

- 可以观看https://www.youtube.com/watch?v=i-fk9o46oVY&t=199s这个网站（需要使用vpn）。

### 4.3 有限自动机的最小化

- 填表法：可以观看https://www.youtube.com/watch?v=i-fk9o46oVY&t=199s这个网站（需要使用vpn）。

### 4.4 Thompson 构造法

- https://www.youtube.com/watch?v=7NA69TEd2iQ 第五个ppt有详细解释。

### 4.5 路径迭代法

- $\boldsymbol{R}_{i j}^{1}=\boldsymbol{R}_{i j}^{0}+\boldsymbol{R}_{i 1}^{0}（\boldsymbol{R}_{1 1}^{0}）^{*}\boldsymbol{R}_{1 j}^{0}$
- $\boldsymbol{R}_{i j}^{2}=\boldsymbol{R}_{i j}^{1}+\boldsymbol{R}_{i 2}^{1}（\boldsymbol{R}_{2 2}^{1}）^{*}\boldsymbol{R}_{2 j}^{1}$
- 想理解更多内容，请观看https://www.youtube.com/watch?v=88aU7f4_g4o&t=296s 。

### 4.6 状态消去法

- https://www.youtube.com/watch?v=57MwzSmBZpw

### 4.7 Pumping 引理

- 设 $|Q|=n,$ $w=a_1a_2a_3…a_m(m\ge n)$ 则存在 $i,j,0\leq i<j\leq n$, $p_i=p_j$其中 ${p}_{k}=\delta^{\prime}\left({p}_{o},{a}_{i} {a}_{2} \dots {a}_{k}\right)$，$0\leq k\leq m$.

  假定 $p_0=q_0$,$p_m\in F$, 即$w\in L(D)$

  令 $w=xyz$

  **其中: $x=a_1a_2….a_i$, $ y=a_{i+1}a_{i+2}a_{i+3}….a_{j}$,$z=a_{j+1}a_{j+2}a_{j+3}….a_m$**

  且满足：

  1. $y\ne \epsilon$
  2. $|xy|\leq n$
  3. 对任何 $k\ge 0$, 都有 $xy^kz\in L$

### 4.8 正规语言的封闭运算

- 并

  若L和M为正规语言，则 $L\cup M$也是正规语言

- 补

  若$L$为$\Sigma$上的正规语言，则 $\overline{L}=\Sigma^{*}-L$ 也是正规语言

- 交

  若 $L$ 和 $M$ 为正规语言，则$L\cap M$也是正规语言

- 差

  若$L$和$M$为正规语言，则也是$L-M$正规语言

- 反向

  若$L$为正规语言，则也$L^{R}$是正规语言

- 星闭包

  若$L$为字母表$\Sigma$上的正规语言，则$L^*$也是正规语言

- 连接

  若$L$和$M$为正规语言，则也是$LM$正规语言

- 同态

  若$L$为正规函数，$h : \Sigma \rightarrow T^{*}$，则$H(L)$也是正规语言

- 反同态

  若${S} \subseteq {T}^{*}$为正规语言，${h} : \Sigma \rightarrow {T}^{*}$，则$h^{-1}(S)$也是正规语言

## Ch.5 CFG and CFL

## Ch.6 PDA

### 6.1 PDA的定义

- **下推自动机（pushdown automaton）**是带有**一个**堆栈的有限状态自动机

- PDA的形式定义

  一个下推自动机PDA是一个七元组
  $$
  P=(Q,\Sigma,\Gamma,\delta,q_{0},Z_{0},F)
  $$

  - Q:**状态**的有穷集合
  - $\Sigma$:**输入符号**的有穷集合
  - $\Gamma$: 有限的**堆栈**字母表
  - $\delta$:**转移函数**
  - $q_{0}$:**初始状态**
  - $Z_{0}$:**初始符号**
  - $F$:**接受状态**（或**终结状态**）的集合

- PDA的瞬时描述

  - 用三元组$(q,w,\gamma)$来表示PDA的配置，其中

    1. $q$是状态
    2. $w$是剩余的输入串
    3. $\gamma$是堆栈的内容

    习惯上，把栈顶放在$\gamma$的左端，栈底放在它的右端。这样的一个三元组被称为PDA的一个**瞬时描述（instantaneous description，ID）**。

  - 令$P=(Q,\Sigma,\Gamma,\delta,q_{0},Z_{0},F)$是一个PDA。定义$\vdash_{P}$为：
    $$
    (q,aw,X\beta)\vdash (p,w,\alpha \beta) \Leftrightarrow(p,\alpha)\in \delta (q,a,X)
    $$
     其中$\begin{equation}
    p, q \in Q, a \in \Sigma \cup\{\varepsilon\},  w \in \Sigma^{\star}, X \in \Gamma,  \alpha, \beta \in \Gamma^{*}
    \end{equation}$


### 6.2 PDA的语言

- 终态接受
- 空栈接受
- 从空栈接受到终态接受
- 从终态接受到空栈接受

### 6.3 PDA和CFG的等价性

#### 6.3.1 从CFG构造PDA

- 构造方法

  设CFG $G=(V,T,P,S)$，构造一个**空栈接受**方式的PDA  $E=(\{q\},T,V\cup T,\delta,q,S)$，转移函数定义如下

  1. 对每一$A\in V$，$\delta(q, \varepsilon, A)=\left\{\left.(q, \beta)\right| A \rightarrow \beta  \in P\right\}$
  2. 对每一$a\in T$，$\delta(q,a,a)=\{(q,\varepsilon)\}$

#### 6.3.2 从PDA构造CFG

- 构造方法

  可参考https://blog.csdn.net/fishcanfly000/article/details/5248704

### 6.4 DPDA

#### 6.4.1 DPDA的概念

- 定义

  一个PDA $P=(Q,\Sigma,\Gamma,\delta,q_{0},Z_{0},F)$为DPDA，当且仅当满足下列条件：

  1. 对于$a\in \Sigma$或$a=\varepsilon$，$X\in \Gamma$，$\delta(q,a,X)$最多包含一个元素
  2. 对于$a\in \Sigma$，若$\delta(q,a,X)\ne \varphi$，则$\delta(q,\varepsilon,X)= \varphi$

- 结论

  若为$L$正规语言，则存在DPDA P，$L(p)=L$

#### 6.4.2 与正规语言DPDA

- DPDA的计算能力强于有限自动机

#### 6.4.3 前缀性质及空栈接受的DPDA

- 前缀性质

  一个语言$L$具有前缀性质(prefix property)， 当且仅当不存在 $x,y\in L$, $x\ne y$，且$x$为$y$的前缀(prefix)

- 结论

  一个语言$L$是某个空栈接受的DPDA P的语言,即$L=N(P)$，当且仅当$L$具有前缀性质，并且 $L$是某个DPDA $P^{'}$的语言, 即$L=L(P^{'})$

#### 6.4.4 DPDA与CFL

- 结论

  某些CFL不是任何DPDA的语言
  
- 定义

  若上下文无关语言$L$是某个DPDA的语言，则称$L$为一个**确定的上下文无关语言**(deterministic context-free language) 

#### 6.4.5 DPDA与无二义文法

- 结论

  1. 一个语言$L$是某个空栈接受的DPDA $P$的语言，及$L=N(P)$，则$L$存在一个无二义文法
  2. 一个语言$L$是某个 DPDA $P$的语言,即$L=L(P)$, 则$L$存在一个无二义文法
  3. 固有二义的语言不是任何DPDA的语言
  4. 存在非固有二义的语言$L$，不是任何DPDA $P$ 的语言

## Ch.7 CFL的性质

### 7.1 CFL的范式

#### 7.1.1 消去无用符号

1. 消去所有非生成符号
2. 消去所有非可达符号

#### 7.1.2 消去$\varepsilon$产生式

#### 7.1.3 消去$Unit$产生式

#### 7.1.4 CFG的化简

- 设 CFG $G = (V, T, P , S )$，可以通过下列步骤对$G$进行简化:
  1. 先消去$\varepsilon$产生式
  2. 再消去$Unit$产生式
  3. 最后消去无用符号

#### 7.1.5 Chomsky Normal Form(CNF)

### 7.2 CFL的pumping引理

- **Pumping Lemma for Context-free Language**

  设$L$是CFL，则存在正常数$n$，使得任一长度不小于$n$的字符串$z\in L$，$\left| z\right| \ge n$，都可以分成5部分，即$z=uvwxy$，满足下列条件：

  1. $vx\ne \varepsilon$
  2. $\left| vwx\right| \leq n$
  3.  对任何$k\ge 0$，都有$uv^{k}wx^{k}y\in L$

- Pumping引理的应用

  - 用于证明某个语言$L$不是CFL
  - 证明步骤
    1. 考虑任意的$n>0$
    2. 找到一个满足以下条件的串$z\in L$（长度至少为$n$）
    3. 任选满足$z=uvwxy\land vx\neq \varepsilon \land \left| vwx\right| \leq n$的$u,v,w,x,y$
    4. 找到一个$k\ge 0$，使$uv^{k}wx^{k}y\notin L$
  - 例题

### 7.3 CFL的封闭性

#### 7.3.1 CFL的替换

- 设$\Sigma$为字母表，$L$为语言的集合。映射$s:\Sigma \to L$称为$\Sigma$上的一个**替换**，对$a\in \Sigma$，$s(a)$为某一语言$L_{a}\in L$；替换的概念可以扩充，设$w=a_{1}a_{2}…a_{n}\in \Sigma^{*}$，定义

$$
s(w)=s(a_{1}a_{2}...a_{n})=s(a_{1})s(a_{2})...s(a_{n})
$$

进一步，设$L$为$\Sigma$上的语言，定义
$$
s(L)=\bigcup_{w\in L}s(w)
$$

- 若$L$为$\Sigma$上的CFL，$s$为$\Sigma$上的一个替换，并且对于任何$a\in \Sigma$，$s(a)$均为CFL，则 $s(L)$也为CFL

#### 7.3.2 CFL的并

- 若$L$和$M$为CFL，则$L\cup M$也是CFL

#### 7.3.3 CFL的闭包（星闭包和正闭包）

- 若$L$为CFL，则$L^{*}$和$L^{+}$也是CFL

#### 7.3.4 CFL的连接

- 若$L$和$M$为CFL，则$LM$也是CFL

#### 7.3.5 CFL的同态与反同态

- 设映射$h:\Sigma\to T^{*}$，则对$w=a_{1}a_{2}…a_{n}\in \Sigma^{*}$，定义$h(w)=h(a_{1})h(a_{2})…h(a_{n})$，称为串$w$的一个同态；对语言$L\subseteq \Sigma^{*}$，定义$L$的同态$h(L)=\{h(w)|w\in L \}$
- 若$L$为CFL，$h:\Sigma\to T^{*}$，则$h(L)$也是CFL
- 设映射$h:\Sigma\to T^{*}$，对语言$L\subseteq T^{*}$，定义$L$的反同态$h^{-1}(L)=\{w|w\in \Sigma^{*}\land h(w)\in L \}$
- 若$L\subseteq T^{*}$为CFL，$h:\Sigma\to T^{*}$，则$h^{-1}(L)$也是CFL

#### 7.3.6 CFL的反向

- 设字符串$w=a_{1}a_{2}…a_{n}$，则$w$的反向$w^{R}=a_{n}a_{n-1}…a_{1}$；语言的反向$L^{R}=\{w^{R}|w\in L\}$
- 若$L$为CFL，则$L^{R}$也是CFL

#### 7.3.7 CFL的交，补，差

- 若$L$和$M$为CFL，但$L\cap M$，$\overline{L}$，$L-M$不一定是CFL

#### 7.3.8 CFL和Regular Language的交

- 若$L$为CFL，$R$为RL，则$L\cap R$也是CFL

### 7.4 CFL的判定性质

#### 7.4.1 有关CFG和PDA转换问题的复杂度
- CFG->CNF
  -  消去无用符号: 计算可达符号和生成符号集合为$O(n^{2})$复杂度，但若采取适当的数据结构，复杂度可降为$O(n)$。消去无用符号不增加文法的长度。
  -  消去$\varepsilon$产生式：复杂度为$O(2^{n})$，结果文法的长度为$O(2^{n})$。如果用级连方式改造产生式，则复杂度可降为$O(n)$。
  -  消去$Unit$产生式：计算$Unit$偶对和消去$Unit$产生式，复杂度为$O(n^{2})$,，结果文法的长度为$O(n^{2})$。
  -  用非终结符替换终结符以及打破长度大于2的右部：复杂度$O(n)$,结果文法长度为$O（n）$。

- 两种接受方式PDA相互转换

  - 终态转空栈：线性复杂度
  - 空栈转终态：线性复杂度

- CFG与PDA的相互转换

  - CFG转空栈接受PDA：线性复杂度

  - 空栈接受PDA转CFG：指数复杂度，但可以对转移函数做适当的变换，得到$O(n^{3})$的复杂度

#### 7.4.2 判定CFL是否为空

**判定算法**

1. 计算所有生成符号的集合
2. 判定文法的开始符号是否为生成符号；若是，则该文法的CFL非空，否则为空。

**算法复杂度**

计算生成符号集合为$O(n^{2})$复杂度，但若采用适当的数据结构，复杂度可降为$O(n)$。

#### 7.4.3 判定CFL中是否包含特定的字符串

**判定算法**

1. 将该文法变换为符合CNF
2. 采用CYK算法判定该文法所产生的语言是否包含字符串$w$

**算法复杂度**

设$\left|w\right|=n$,则该算法复杂度为$O(n^{3})$

**CYK算法**

算法可参考https://blog.csdn.net/ssaalkjhgf/article/details/80435676

#### 7.4.4 有关CFL的几个不可判定问题

1. 给定CFG G是否是无二义的？
2. 给定CFL是否是固有二义的？
3. 两个CFL的交是否为空？
4. 两个CFL是否相等？
5. 给定CFL是否等于$\Sigma^{*}$?

#### 7.4.5 判定CFG是否为正则语言

https://blog.csdn.net/ycheng_sjtu/article/details/26104869

## Ch.8 Turing Machine

### 8.1 图灵机

- 图灵机包含可处于状态有穷集合中任何一种状态的**有穷控制（Finite Control）**，有划分成方格或单元的**Tape**，每个单元可包含有穷多种符号中任何一种符号。

- 开始时，**输入**（有穷长度的从**输入字母表**中选择的符号的串）放在带上。所有其他带单元（向左、向右都无穷延伸）开始时都包含一个所谓**空格**的特殊符号。空格是**带符号**，但不是输入符号，除了输入符号和空格之外，还可能有其他的带符号。

- 还有总是位于带单元之一上的**带头**。说图灵机正在**扫描**这个单元。开始时，带头位于包含输入的最左单元上。

- 图灵机的**移动**是有穷控制的状态和扫描的带符号的函数。在一步移动中，图灵机将：

  1. 改变状态。
  2. 在扫描的单元中写带符号。这个带符号代替扫描的单元中的任何符号。
  3. 向左或向右移动带头。

- 图灵机的形式定义

  一个图灵机是一个七元组
  $$
  M=(Q,\Sigma,\Gamma,\delta,q_{0},B,F)
  $$

  - Q:有穷控制的**状态**有穷集合
  - $\Sigma$:**输入符号**的有穷集合
  - $\Gamma$: **带符号**的完整集合，$\Sigma$总是$\Gamma$的子集合
  - $\delta$:**转移函数**
  - $q_{0}$:**初始状态**
  - $B$:**空格符号**
  - $F$:**终结状态**或**接受状态**的集合

- 图灵机的瞬时描述

  - 图灵机$M=(Q,\Sigma,\Gamma,\delta,q_{0},B,F)$的当前格局用字符串$X_{1}X_{2}…X_{i-1}qX_{i+1}…X_{n}$表示，称为**ID（instantaneous descriptions）**，其中
    1. $q\in Q$为$M$当前的状态
    2. 当前带头正在扫描$X_{i}$
    3. $X_{1}X_{2}…X_{n}$为当前带中最左端的非空白符号与最右端的非空白符号之间的带符号串. 有两个例外，即当带头位于最左端非空白符号的左边时，$X_{1}X_{2}…X_{n}$的某 个前缀部分为空白符号串;当带头位于最右端非空白符号的右边时，$X_{1}X_{2}…X_{n}$的某个后缀部分为空白符号串
  - 给定图灵机$M=(Q,\Sigma,\Gamma,\delta,q_{0},B,F)$，定义ID‘s之间的推导关系$\vdash_{M}$如下：
    - 设$\delta ( q,X_{i}) =(p,Y,L)$，则有$X_{1}X_{2}…X_{i-1}qX_{i}X_{i+1}…X_{n}\vdash_{M}X_{1}X_{2}…X_{i-2}pX_{i-1}YX_{i+1}…X_{n}$，但有如下两个例外
      1. $i=1$时，$qX_{1}X_{2}…X_{n}\vdash_{M}pBYX_{2}…X_{n}$
      2. $i=n$及$Y=B$时，$X_{1}X_{2}…X_{n-1}qX_{n}\vdash_{M}X_{1}X_{2}…X_{n-2}pX_{n-1}$
    - 设$\delta ( q,X_{i}) =(p,Y,R)$，则有$X_{1}X_{2}…X_{i-1}qX_{i}X_{i+1}…X_{n}\vdash_{M}X_{1}X_{2}…X_{i-1}YpX_{i+1}…X_{n}$，但有如下两个例外
      1. $i=n$时，$X_{1}X_{2}…X_{n-1}qX_{n}\vdash_{M}X_{1}X_{2}…X_{n-1}YpB$
      2. $i=1$及$Y=B$时，$qX_{1}X_{2}…X_{n}\vdash_{M}pX_{2}…X_{n-1}X_{n}$
    - 上述关系$\vdash_{M}$的自反传递闭包记为$\vdash_{M}^{*}$(或$\vdash^{*}$ )

- 递归可枚举语言

  - 可以被图灵机接受的语言称为**递归可枚举语言（recursive enumerable languages）**

  - 给定图灵机$M=(Q,\Sigma,\Gamma,\delta,q_{0},B,F)$,定义$M$的语言
    $$
    L(M)=\{ w|w \in \Sigma^{*} \land \exists p(p \in F \land \alpha \in \Gamma^{*} \land \beta \in \Gamma^{+} \land q_{0}w \vdash_{M}^{*} \alpha p \beta )\}
    $$

  - 图灵机的停机

    停机（halts）指图灵机不存在下一个移动（move）

  - 结论

    任给图灵机$M$，容易构造一个图灵机$M^{'}$,使得$L(M)=L(M^{'})$，并满足：如果$w\in L(M)$，则对于$w$，$M^{'}$接受$w$并一定停机。但是，如果$w\notin L(M)$，则对于$w$，$M$不一定能停机

  - 递归语言(recursive languages)

    称语言$L$是**递归的**，当且仅当存在图灵机$M$，使得$L=L(M)$且满足：

    1. 如果$w \in L(M)$，则对于$w$，$M$接受$w$（自然会停机，到达终态）
    2. 如果$w \notin L(M)$，则对于$w$，$M$最终也会停机（虽然不能到达终态）

    递归语言对应的问题是可判定的（Church-Turing论题）

### 8.2 基本图灵机的编程技巧

- 利用带存储区的状态（storage in the state）

  此类图灵机$M=(Q,\Sigma,\Gamma,\delta,q_{0},B,F)$中，状态中可以包含一个具有有限个取值的存储单元，即状态集合为$Q=S\times T=\{ [q,a]|q\in S\land a\in T\}$，其中$q\in S$通常表示控制状态，而$a\in T$通常表示数据元素

- 多道（multiple tracks）图灵机

  此类图灵机$M=(Q,\Sigma,\Gamma,\delta,q_{0},B,F)$中，带符号可以说元组的形式

- 子例程（subroutines）的设计

### 8.3 对基本图灵机的扩展

#### 8.3.1 多带图灵机（Multitape Turing Machines）

- 特点

  1. 初始时，输入符号串置于第一条带上;所有带（包括第一条）的其它单元格的符号均为空白符;有限 控制处于初态;第一条带的读写头(带头)置于输入符号串的最左端;其余各带的读写头置于任何单元格上
  2. 在每一个移动步(move)里，控制进入新的状态，每条带上正被扫描的符号被替换为新的带符，每个带头独立地左移一格、右移一格或者不动.

- 语言接受能力与单带图灵机等价

  可以采用一个既具有带存储区的状态，又带有多个道的图灵机来模拟。$k$个带的图灵机可以用$2k$个道的图灵机来模拟

#### 8.3.2 非确定图灵机（Nondeterministic Turing Machines）

- 下一个动作有多种选择

  转移函数可以为$\delta:Q\times \Gamma \to 2^{Q\times \Gamma\times D}$，其中$Q$、$\Gamma$和$D$分别为有限状态集、带符号集和带头的移动方向。即$\delta(q,X)$为三元组的集合: $\{(q_{1} ,Y_{1} ,D_{1} ),(q_{2} ,Y_{2} ,D_{2} ),...,(q_{k} ,Y_{k} ,D_{k} ) \} $

- 语言接受能力与（确定的）图灵机等价

### 8.4 受限的图灵机

#### 8.4.1 具有半无穷带（Semi-infinite Tapes）的图灵机

- 带头的初始位置左部没有单元格，带头移动受限于从带头初始位置开始向右无限延伸的范围
- 可以用一个双道的半无穷带图灵机模拟具有双向无穷带的基本图灵机.

#### 8.4.2 多栈机（Multistack Machines）

- 具有多个下推栈的PDA，包含$k$个下推栈的一步转移可表达为$(p, \gamma_{1}, \Gamma_{2}, ..., \Gamma_{k})\in(q, a, X_{1}, X_{2}, ..., X_{k})$
- 利用一个多带图灵机很容易模拟多栈机
- 利用一个双栈PDA可以模拟基本图灵机

#### 8.4.3 计数器机（Counter Machines）

- 结论
  1. 具有一个计数器的计数器机的语言接受能力相当于确定的下推自动机
  2. 具有两个(或以上)计数器的计数器机的语言接受能力相当于图灵机，即可以接受递归可枚举语言
  3. 任何递归可枚举语言可以被具有三个计数器的计数器机接受
  4. 任何具有三个计数器的计数器机可以用一个具有两个计数器的计数器机来模拟

### 8.5 图灵机与计算机

- 普通计算机模拟图灵机

  采用适当的数据结构(如转移表)不难编制普通的计算机程序实现图灵机的有限状态控制机制。存在问题的是如何模拟无限延伸的带，因为普通计算机的存储空间(包括各个级别的存储器)是有限的. 但是，可以假想一种可以无限扩充存储量的存储系统。实际上，可装卸的外存系统并不严格规定存储量的上限，而且并非所有信息都需要在线存储

- 多带图灵机模拟普通计算机

  可以用多带图灵机模拟典型的存储程序式计算机

## Ch.9 计算理论初步

### 9.1 对角语言与通用语言

#### 9.1.1 图灵机与输入串的二进制编码

- 图灵机的编码

  对于所关心的问题不失一般性，为方便讨论，先对图灵机作一些假定和简化:

  1. 输入字母表为$\{0,1\}$
  2. 假定有限状态为$q_{1}, q_{2},…, q_{k}$，并假定初态总是$q_{1}$，终态总是$q_{2}$(因已假设图灵机到达接受态总是停机，所以假定一个终态即可)
  3. 假定带符号为$X_{1},X_{2},…,X_{m}$，并假定$X_{1}$总代表0，$X_{2}$总代表1，$X_{3}$总代表B
  4. 假定带头的移动方向为$D_{1}$ 和$D_{2}$，分别代表$L$和$R$

  在这些假定之后，转移规则$\delta(q_{i} ,X_{j}) = (q_{k} , X_{l} , D_{m})$可以编码为$0^{i}10^{j}10^{k}10^{l}10^{m}$，所有转移规则的编码排列在一起可以作为该图灵机的编码，形如$C_{1}11C_{2}11...C_{n-1}11C_{n}$

- 0，1字符串的编码

- 图灵机输入串偶对的编码

  在通用语言的定义中，将会用到图灵机与输入串偶对 $(M,w)$ 的编码. 设$M$的二进制编码为$C$，$w$的二进制编码为$C^{'}$，则$(M,w)$的二进制编码为$C 111 C^{'}$.

#### 9.1.2 对角（diagonalization）语言

- 首先给图灵机编码
  规则如下：

- 结论

  $L_{d}$ 不是递归可枚举语言

#### 9.1.3 递归语言和递归可枚举语言的补运算

- 结论
  1. 作用于递归语言的补运算是封闭的。 即如果$L$是递归语言， 则$\overline{L}$ 也是递归语言
  2. 递归可枚举语言的补运算不是封闭的
  3. 如果语言$L$及$\overline{L}$都是递归可枚举的，则语言$L$及$\overline{L}$都一定是递归的

#### 9.1.4 通用（universal）语言

### 9.2 问题与语言

### 9.3 问题的归约

### 9.4 有关图灵机的判定问题

### 9.5 Post对应问题与问题的不可判定性

- Post对应问题

  Post对应问题（Post’s Corresponding Problem），简称PCP。PCP的一个实例包含同一字母表上的两组字符串，，；称PCP的该实例有解，当且仅当存在整数序列，使得

- 结论

  Post对应问题是不可判定的

  我记得这部分好像是书上有证明的，但是并没有能够

### 9.6 P问题与NP问题

- $P \subseteq NP$
- $P = NP \ ???$未解之谜

### 9.7 NP-完全问题与NP-难问题

