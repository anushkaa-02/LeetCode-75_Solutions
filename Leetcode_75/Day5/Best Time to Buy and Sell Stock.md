# Best Time to Buy and Sell Stock
- ## Question:
>You are given an array prices where prices[i] is the price of a given stock on the ith day.
>
>You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.
>
>Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

- Example :

      Input: prices = [7,1,5,3,6,4]
      Output: 5
      Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
      Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
      

- ## Solution:
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int profit_max = 0;
        int b_ptr = 0;
        int s_ptr = 1;
        
        while (s_ptr < prices.size()) {
            if (prices[s_ptr] < prices[b_ptr]) 
                b_ptr = s_ptr;
            
            else if (prices[s_ptr] - prices[b_ptr] > profit_max) 
                profit_max = prices[s_ptr] - prices[b_ptr];
            
            s_ptr++;
        }
        return profit_max;
    }
};
```

## Tags
`Array` `Dynamic Programming`
