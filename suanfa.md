## 1 面试注意事项

### 1-1 算法面试 

- 思考路径
- 不代表正确地回答，思考方向更重要
- 对问题细节和应用环境有沟通
- 排序：
  - 快排
  - 数据特征：大量重复元素---》**三路快排**
  - 数据近乎有序：插入排序
  - 是否取值范围非常有限：计数排序
  - 额外要求：稳定---》归并排序
  - 存储状况，快排以来随机存取，链表--》归并排序
  - 数据量大小：太大---》外排序
- 独到见解，优化，代码规范，容错性

### 1-2 面试问题

- 项目经历以及遇到的问题

- 印象最深的 bug

- 面向对象，设计模式

- 网络相关，安全相关，内存相关，并发相关

- 遇到的最大的挑战

- 犯过的错误

- 遭遇的失败

- 最享受的工作内容

- 遇到冲突的处理方式

- 做的最与众不同的的事儿

- 准备好合适的问题问面试官（也可以对面试官问过的问题进行反问）

  - 小组的运行模式
  - 项目的后续规划
  - 产品中问题的解决方法
  - 员工培训（入职前，在职）
  - 发展空间，晋升途径
  - 您觉得，这份工作所需的能力，我还有哪些不具备？ 

### 1-3 内容

- 各种排序算法
- 基础数据结构和算法的实现：堆，二叉树，图
- 基础数据结构的使用：如链表，栈，队列，哈希表
- 基础算法：深度优先，广度优先，二分查找
- 基础算法思想：递归，分治，回溯搜索，贪心，动态规划
- Leetcode HackerRank

### 1-4 题目解读

- 注意题目中的条件
- 没有思路时，找几个简单的测试用例
- 不要忽视暴力解法
  - 例如：在字符串中找没有重复字母的最长子串 O(n^2) 遍历 O(n) 判断 ---》O(n^3)
- 极端条件判断，变量名，模块化
- 对于基础问题，寿司代码，快排等

## 2 复杂度判读

### 2-1 时间复杂度

- 时间复杂度
- 大O ：O(f(n)) 需要执行的指令与 f(n) 成正比，最低上界
  - 在学术界，O(f(n)) 指的是算法执行的上界
- 算法复杂度在有些情况下是用例相关的

### 2-2 数据规模

- 10^5 进行选择排序，
- 1 s 之内解决问题，O(n^2) 可以处理 10^4 级别的数据 ， O(n) -> 10^8级别 O(nlogn)->10^7级别
- 空间复杂度：辅助空间；递归调用的空间代价


### 2-3 复杂度

- 判断素数

### 2-4 复杂度实验

- 实验，观察趋势
- 自底向上的归并排序
- log2N/logN = 1 + log2/logN 

### 2-5 递归复杂度

- 不是递归都是 O(logn) 的复杂度
- 二分搜索
- 多次递归调用，可能是指数级算法
- 递归算递归几层，每层都处理什么量级的数据

### 2-6 均摊复杂度

- 动态数组 Vector ：resize 复杂度为 O(n) ；push_back 的复杂度仍为 O(1) ，因为 O(n) 均摊到 n 次 push_back 操作中。
- 动态数组 Vector：删除大量元素，收回空间。可能添加/删除元素操作穿插，导致复杂度无法均摊。策略，只有删除到只剩 1/4 元素时再收回空间。
- 动态栈，动态队列

## 3 数组相关问题

### 3-1 数组中的问题

- 排序，查找，栈，队列，堆
- 二分查找：| < | = | > | 三个区间
  - 限定变量的意义 `[ l...r ]` 前后都包含。并判断是否是一个合法的搜索区间。
  - 为查找到结果，返回 -1；？

### 3-2 程序正确 

- l + r 整型溢出问题

### 3-3 面试问题实战

- 283 移动数组中的 0 值到末尾
  - 存非零元素，重新填充到头部。尾部填0；时间 O(n) , 空间 O(n)
  - 一个指针遍历元素 i，另一个指针 k 指向可以存放非零元素的地址；时间 O(n), 空间 O(1) ；[0...k) 都为非零元素，
  - 非零元素与零元素交换位置，不用在末尾中的元素中进行填0；优化，避免全都是非零元素，致使元素自己交换，策略：判断 i 与 k 是否相等。
- 快速排序
  - 三路快排，有大量重复元素。
  - 随机选取标兵，避免近乎有序。
- 练习题 27 Leetcode 
  - 如何定义删除，
  - 保持相对顺序
  - 空间复杂度要求
- 练习题 26 
  - 对已排序数组元素去重
- 练习题 80
  - 去重，最多保留两个重复的元素
- **特征**：使用一个指针遍历数组，用另一个指针指示当前符合条件的元素的位置，根据遍历结果，调整第二个指针。

### 3-4 基础算法思路的应用

- 75 ：0 1 2 三个数值的数组的排序
  - 各种排序算法
  - 计数排序：统计个数，重新放回。遍历了两遍
    - 注意判断数值是否在有效范围内。
  - 三路快速排序。只遍历一遍
    - 多用断言
- 练习题 88 ：归并有序数组
- 练习题 215 ：寻找第 K 大的元素
- 167 Two sum：找出两个元素和为目标值的索引
  - 没有解，多个解的情况
  - 暴力解法，双层遍历
  - 输入有序：采用二分搜索目标值：O(nlogn)
  - 使用两个指针，初始分别指向开头和末尾，根据和的结果移动指针。叫**对撞指针**。
  - 元素个数大于等于 2 。没有解，可以抛出异常。
- 练习题 125 ：忽略大小写和标点符号，判断字符串是否是回文
  - 空字符串？
- 练习题 344 翻转字符串
- 练习题 345 将字符串中的元音字母反转
- 练习题 11  ，选取两个数，与 x 轴构成容量最大的容器。
- **特点**：首尾各一个指针，不断收缩指针范围进行搜索。

### 3-7 双索引 (滑动窗口)

- 209 最短的连续子数组和大于特定值的子数组长度
  - 是否要求连续；没有解怎么办
  - 暴力解法：遍历所有子数组 [i...j] 时间 O(n^3) ==> 优化? O(n^2)
  - 根双索引：据求和结果动态滑动 i ... j 窗口 时间 O(n)

### 3-8 双索引

- 3 ： 在一个字符串中寻找没有重复字母的最长字串
  - 字符集？大小写
  - 双索引：根据子串中是否有重复子串来调整窗口；记录重复子串，使用一个数组来记录是否出现。

- 练习题 438 ：p 是由 s 的子串字母构成的字符串

- 练习题 76 ：s 中寻找最短的子串包含 T 中所有的字符
  - 什么叫包含所有字符 ？s = 'a'; t = 'aa'

- **特点**：双索引滑动窗口。

- **子串问题**：

  ```c++
  string minWindow(string s, string t) {
          vector<int> map(128,0);
          for(auto c: t) map[c]++;
          int counter=t.size(), begin=0, end=0, d=INT_MAX, head=0;
          while(end<s.size()){
              if(map[s[end++]]-->0) counter--; // 把其他字符的计数变为负数7
              while(counter==0){ //valid
                  if(end-begin<d)  d=end-(head=begin);
                  if(map[s[begin++]]++==0) counter++;  //make it invalid
              }  
          }
          return d==INT_MAX? "":s.substr(head, d);
      }
  ```

  

## 4 查找问题

### 4-1 查找问题

- 可分为两类 1. 查找有无，是否存在元素 ‘a’ 用 set；2. 查找对应关系（键值对），元素 ’a‘ 出现几次，用 map 
- insert find erase change(map)
- 349 求两个数组中的公共元素
  - 使用 set 存结果，查结果 时间复杂度 O(nlogn) 
  - 如何只用一个 set
- 350 求两个数组的交集
  - 重复的元素也需要重复输出。使用 map 记录元素出现次数，
  - map 不存在某个元素时，使用索引访问会自动创建并初始化为 0 ；
  - map.insert(make_pair(a,b));
- 如果数组有序，有什么优化

### 4-3 set map 时间复杂度

- 插入/查找/删除 由二叉平衡树实现 复杂度 O(logn)
- unordered_map/set ，由哈希表实现，失去了数据的顺序性 插入/查找/删除 时间复杂度 O(1)
- 练习题 242 ：字符串改变顺序后变成另一个字符串，判断是否是这种情况
- 练习题 202 ：数值每个位的平方和是否结果为1
- 练习题 290 ：Word Pattern // 提示，使用两个映射
- 练习题 205 ：同构，两个字符串通过字符映射可以相等
  - 字符集；空串；
- 练习题 451 ：按照字母出现的频率倒序重组字符串
- 使用 set map 解决

### 4-4 sum 问题 

- 1 two sum ；数组是无序的；
  - 索引从 0 还是 1 开始
  - 没有解怎么办；多个解怎么办
  - 暴力解法 O(n^2)
  - 排序后使用双索引对撞 O(nlogn)，索引信息会丢失，**怎么处理**
  - 使用查找表，对元素 a 查找 target - a 是否存在，对应的索引是谁， 使用 map
    - 有重复的元素会覆盖前一个值的索引，导致错过两个相等的值相加为target值的情况；策略：放入之前先查 target - a 是否存在。
    - 时间复杂度 O(n) 空间复杂度 O(n)
- 15 3 sum 查找三个数的和为 0 
- 18 4 sum 
- 16 3 sum Closest 三个数的和与 target 最接近的三个数

### 4-5 4 sum II ---454

- 四个数组，各取一个数，和为 0
- 暴力 O(n^4)
- 查找表 O(n^3)
- C+D的每一种可能放入查找表中，空间/时间 复杂度 O(n^2) ，用 map 存和出现的次数
- 由数据规模推算出算法应该有的复杂度
- 练习题 49 ：字符串数组分组，根据出现的字符进行分组

### 4-6 三点，中间点等距 --- 447

- 暴力解法 O(n^3)
- 查找表，到点 i 的同距离的计数 map ， 通过同距离数字的组合数结果相加得到该点作为中心点的结果。（不开根号，保持整数）时间 O(n^2) 空间 O(n)；注意整形相乘溢出问题。
- 练习题 149 ：最多有多少个点在一条直线上；
  - 点坐标范围；点坐标的表示（整数，浮点数？）

## 5 链表

### 5-1 链表

- 206 反转链表：使用三个指针 pre cur next
  - 注意指针是否有效
- 练习题 92 反转链表 2 ：只反转特定范围的节点
  - 注意范围的有效性
- 练习题 83 移除有序链表的重复元素
- 练习题 86 partition list
- 练习题 328 索引为奇数的节点排前面，偶数节点排后面
- 练习题 2 对两个由链表表示的数字进行加法运算
  - 有前置0？负数？
- 练习题 445 add two numbers  顺序存储
  - 不允许修改链表？
- **注意**：链表虽然不能随机存取，但是随意拼接的特性

### 5-3 虚拟头节点

- 203 删除值为 val 的节点 
  - 待删除节点为第一个节点时：设立虚拟头节点，新建一个节点指向头节点，从而不用额外考虑头节点的情况。
  - 删除节点之前，需要先获取该节点的下一个节点然后再删除
- 练习题 82 有序链表重复的元素全部删除
- 练习题 21 两个有序链表的 merge

### 5-4 交换链表的相邻节点

- 24：需要四个指针，两个指针指向一对节点，其他两个指针分别指向前后两个指针，类似反转链表，pre cur1 cur2 next。
  - 引入虚拟头节点
- 练习题 25 k 个节点为一组进行反转
- 练习题 147 在链表上进行插入排序

### 5-5 删除链表中的某个节点

- 只传递了待删除的节点；通过移动后续节点的值实现
  - 若为最后一个节点，需要将节点设为 NULL

### 5-6 双指针

- 19 删除倒数第 n 个节点
  - n 从 0 还是 1 计 ； n 是否合法
  - 删除节点的操作都可以加入虚拟头节点
  - 解法 1 先遍历得到长度，再删除
  - 解法 2 两个指针，前面的指针先移动 n 次，后面两个指针一起移动，然后删除节点
- 练习题 61 循环旋转列表 k 位
- 练习题 143 重新组织链表
  - 如何获得中间的元素：两次遍历，一次遍历？
- 练习题 234 判断是否是回文链表

## 6 栈/队列

### 6-1 栈/队列

- 20 括号匹配是否合法
  - 使用栈解决问题，根据括号的方向来决定是入栈，还是和栈顶元素进行匹配
  - 栈顶元素反应了最近的需要匹配的元素
  - 在嵌套的关系中，通过栈来得到最近的需要匹配的元素
- 练习题 150 求逆波兰表达式的值
- 练习题 71 简化路径
  - 是否合法；不能回退的情况；冗余的 /

### 6-2 栈和递归

- 144 94 145 二叉树的遍历
- 用栈实现非递归遍历

```c++
// 前序
vector<int> preorderTraversal(TreeNode* root) {
    vector<int> res;
    if(root == NULL)
        return res;
    stack<TreeNode*> s;
    s.push(root);
    while(!s.empty()) {
        TreeNode *n = s.top();
        s.pop();
        res.push_back(n->val);
        if(n->right) s.push(n->right);
        if(n->left) s.push(n->left);
    }
    return res;
}
// 后序
vector<int> postorderTraversal(TreeNode* root) {
    vector<int> res;
    if(root == NULL)
        return res;
    stack<TreeNode*> s;
    s.push(root);        
    while(!s.empty()) {
        TreeNode *n = s.top();
        s.pop();
        res.insert(res.begin(), n->val);
        if(n->left) s.push(n->left);
        if(n->right) s.push(n->right);
    }
    return res;
}
// 中序
vector<int> inorderTraversal(TreeNode* root) {
    stack<TreeNode*> s;
    vector<int> res;
    if(root == NULL)
        return res;
    s.push(root);
    TreeNode * n = root->left;
    while(!s.empty() || n) {
        while(n) {
            s.push(n);
            n = n->left;
        }
        n = s.top();
        res.push_back(n->val);
        s.pop();
        n = n->right;
    }
    return res;
}
```

- 练习题 341 平铺嵌套的数组

### 6-4 队列/广度优先遍历

- 102 二叉树的层序遍历
- 练习题 107 从底层向上的逐层遍历
- 练习题 103 之字形逐层遍历
- 练习题 199 返回右侧能看到的节点

### 6-5 BFS / 无权图最短路径

- 279 寻找最少的完全平方数，使和为 n
  - 肯定有解
  - 转换为图论问题，n个节点，若与其他数字相差一个完全平方数，则连接
  - 利用广度优先遍历进行搜索最短路径
  - 会有大量的节点重复访问，可以通过一个数组记录是否访问过
- 练习题 127 从一个单词变换到另一个单词的最短路径
- 练习题 126 同 127 输出所有最短路径

### 6-6 优先队列

- 利用堆实现；**需要手撕**
- C++ ：priority_queue 最大堆
- 347 返回前 k 个出现频率最高的元素
  - 注意 k 的合法性
  - 扫描统计并排序 O(nlogn)
  - 扫描统计并维护优先队列存储前 k 个频率最高的元素 O(nlogk)
  - 可以 O(nlog(n-k))
- 练习题 23 ：归并 k 个有序数组

## 7 二叉树/递归

### 7-1 二叉树/递归

- 终止条件
- 递归过程
- 104 二叉树最高深度
- 练习题 111 求二叉树的最低深度
- 226 反转一颗二叉树
- 练习题 100 判断二叉树是否相等
- 练习题 101 判断二叉树是否左右对称
- 练习题 222 求完全二叉树的节点个数
- 练习题 110 判断是否为平衡二叉树

### 7-3 递归终止条件

- 112 从根到叶子节点路径的和为 sum
  - 不一定是叶子节点
- 练习题 111 二叉树最低深度
- 练习题 404 左叶子节点之和

### 7-4 复杂递归

- 257 返回从根节点到叶子节点路径的字符串
- 练习题 113 返回和为 sum 的所有路径
- 练习题 129 每个路径表示一个数，求其和
- 437 路径和为 sum ，不要求路径的起始/终止节点
  - 分类讨论，是否包含当前节点递归调用

### 7-6 二叉搜索树

- insert/find/ delete /min /max/ ...
- 235 两个节点在一颗二分搜索树中的最近公共祖先
- 练习题 98 验证是否是二分搜索树
- 练习题 450 二分搜索树删除一个节点
- 练习题 108 有序数组转换为平衡的二分搜索树
- 练习题 230 在二分搜索树中寻找第 k 小元素
- 练习题 236 二叉树中寻找两个节点的最近公共祖先

## 8 递归/回溯

### 8-1 递归与回溯/树形问题

- 17 数字字符串对应字符集的所有字母组合
  - 树形问题 复杂度 3^n = O(2^n) 
- 练习题 93 给一个数字字符串，加三个点，返回所有合法 IP
- 练习题 131 将一个字符串拆分成回文字符串
- 应用：排列 
- 46 返回元素的排列
- 练习题 47 可能有相同元素的全排列
- 应用： 组合
- 77 1-n 的 n 个数字，选出 k 个数字的组合
  - 回溯
  - 优化：剪枝，不必要的递归树枝
- 练习题 39 组合元素和为 T ，元素可以使用多次
- 练习题 40 组合元素和为 T ，元素可能相同，只能使用一次
- 练习题 216 
- 练习题 78 集合的所有子集
- 练习题 90 元素可能相同的集合的子集
- 练习题 401 二进制时间表，给出 n 个灯亮的情况可以表示的所有时间

### 8-6 二维平面的回溯

- 79 二维平面的字母数组是否能有一个路径组成特定单词
  - 偏移量数组
- floodfill 算法
  - 深度优先遍历
  - 200 判断二维数组表示的地图有几个岛屿
  - 通过深度优先进行标记
- 练习题 130 找到被 x 包围的 o 将其反转成 x
- 练习题 417 二维数组中可以同时流向两个角的水位

### 8-8 回溯/传统人工智能

- 51 N皇后 n 个皇后放在 n*n 棋盘中，横/竖/对角线不会同时出现两个皇后
  - 每一行都有一个皇后，递归/回溯放置每一行的皇后
  - 注意剪枝，如何判断？同列/两个方向的对角线（相减/相加为常数）没有其他皇后
- 练习题 优化思路
- 练习题 52 求 n 皇后 所有解的个数
- 练习题 37 数独求解

## 9 动态规划

### 9-1 动态规划

- 斐波那契数列
  - 递归 复杂度 指数级
  - 避免重复运算（重复子问题） 使用数组存储计算结果 复杂度 O(n)
  - **记忆化搜索-自上而下解决 ---》递归**
  - **使用循环， 自下而上解决 ---》动态规划**
- 拆解为子问题，同时保存子问题答案，子问题答案只求解一次
- 70 爬楼梯的爬法 一个/两个台阶 
- 练习题 120 三角形数组，自顶向下的和最小的路径 // 自底向上
- 练习题 64 二维矩阵，求左上角到右下角的路径，路径和最小

### 9-3 分割整数

- 343 分割整数为多个数的和，使其乘积最大
  - 递归，暴力 O(2^n)
  - 存储重复子问题的结果
  - 最优子结构：由子问题的最优解能得到问题的最优解
  - 记忆化搜索/动态规划 O(n^2)
- 练习题 279 寻找最少的完全平方数的和为 n 
- 练习题 91 数值与字母对应，给定数值有多少中有解析方法
- 练习题 62 二维数组路径数
- 练习题 63 二维数组有障碍物，求路径数

### 9-4 house robber 

- 198 house robber 不能偷临近的房子，最多偷多少
  - 暴力解法 O((2^n)n) 
  - 每个房子可偷可不偷
  - 记忆化搜索/动态规划
  - 状态的定义：（函数的定义/含义）
  - 状态转移：函数怎么做 
  - 练习题 使用新的状态定义
- 练习题 213 house robber II 环形街道
- 练习题 337 house robber III 小区是二叉树结构
- 练习题 309 给定股票的价格趋势，如何买卖才能使利润最大

### 9-5 背包

- 0-1背包 
  - 暴力解法 O((2^n)n) 遍历 2^n 种方案并以 n 判断是否有效解
  - 两个约束 n 个物品， 容量 c ；--》状态 f(n, c)
  - 递归-》记忆化搜索-》动态规划 
  - 时间/空间复杂度 O(n*c)
- 优化：
  - 保持 2 行的元素
  - 只使用 1 行
- 完全背包，物品无限使用
- 多重背包，物品有数个
- 多维费用背包
- 物品互相排斥/依赖

### 9-7 背包问题变样

- 416 数组分为两组数，和相等
  - 填满 sum/2 的背包
  - 时间复杂度 O(n*sum) 存 True or false
- 练习题 322 不同面值的硬币，能否凑成指定金额，可无限使用
- 练习题 377 无重复的整型数组，可重复使用，有多少中可能能凑出制定数字
  - 顺序相关？
- 练习题 474 组合 0 1 串
  - 输入数据的约束对算法的要求
- 练习题 139 字符串数组和字符串，能否以字符串的字符串成给定字符串
- 练习题 494 数字序列给其分配正负号，使其和为给定数值，有多少种可能

### 9-8 最长上升子序列

- 300 最长上升子序列的长度
  - 需要连续？绝对上升？
  - 暴力 ：所有子序列，每个元素可放可不放 O((2^n)n)
  - 定义状态 
  - 如何得到最后长度值？如何得到序列？
  - 可以为 O(nlogn) 
- 练习题 376 最长的一升一降的子序列

### 9-9 最长公共子序列

- 两个字符串的公共子序列 （基因）
  - 状态：两个字符串都有一个变量
- dijkstra 单源最短路径 --》 动态规划
- 给出具体的解
  - 300 LIS 多个解 数组回溯
  - 0-1 背包 需要保留背包过程
- 动态规划

## 10 贪心算法

### 10-1 贪心

- 455 分配饼干
  - 策略：最大的饼干给最贪心的小朋友
  - 一般需要排序 复杂度 O(nlogn)
- 练习题 392 两个字符串，判读是否是子序列

### 10-2 贪心与动态规划

- 435 一组区间，最少删除多少区间使之不相重叠
  - 暴力 找出所有组合 O((2^n)n)
  - 按起始点进行排序
  - 动态规划---》最长上升子序列 O(n^2)
  - 贪心---》按结尾进行排序，每次选择结尾最早的区间 O(n)
- 贪心选择性质
  - 如果无法使用贪心算法，指出反例即可
  - 使用反证法证明
- 最小生成树
- 最短路径

LRU 算法，Tier 树，字符串子串匹配，回文

## 11  智力题

### 11-1 过河

- 一家五口过河分别需要 1 3 6 8 12 秒，一次最多两个人同时过桥，并且需要灯，灯 30s 后灭，如何在灯灭之前全部过河。

  ```
  过       回
  1，3     1    4s
  8，12    3    15s
  1，6     1    7s
  1，3          3s
  共 29s
  ```

### 11-2 5L 6L 得 3L

- 两个瓶子容量分别为 5L 和 6L，如何得到 3L 的水

  ```
  1. 6L 盛满，并用 6L 的水倒满 5L 的瓶子，6L 的瓶子剩 1L 的水，将 5L 的水倒空，导入 6L 瓶子中的 1L 水。
  2. 再重复步骤 1 两遍，能得到 3L 的水。
  ```

### 11-3 两种药混一起

- 两种药各 x 片，混一起无法区分，每天需要各吃一片。

  ```
  方法 1：将每个药片分为 x 份，每天每个药片都吃一份。
  方法 2：将所有药片捣碎，分为 x 份，每天吃一份。
  ```

### 11-4 药丸单次检测

- 有 20 瓶药丸，其中 19 瓶中的药丸重 1 克，余下一瓶药丸重 1.1 克，如何只使用一次称重天平找到比较重的那瓶药丸。

  ```
  对每瓶药丸分别编号 1 ~ 20，从每瓶药丸中分别取出对应编号数目的药丸，将取出的所有药丸一起称重，得到总重，即可算出较重那瓶药丸的编号。如所有药丸都是 1 克，则总重为 (1+20)*20/2 = 210，若称出总重为 211.3，则编号 13 为较重的那瓶药丸。
  ```

  