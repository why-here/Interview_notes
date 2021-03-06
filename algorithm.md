#### 算法

##### 求一个数开根号

两种方法：二分法，牛顿法

二分法：通过比较中间值与最终值的大小来改变中间值，最终在满足某个精度的情况下返回这个中间值作为最终结果。 

牛顿法：设r是f(x)=0的根，选取x0作为r初始近似值，过点(x0,f(x0))做曲线y=f(x)的切线L，L的方程为y=f(x0)+f′(x0)(x−x0)，求出L与x轴交点的横坐标 x1=x0−f(x0)/f′(x0)，称x1为r的一次近似值。

[Link](https://blog.csdn.net/u012348774/article/details/79804369)

##### LRU 算法

内存页数有限，LRU 通过最近最少使用的策略，在内存填满并且有缺页的时候，淘汰旧页数据。可以通过队列来保存页面访问记录，用哈希表实现快速查询。当引用一个页面，并且该页面在内存上时，将该页重新入队；若页面不在内存上，将队列头部出队，删除哈希表记录，将新页面入队，并在hash表上做记录。

[Link](https://www.geeksforgeeks.org/lru-cache-implementation/)

##### 洗牌

1. 从数组中随机选取一个数p。
2. 将p与数组中最后（也可以是最前）的元素交换。（如果随机选中的是最后的元素，则相当于没有发生交换）
3. 去掉最后的元素（这里并没有删除操作，而是缩小索引值范围），即选中的p，缩小选取的数组范围。
4. 重复步骤（1）~（3），直到数组的长度为1时结束。

从第一张牌开始，将每张牌和随机的一张牌进行交换 

[Link](https://blog.csdn.net/leonwei/article/details/8925056)

##### 链表是否相交并找出交点

- 暴力遍历两个链表 O(n1*n2)；
- 将其中一个链表节点存入哈希表，用另一个链表的节点进行查找，但不能找到交点；
- 遍历两个节点，记录长度，并判断最后一个节点是否相等，若相等则相交，然后通过让较长的链表先走，然后一起走，找到第一个交点。
- 如果一个有环一个没环必定不相交。如果有环且两个链表相交，则两个链表都有**共同一个环**；分别得到两个环中的一个节点，然后判断一个节点是否在另一个环中。若在则相交。

[Link](https://blog.csdn.net/gao1440156051/article/details/51689521)

##### 判断链表是否存在环

- 用 map 记录节点，判断节点是否重复出现；
- 用两个指针，一个指针每次走两步，一个指针每次走一步，若指针相遇则有环；
- 找到环的入口节点：先用两个指针一个两步走，一个一步走，相遇后，快指针从头开始一步走，慢指针继续走，下次相遇即为环的入口。

> 假定起点到环入口点的距离为 a，p1 和 p2 的相交点 M 与环入口点的距离为 b，环路的周长为L，当 p1 和 p2 第一次相遇的时候，假定 p1 走了 n 步。那么有： 
>
> p1走的路径： `a+b ＝ n`； p2走的路径： `a+b+k*L = 2*n`； p2 比 p1 多走了k圈环路，总路程是p1的2倍。可以得到 `k*L=a+b=n` 。
>
> 此时 p1 和 p2 再走 a 步都会到达环的入口。

[Link](http://wuchong.me/blog/2014/03/25/interview-link-questions/)

##### 第 K / 前 K 大的数

- N 数量小：排序后取出 K 个数 O(nlogn)

- N 小， K 也小，通过选择排序或冒泡排序 O(nk)

- 通过快速排序的分区进行查找 O(n)

- N 很大 ，用一个数组维护前 K 大的数，遍历数组，若新数比 K 个数中的最小元素还小，保持不变，否则新数替换最小元素。`O(N*k)`。或使用最小堆替换这个数组，复杂度为 `O(n*logk)`

- 取值范围小，通过计数

  [Link](http://blog.sina.com.cn/s/blog_54f82cc201013tke.html)

##### 正整数分解使得乘积最大问题

- 尽可能多分解出3，然后分解出2，不要分出1。 

- 余数 为 2 ，分解为多个 3 * 2，余数为 1 ，分解为多个 3 * 2 * 2；

  [Link](https://blog.csdn.net/xiaoquantouer/article/details/70142739)

##### 栈的压入、弹出序列

- 模拟，最后判断栈是否为空；[Link](https://www.nowcoder.com/questionTerminal/d77d11405cc7470d82554cb392585106)
- 弹出的元素，在压入序列中个弹出元素之前压入的元素都应该按逆序输出。

##### 包含 min 函数的栈

- 维护两个栈分别用于保存数据以及当前最小数，压入时，最小栈压入当前最小的数（将最小栈的头与压入的数值做比较）。[Link](https://www.nowcoder.com/questionTerminal/4c776177d2c04c2494f2555c9fcc1e49)

##### 数组中出现次数超过一半的数字

- 排序，数组中间的数可能时出现超过一半的数，验证之。
- 遍历计数，目标数的计数将大于其余数的计数，因此遇到当前数相同的数加一，不同的数减一，计数为0时，取当前数；然后验证最后剩余的数是否出现超过一半。[Link](https://www.nowcoder.com/questionTerminal/e8a1b01a2df14cb2b228b30ee6a92163)

##### 连续子数组的最大和

- 动态规划：F(i) =max(F(i-1) + array[i] , array[i]) ; res = max(res, F(i)); [Link](https://www.nowcoder.com/questionTerminal/459bd355da1549fa8a49e350bf3df484)

##### 记录二叉树中和为 S 的所有路径

- 利用深度优先算法遍历，记录链表，进入是 push 退出时 pop 。[Link](https://www.nowcoder.com/questionTerminal/b736e784e3e34731af99065031301bca)

##### 二叉树深度

- 递归：[Link](https://www.nowcoder.com/questionTerminal/435fb86331474282a3499955f0a41e8b)

  ```c++
  if(!pRoot) return 0 ;
  return max(1+TreeDepth(pRoot->left), 1+TreeDepth(pRoot->right));
  ```

- 利用队列逐层遍历，记录层数

##### 字符串的排列

[Link](https://www.nowcoder.com/questionTerminal/fe6b651b66ae47d7acce78ffdd9a96c7) 

<img allign="center" src="G:/%E9%9D%A2%E8%AF%95%E6%95%B4%E7%90%86/permutation.png">

##### 复杂链表的复制

- 在原链表的每个节点后面复制节点；设置随机指针；拆分链表，每个节点的 next 都指向下一个节点的 next （包括复制的节点）。[Link](https://www.nowcoder.com/questionTerminal/f836b2c43afc4b35ad6adc41ec941dba)

##### 统计一个数字在排序数组中出现的次数。

- 二分查找，然后在查找结果的前后继续查找。
- 若数组是 int 型，可对 k-0.5 和 k+0.5 分别进行二分查找，用结果相减。[Link](https://www.nowcoder.com/questionTerminal/e02fdb54d7524710a7d664d082bb7811)

##### 数组除了两个数只出现一次，其他的数都出现两次。找到出现一次的数

- 把所有的数异或保存，得到只出现一次的两个数异或的结果；以异或结果中的其中一个非 0 位为指标将数组划分为两组；分别对两组数异或得到两个只出现一次的数。[Link](https://www.nowcoder.com/questionTerminal/e02fdb54d7524710a7d664d082bb7811)

##### 在递增数组中找到和为 S 的乘积最小的两个数

- 用两个指针指向头部和尾部，如果和过大，向后移动尾部，和过小向前移动头部。[Link](https://www.nowcoder.com/questionTerminal/390da4f7a00f44bea7c2f3d19491311b)

##### 丑数

- 如果 p 是丑数，那么 p=2^x * 3^y * 5^z 。对于任何丑数p，那么 `2*p,3*p,5*p` 都是丑数。res[ix] 表示 res[ix]*3 候选的最小的丑数。[Link](https://www.nowcoder.com/questionTerminal/6aa9e04fc3794f68acf8778237ba065b)

  ```c++
  res[i] = min(res[i2]*2, min(res[i3]*3, res[i5]*5));
  if(res[i] == res[i2]*2) i2++;
  if(res[i] == res[i3]*3) i3++;
  if(res[i] == res[i5]*5) i5++;
  ```

##### 链表中环的入口结点

- 使用 std::set 存储节点， set::insert 返回 pair<iterator,bool> ，若插入没有重复节点，pair.second 返回 True ，若有重复节点，返回 False。 [Link](https://www.nowcoder.com/questionTerminal/253d2c59ec3e4bc68da16833f79a38e4)

##### 求 1+2+3+ ... +n，不能使用循环和条件判断。

- 使用递归+短路特点 `ans && (ans += Sum_Solution(n - 1));`[Link](https://www.nowcoder.com/questionTerminal/7a0da8fc483247ff8800059e12d7caf1)
- 利用构造函数 `A *a = new A[n];` 每次重新计算时，需要重设值。

##### 求二叉树中两个节点的最低公共祖先节点

- 是二叉搜索树：从树的根节点开始和两个输入的节点进行比较。 一个比当前节点大，一个比当前节点小，则当前节点为最低公共祖先。否则根据大小选择左/右子树进行比较。
- 树的节点有指向父节点的指针：转换为求两个链表的第一个公共节点。
- 没有指向父节点的指针：
  - 非递归：用两个链表分别保存从根节点到输入的两个节点的路径，然后把问题转换成两个链表的最后公共节点。
  - 递归：（1）如果两个节点分别在根节点的左子树和右子树，则返回根节点 （2）如果两个节点都在左子树，则递归处理左子树；如果两个节点都在右子树，则递归处理右子树 

[Link](http://blog.csdn.net/wenqiang1208/article/details/64152061)

##### 两个栈实现队列+两个队列实现栈

  由结构体互导数据，得到头部或尾部的数据。栈实现队列是，入栈在第一个栈操作，出栈在第二个栈操作。

  [Link](http://blog.csdn.net/sheepmu/article/details/38428205)

##### 海量数据处理

  [Link](https://blog.csdn.net/v_JULY_v/article/details/6279498)

- **海量日志数据，提取出某日访问百度次数最多的那个IP。** 

  **算法思想：分而治之 + Hash**

  1. IP 地址最多有 2^32 = 4G 种取值情况，所以不能完全加载到内存中处理； 
  2. 可以考虑采用“分而治之”的思想，按照 **IP 地址的 Hash( IP ) % 1024 值**，把海量 IP 日志分别存储到 1024 个小文件中。这样，每个小文件最多包含 4 MB 个 IP 地址； 
  3. 对于每一个小文件，可以构建一个 IP 为 key ，出现次数为 value 的 Hash map，同时记录当前出现次数最多的那个 IP 地址；
  4. 可以得到 1024 个小文件中的出现次数最多的 IP ，再依据常规的排序算法得到总体上出现次数最多的 IP ；

- **搜索引擎会通过日志文件把用户每次检索使用的所有检索串都记录下来，每个查询串的长度为1-255字节。** **请你统计最热门的10个查询串，要求使用的内存不能超过1G。** 

  1. 先对这批海量数据预处理，在O（N）的时间内用Hash表完成**统计** 
  2. 借助堆这个数据结构，找出 Top K，时间复杂度为 N'logK 

- **有一个1G大小的一个文件，里面每一行是一个词，词的大小不超过16字节，内存限制大小是1M。返回频数最高的100个词。** 

  1. 采用类似第一个例子的方法，找出每个小文件中 TOP 100 的词汇，然后进行归并，丢弃掉TOP 100 之后的词。

- **有10个文件，每个文件1G，每个文件的每一行存放的都是用户的query，每个文件的query都可能重复。要求你按照query的频度排序。**

  1. 方案 1 ：与上一个例子相似。
  2. 方案 2 ：query 的总量是有限的，直接用 hash_map 进行统计，然后做排序。

- **给定a、b两个文件，各存放50亿个url，每个url各占64字节，内存限制是4G，让你找出a、b文件共同的url？** 

  1. 将两个文件分别进行 hash，存储到多个小文件中，那么两个文件中相同的 url 将被存入相同编号的小文件中，只要求出小文件中相同的 url 即可。求小文件中相同的 url，可以将一个文件中的 url 存入 hash_set 中，然后遍历另一个文件，查看是否在 hash_set 中。

- **在2.5亿个整数中找出不重复的整数，注，内存不足以容纳这2.5亿个整数。** 

  1. 方案 1 ：采用 2-Bitmap（每个数分配 2 bit，00 表示不存在，01 表示出现一次，10 表示多次，11 无意义）进行，共需内存 2^32 * 2 bit=1 GB 内存，然后扫描这 2.5 亿个整数。 
  2. 方案 2 ：也可采用与第 1 题类似的方法，进行划分小文件的方法。然后在小文件中找出不重复的整数，并排序。然后再进行归并，注意去除重复的元素。 

- **腾讯面试题：给40亿个不重复的unsigned int的整数，没排过序的，然后再给一个数，如何快速判断这个数是否在那40亿个数当中？** 

  1. 方案 1 ：申请512M的内存，一个bit位代表一个unsigned int值。读入40亿个数，设置相应的bit位，读入要查询的数，查看相应bit位是否为1，为1表示存在，为0表示不存在。 
  2. 方案 2 ：将 40 亿个数按最高位为 1 或 0 划分的两个文件中，然后更加待查找的数的最高位来判断在哪个文件中，然后判断次高位。。。时间复杂度位 O(logn)。

- **怎么在海量数据中找出重复次数最多的一个？** 

  1. 先做hash，然后求模映射为小文件，求出每个小文件中重复次数最多的一个，并记录重复次数。然后找出上一步求出的数据中重复次数最多的一个就是所求 

- **上千万或上亿数据（有重复），统计其中出现次数最多的钱N个数据。** 

  1. 与第二题类似

- **一个文本文件，大约有一万行，每行一个词，要求统计出其中最频繁出现的前10个词，请给出思想，给出时间复杂度分析。**

  1. 这题是考虑时间效率。用trie树统计每个词出现的次数，时间复杂度是O(n*le)（le表示单词的平准长度）。然后是找出出现最频繁的前10个词，可以用堆来实现，前面的题中已经讲到了，时间复杂度是O(n*lg10)。所以总的时间复杂度，是O(n*le)与O(n*lg10)中较大的哪一个。 

##### 两个有序数组的中位数

> 回顾下中位数，对于一个有序数组，如果数组长度是奇数，那么中位数就是中间那个值，如果长度是偶数，就是中间两个数的平均数。

- 解法 1 O(nlogn) ：将两个数组合并成一个，然后排序，最后根据数组长度选择中位数

- 解法 2 O(n) ：通过归并排序合并数组，然后根据长度选择中位数

  - 解法 3 O(logn) ：转变成一个寻找第 k 小数的问题。通过对k/2位置数值大小的比较，进行二分查找，逐步排除掉肯定是小于第 k 个数的数，最后找到所求的第k小数。每次都有k一半的元素被删除，所以算法复杂度为log*k*，由于求中位数时k为（m+n）/2，所以算法复杂度为log(m+*n*)。

  [Link](https://blog.csdn.net/yutianzuijin/article/details/11499917)

##### 二叉树基础

> - 二叉树的第 $i$ 层至多拥有 $2^{i-1}$ 个节点数；
>
> > - 深度为 $k$ 的二叉树至多总共有 $2^{k+1}-1$ 个节点数（定义根节点所在深度 $k_0 = 0$）；
> >
> > - 对任何一棵非空的二叉树 T ，如果其叶片(终端节点)数为 $n_0$，分支度为 2 的节点数为 $n_2$，则 $n_0 = n_2 + 1$。
> >
> > - 完全二叉树：叶节点只能出现在最下层和次下层，并且最下面一层的结点都集中在该层最左边的若干位置的二叉树。
> >
> >   - 具有 n 个节点的完全二叉树的高度为 $l o g _2 n + 1 $；
> >   - $n_0$是度为 0 的结点总数（即叶子结点数），$n_1$是度为 1 的结点总数，$n_2$是度为 2 的结点总数。
> >   - $n = n_0 + n_1 + n_2$ （其中n为完全二叉树的结点总数）
> >   - $n = 1 + n_1 + 2*n_2$  （除根结点外其他结点都有父结点）
> >   - $n = 2*n_0 + n_1 - 1$  （上面两式相减，$n_1$ 等于 1 或 0）
> >   - n 为偶数，则 $n_0 = n/2$，n 为奇数，则 $n_0 = (n+1)/2$ （可根据完全二叉树的结点总数计算出叶子结点数）
> >
> >   [Link](https://baike.baidu.com/item/%E5%AE%8C%E5%85%A8%E4%BA%8C%E5%8F%89%E6%A0%91)
> >
> > - 顺序存储
> >
> >   - 若是满二叉树就能紧凑排列而不浪费空间；
> >   - 如果某个节点的索引为i，（假设根节点的索引为0）则在它左子节点的索引会是 $2 i + 1 $，以及右子节点会是 $2 i + 2 $；而它的父节点（如果有）索引则为 $\left\lfloor {\frac {i-1}{2}}\right\rfloor $。
> >
> > - 链表存储
> >
> >   - 使用链表能避免顺序存储浪费空间的问题；
> >   - 但是，由于缺乏父链的指引，在找回父节点时需要重新扫描树得知父节点的节点地址。
> >
> > - 将n叉树转换为二叉树
> >
> >   - 一般有序树可映射为二叉树，但反之未必成立。二叉树当且仅当根节点没有右子结点时可转换为 n 叉树。
> >   - n 叉树转换为二叉树的方法：二叉树中结点 x 的左子结点为 n 叉树中结点 x 的左子结点；二叉树中结点 x 的右子结点为 n 叉树中结点 x 的第一个右边的同级结点 y 。
> >
> >  [Link](https://zh.wikipedia.org/wiki/%E4%BA%8C%E5%8F%89%E6%A0%91)
> >
> > - 二叉搜索树（BST）
> >
> >   - 左子树上所有节点的值均小于它的根节点的值；右子树上所有节点的值均大于它的根节点的值；任意节点的左、右子树也分别为二叉查找树；没有键值相等的节点；
> >   - 优势在于查找、插入的时间复杂度较低。为O(log n)；
> >   - 一个无序序列可以通过构造一棵二叉查找树变成一个有序序列，构造树的过程即为对无序序列进行查找的过程；
> >   - 每次插入的新的结点都是二叉查找树上新的叶子结点，在进行插入操作时，不必移动其它结点，只需改动某个结点的指针；
> >   - 搜索、插入、删除的复杂度等于树高，期望 $O ( log ⁡ n ) $，最坏 $O ( n )$（数列有序，树退化成线性表）。
> >   - 若该组数值经是有序的（从小到大），则建造出来的二叉查找树的所有节点，都没有左子树。
> >
> >   [Link](https://zh.wikipedia.org/wiki/%E4%BA%8C%E5%85%83%E6%90%9C%E5%B0%8B%E6%A8%B9)
> >
> > - 平衡树
> >
> >   > 平衡指所有叶子的深度趋于平衡；几乎所有平衡树的操作都基于树旋转操作，通过旋转操作可以使得树趋于平衡；
> >
> >   - AVL 树
> >
> >     > 任何节点的两个子树的高度最大差别为1；
> >     >
> >     > 节点的**平衡因子**是它的左子树的高度减去它的右子树的高度；带有平衡因子1、0或 -1的节点被认为是平衡的。带有平衡因子 -2或2的节点被认为是不平衡的，并需要重新平衡这个树。
> >
> >     - 在左左和右右的情况下，只需要进行一次旋转操作；在左右和右左的情况下，需要进行两次旋转操作。
> >     - 删除：从AVL树中删除，可以通过把要删除的节点向下旋转成一个叶子节点，接着直接移除这个叶子节点来完成。
> >
> >     [Link](https://zh.wikipedia.org/wiki/AVL%E6%A0%91)
> >
> >   - 红黑树
> >
> >     > 基于二叉查找树增加了额外要求：1. 节点是红色或黑色。2. 根是黑色。3. 所有叶子都是黑色（叶子是NIL节点）。4. 每个红色节点必须有两个黑色的子节点。（从每个叶子到根的所有路径上不能有两个连续的红色节点。）5. 从任一节点到其每个叶子的所有简单路径都包含相同数目的黑色节点。
> >     >
> >     > 从根到叶子的最长的可能路径不多于最短的可能路径的两倍长。
> >     >
> >     > 任何不平衡都会在三次旋转之内解决。
> >
> >     - 插入：首先以二叉查找树的方法增加节点并标记它为红色。接着通过颜色调换（color flips）和树旋转来调整。
> >     - 删除：
> >
> >     > 红黑树相对于AVL树来说，牺牲了部分平衡性以换取插入/删除操作时少量的旋转操作，整体来说性能要优于AVL树。
> >
> >     [Link](https://zh.wikipedia.org/wiki/%E7%BA%A2%E9%BB%91%E6%A0%91)
> >
> >   - B 树
> >
> >     > B 树，概括来说是一个一般化的二叉查找树，可以拥有多于 2 个子节点。
> >     >
> >     > B 树减少定位记录时所经历的中间过程，从而加快存取速度。B 树这种数据结构可以用来描述外部存储。这种数据结构常被应用在数据库和文件系统的实现上。
> >
> >     > 在 B 树中，内部（非叶子）节点可以拥有可变数量的子节点（数量范围预先定义好）。
> >     >
> >     > 内部节点可能会被合并或者分离。
> >     >
> >     > 子节点数量的上界和下界依特定的实现而设置。
> >     >
> >     > B 树中每一个内部节点会包含一定数量的键值。通常，键值的数量被选定在 d 和 2d 之间。因数2将保证节点可以被拆分或组合。
> >     >
> >     > 一个 B 树通过约束所有叶子节点在相同深度来保持平衡。
> >
> >     > 在存取节点数据所耗时间远超过处理节点数据所耗时间的情况下，B 树在可选的实现中拥有很多优势，因为存取节点的开销被分摊到里层节点的多次操作上。
> >
> >   [Link](https://zh.wikipedia.org/wiki/%E5%B9%B3%E8%A1%A1%E6%A0%91)

##### 排序算法

> 1. 稳定性：a 与 b 相等，排序之前 a 在 b 之前，排序之后 a 还在 b 之前。好处：使用部分键值作为指标进行排序后，未作为排序指标的键值的顺序仍旧保持有序，比如用 [112 和 121] 的最高位排序，稳定算法的结果为 [112 121]，不稳定算法结果可能为 [121 112]。[Link](http://qr.ae/TUTLVr)
>
> > 1. 是否基于比较，时间，空间复杂度，最好，最坏情况。
> >
> > 2. 所有基于比较的排序算法时间复杂度至少为 O(nlogn);
> >
> > 3. **冒泡排序**：逐轮比较邻近的值并交换；
> >
> >    - 优化 1 ：若不发生 swap ，表示已正序；
> >
> >    - 优化 2 ：记录最后一次发生交换的位置，其之后的元素已排好序；
> >
> >    - 优化 3 ：进行双向的循环（鸡尾酒排序），正向最大移到末尾，反向最小移到最前。
> >
> >      冒泡排序：从底部往上冒快，从顶部往下冒慢；鸡尾酒排序：双向冒泡，使双向冒泡都快。
> >
> > 4. **插入排序**：每次取一个未排序元素，在已排序的数列中找到合适的位置插入（需要移动元素）。
> >
> >    改进：在插入有序的数列中时，使用二分查找，找到要插入的位置。
> >
> > 5. **希尔排序**：基于插入排序的以下两点性质而提出改进方法的
> >
> >    - 插入排序在对几乎已经排好序的数据操作时， 效率高， 即可以达到线性排序的效率
> >    - 但插入排序一般来说是低效的， 因为插入排序每次只能将数据移动一位
> >
> >    步骤：
> >
> >    - 先取一个正整数 d1(d1 < n)，把全部记录分成 d1 个组，所有距离为 d1的倍数的记录看成一组，然后在各组内进行插入排序
> >    - 然后取 d2(d2 < d1)
> >    - 重复上述分组和排序操作；直到取 di = 1(i >= 1) 位置，即所有记录成为一个组，最后对这个组进行插入排序。一般选 d1 约为 n/2，d2 为 d1 /2， d3 为 d2/2 ，…， di = 1。
> >
> >    [Link](http://bubkoo.com/2014/01/15/sort-algorithm/shell-sort/)
> >
> > 6. **快速排序**：
> >
> >    - 步骤 1 ：从数组中随机取一个值作为标兵
> >    - 步骤 2 ：将数组分为左右两个区间，比标兵大在右，比标兵小在左
> >    - 步骤 3 ：重复步骤 1，2
> >
> >    分区办法：把标兵放在末尾（或取末尾为标兵），循环移动（交换）小于等于标兵的元素到数组左半边，最后将标兵重新交换到指定位置。
> >
> >    应用：使用分区来查找数组中第 K 大的元素，或最大/小的 K 个元素。
> >
> > 7. **选择排序**：首先在数组中找到最大的元素并与末尾元素交换，重复此操作。
> >
> > 8. **归并排序**：递归将数组不断划分为大小为1的数组，然后递归将两个已排好序的数组合并成一个数组。可以使用临时数组用于合并，也可以采用类似插入排序的方法进行合并（将其中一个子数组中的元素依次插入到另一个数组当中）。[Link](http://bubkoo.com/2014/01/15/sort-algorithm/merge-sort/)
> >
> >    归并排序除了可以对数组进行排序，还可以高效的求出数组小和（即单调和）以及数组中的逆序对，详见这篇[博文](http://www.jianshu.com/p/3ab5033074f1)。
> >
> > 9. **堆排序**：将数组看成一颗完全二叉树，递归构造最大堆（堆根节点最大）或最小堆（根节点最小），将剩余的堆继续调整为最大堆。
> >
> > - 操作 1 ：最大堆调整（Max-Heapify）保证下标 i 的结点之后（两层之内）结点都满足最大堆的性质
> >
> > - 操作 2 ：创建最大堆（Build-Max-Heap）将自下而上的调用 Max-Heapify 来改造数组，建立最大堆
> >
> >   - 操作 3 ：堆排序（Heap-Sort）调用Build-Max-Heap将数组改造为最大堆，然后将堆顶和堆底元素交换，之后将底部上升，最后重新调用Max-Heapify 保持最大堆性质。
> >
> >   [Link](http://bubkoo.com/2014/01/14/sort-algorithm/heap-sort/) [Link](https://www.youtube.com/watch?v=MtQL_ll5KhQ)
> >
> > 1. **桶排序**：
> >
> > - 步骤 1 ：假设待排序的一组数统一的分布在一个范围中，并将这一范围划分成几个子范围，也就是桶
> > - 步骤 2 ：将待排序的一组数，分档规入这些子桶，并将桶中的数据进行排序
> > - 步骤 3 ：将各个桶中的数据有序的合并起来
> >
> > 1. **基数排序**：基数排序法会使用到桶 (Bucket)，顾名思义，通过按照要比较的位（个位、十位、百位…），将要排序的元素分配至 0~9 个桶中，借以达到排序的作用，排序完后用第二位分桶排序，直到遍历所有位。
> > 2. **猴子排序**：是个既不实用又原始的排序算法，其原理等同将一堆卡片抛起，落在桌上后检查卡片是否已整齐排列好，若非就再抛一次。
> > 3. **计数排序**：统计数值出现的次数，然后根据统计结果进行排序。反向填充目标数组，可以确保计数排序的稳定性。
> >
> > - 步骤 1 ：统计数组A中每个值A[i]出现的次数，存入C[A[i]]
> > - 步骤 2 ：从前向后，使数组C中的每个值等于其与前一项相加，这样数组C[A[i]]就变成了代表数组A中小于等于A[i]的元素个数
> >   - 步骤 3 ：反向填充目标数组B：将数组元素A[i]放在数组B的第C[A[i]]个位置（下标为C[A[i]] - 1），每放一个元素就将C[A[i]]递减
> >
> > | 排序方法 |       平均情况        |     最好情况     |       最坏情况        |      辅助空间      | 稳定性  |    备注    |
> > | :--: | :---------------: | :----------: | :---------------: | :------------: | :--: | :------: |
> > | 冒泡排序 |     $O(n^2)$      |    $O(n)$    |     $O(n^2)$      |     $O(1)$     |  稳定  |  n 小时好   |
> > | 选择排序 |     $O(n^2)$      |   $O(n^2)$   |     $O(n^2)$      |     $O(1)$     | 不稳定  |  n 小时好   |
> > | 插入排序 |     $O(n^2)$      |    $O(n)$    |     $O(n^2)$      |     $O(1)$     |  稳定  |   有序的好   |
> > | 希尔排序 | $O(nlogn)到O(n^2)$ | $O(n^{1.3})$ |     $O(n^2)$      |     $O(1)$     | 不稳定  |          |
> > | 堆排序  |    $O(nlogn)$     |  $O(nlogn)$  |    $O(nlogn)$     |     $O(1)$     | 不稳定  |  n 大时好   |
> > | 归并排序 |    $O(nlogn)$     |  $O(nlogn)$  |    $O(nlogn)$     |     $O(n)$     |  稳定  |  n 大时好   |
> > | 快速排序 |    $O(nlogn)$     |  $O(nlogn)$  |     $O(n^2)$      | $O(logn)到O(n)$ | 不稳定  |   n 大时   |
> > | 计数排序 |    $O(n + k)$     |  $O(n + k)$  |    $O(n + k)$     |   $O(n + k)$   |  稳定  | 可与基数排序配合 |
> > | 基数排序 |    $O(n * dn)$    | $O(n * dn)$  |    $O(n * dn)$    |  $O(n * dn)$   |  稳定  |          |
> > | 桶排序  |      $O(n)$       |    $O(n)$    | $O(nlogn)或O(n^2)$ |  $O(n + bn)$   |  稳定  |          |
> >
> >  [基于比较](http://www.cnblogs.com/eniac12/p/5329396.html) [不基于比较](http://www.cnblogs.com/eniac12/p/5332117.html)

##### 快排第 n 趟排序结果校验

> 每趟排序就有一个元素排在了最终的位置上。那么就是说，第n趟结束，至少有n个元素已经排在了最终的位置上。 [Link](https://blog.csdn.net/u011240016/article/details/53149645)

##### 矩阵链乘法

> 对于一般的矩阵乘法来说，如矩阵A(m,n)与矩阵B(n,p)相乘需要进行的加法次数为`m*n*p`次乘法。 

- [Link](https://blog.csdn.net/luoshixian099/article/details/46344175)

##### 电影票问题

> 模拟所有人买票过程，递归求解；拿50块钱的都能立即买票，拿100块钱的只有前面拿50块钱的多余100块钱的才能买票。

- [Link](http://samuschen.iteye.com/blog/1158748)