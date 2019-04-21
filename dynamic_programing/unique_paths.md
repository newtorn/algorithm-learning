不同的路径 Unique Paths
===

问题描述
---
>有一个机器人的位于一个 m × n 个网格左上角。机器人每一时刻只能向下或者向右移动一步。机器人试图达到网格的右下角。问有多少条不同的路径？(**`n和m均不超过100`**)

确定状态
---
+ 最后一步
   - 设定左上角第一个格子的坐标为(0, 0)，则最后一个格子的坐标为(m-1, n-1)
   - 最后一步到达坐标为(m-1, n-1)的格子来自哪些格子(坐标)
   - 机器人只能向下或向右移动一步，则有如下集合
   - {(m-1-1, n-1), (m-1, n-1-1)} => (m-1, n-1)
+ 子问题
   - dp[i][j]表示到达坐标(i, j)位置的所有不同路径
   - 那么达到右下角最后一个坐标(m-1, n-1)可用dp表示
   - dp[m-1][n-1] = dp[m-1-1][n-1] + dp[m-1][n-1-1]
   - 那么达到某一格的问题都可以抽象成与到达最后一格的问题
   - 达到每个格子的路径等同于到达这个格子左边的格子的路径与达到这个格子上边的格子的路径的和

转移方程
---
   - dp[i][j] = dp[i-1][j] + dp[i][j-1]

初始条件和边界情况
---
   - 初始条件：
      + dp[0][0] = 1 (第一格只有1种)
      + dp[0][1...n-1] = 1 (第一行的格子只能来自左边的格子)
      + dp[1...n-1][0] = 1 (第一列的格子只能来自上边的格子)
   - 边界越界
      + 网格规模`m x n`表示`m`行`n`列
      + 横坐标不能超过`n-1`
      + 纵坐标不能超过`m-1`

计算顺序
---
   - 假定从左到右从上到下
   - dp[0][0], dp[0][1], dp[0][2]...dp[0][n-1]
   - ...
   - dp[m-1][0], dp[m-1][1], ..., dp[m-1][n-1]

代码
---
```cpp
class Solution {

public:
    /**
     * @param m: positive integer (1 <= m <= 100)
     * @param n: positive integer (1 <= n <= 100)
     * @return: An integer
     */
    int uniquePaths(int m, int n) {

        // define status array
        vector< vector<int> > dp(m, vector<int>(n));
        
        // initialization
        for (int i = 0; i < n; ++i) dp[0][i] = 1;
        for (int j = 0; j < m; ++j) dp[j][0] = 1;

        // traverse
        for (int i = 1; i < m; ++i) {
            for (int j = 1; j < n; ++j) {
                dp[i][j] = dp[i][j-1] + dp[i-1][j];
            }
        }
        
        //return result
        return dp[m-1][n-1];
    }

};
```
