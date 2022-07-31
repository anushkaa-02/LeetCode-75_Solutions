# Running Sum of 1D array
- ## Question:
>Given an array nums. We define a running sum of an array as runningSum[i] = sum(nums[0]…nums[i]).
>
>Return the running sum of nums.

- Example :

      Input: nums = [1,2,3,4]
      Output: [1,3,6,10]
      Explanation: Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].
      
- ## Solution:
```cpp
class Solution {
public:
    vector<int> runningSum(vector<int>& nums) {
        for(int i=1;i<nums.size();i++) nums[i]+=nums[i-1];
        return nums;
    }
};
```

## Tags

`Array` `Prefix Sum`
