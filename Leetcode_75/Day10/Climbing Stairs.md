# Climbing Stairs
- ## Question:
>You are climbing a staircase. It takes n steps to reach the top.
>
>Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

- Example :

      Input: n = 2
      Output: 2
      Explanation: There are two ways to climb to the top.
      1. 1 step + 1 step
      2. 2 steps
      
- ## Solution:
```cpp
class Solution {
public:
    int climbStairs(int n) {
        if(n<=2)
            return n;
        
        int dp[]={0,1,2};    
        for(int i=3;i<=n;i++)
        { 
            dp[(i)%3]=dp[(i+1)%3]+dp[(i+2)%3];
        }
        return dp[n%3];
    }
};
```

