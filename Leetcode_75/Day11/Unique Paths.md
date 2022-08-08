# Unique Paths
- ## Question:
>There is a robot on an m x n grid. The robot is initially located at the top-left corner (i.e., grid[0][0]). The robot tries to move to the bottom-right corner (i.e., >grid[m - 1][n - 1]). The robot can only move either down or right at any point in time.
>
>Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner.
>
>The test cases are generated so that the answer will be less than or equal to 2 * 109.

- Example :

      Input: m = 3, n = 2
      Output: 3
      Explanation: From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
      1. Right -> Down -> Down
      2. Down -> Down -> Right
      3. Down -> Right -> Down

- ## Solution:
```cpp
class Solution {
public:
    int solve(int i, int j, vector<vector<int>> &dp, int& m, int& n) {
        if(i == m-1 || j == n-1) return 1;
        if(dp[i][j] != 0)return dp[i][j];
        
        dp[i][j] = solve(i+1, j, dp, m, n) + solve(i, j+1, dp, m, n);
        return dp[i][j];
    }
    int uniquePaths(int m, int n) {
        vector<vector<int>> dp(m , vector<int>(n , 0));
        return solve(0, 0, dp, m, n);
    }
};
```

## Tags
`Array` `Dynamic Programming`
