动态规划(Dynamic Programing)
===

思想(Thought)
---
>动态规划算法通常用于求解具有某种最优性质的问题。在这类问题中，可能会有许多可行解。每一个解都对应于一个值，我们希望找到具有最优值的解。动态规划算法与分治法类似，其基本思想也是将待求解问题分解成若干个子问题，先求解子问题，然后从这些子问题的解得到原问题的解。与分治法不同的是，适合于用动态规划求解的问题，经分解得到子问题往往不是互相独立的。若用分治法来解这类问题，则分解得到的子问题数目太多，有些子问题被重复计算了很多次。如果我们能够保存已解决的子问题的答案，而在需要时再找出已求得的答案，这样就可以避免大量的重复计算，节省时间。我们可以用一个表来记录所有已解的子问题的答案。不管该子问题以后是否被用到，只要它被计算过，就将其结果填入表中。这就是动态规划法的基本思路。具体的动态规划算法多种多样，但它们具有相同的填表格式。

适用条件(Application Condition)
---
+ 最优化原理(最优子结构性质)
+ 无后效性
+ 子问题的重叠性

组成部分(Component)
---
+ 确定状态(Sure Status)
   - 状态在动态规划的作用属于定海神针
   - 简单滴说，解动态规划的时候需要开一个数组，数组的每一个元素arr[i]或者arr[i][j]代表什么
   - 确定状态需要两个意识
      + 研究最优策略的最后一步
      + 将问题转化成子问题
+ 转移方程(Transition Equation)
   - 根据子问题直接定义得到
+ 初始条件和边界情况(Initialization and Boundary)
   - 初始条件：转移方程算不出来的，需要手工定义
   - 边界越界：下标不能超过数组的长度和低于0
+ 计算顺序(Calculation Order)
   - 利用之前的计算结果计算当前状态
   - 从小到大计算，那么大的应该提前计算出来了
   - 同理从大到小，那么小的应该提前计算出来了

常见动态规划类型(Type)
---
+ 坐标型(20%)
+ 序列型(20%)
+ 划分型(20%)
+ 区间型(15%)
+ 背包型(10%)
+ 最长序列型(5%)
+ 博弈型(5%)
+ 综合型(5%)

特点及其实例(Feature)
---
+ 计数(Count)
   - 有多少种走到右下角
      + 实例: [Unique Paths](./unique_paths.md) => [LintCode-114](https://www.lintcode.com/problem/unique-paths/)
   - 有多少种方法选出k个数使得和是Sum
      + 实例: [Coin Change](./coin_change.md) => [LintCode-669](https://www.lintcode.com/problem/coin-change)
   - 题目列表
      + ...
      + ...
+ 求最大最小值(Maximum or Minimum value)
   - 从数组中选出k个连续的数使得乘积最大
      + 实例: [Maximum Product Subarray](./maximum_product_subarray.md) => [LintCode-191](https://www.lintcode.com/problem/maximum-product-subarray)
   - 最长上升子序列长度
      + 实例: [Longest Increasing Subsequence](./longest_increasing_subsequence.md) => [LintCode-76](https://www.lintcode.com/problem/longest-increasing-subsequence)
   - 题目列表
      + ...
      + ...
+ 求存在性(Existence)
   - 跳跃游戏,判断你是否能到达数组的最后一个位置。
      + 实例: [Jump Game](./jump_game.md) => [LintCode-116](https://www.lintcode.com/problem/jump-game)
   - 能不能选出k个数使得和是sum
      + 实例: [K Sum](./k_sum.md) => [LintCode-89]()
   - 题目列表
      + [Jump Game II](https://www.lintcode.com/problem/jump-game-ii)
      + ...

动态规划打印路径(Output Path)
---

动态规划时间空间优化(Optimization)
---
+ FollowUp