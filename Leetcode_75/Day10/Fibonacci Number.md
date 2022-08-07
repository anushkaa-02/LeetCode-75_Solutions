# Fibonacci Number
- ## Question:
>The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from >0 and 1.
- F(0) = 0, F(1) = 1
- F(n) = F(n - 1) + F(n - 2), for n > 1.
>Given n, calculate F(n).

- Example :

      Input: n = 3
      Output: 2
      Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.
      

- ## Solution:
```cpp
class Solution {
public:
    int fib(int n) {
        if(n<=1) return n;
        int prev2 = 0, prev1 = 1, cur;
        for(int i=2;i<=n;i++){
            cur = prev1+prev2;
            prev2 = prev1;
            prev1 = cur;
        }
        return cur;
    }
};
```

## Tags
`Math` `DP`
