# 3Sum Closest
- ## Question:
>Given an integer array nums of length n and an integer target, find three integers in nums such that the sum is closest to target.
>
>Return the sum of the three integers.
>
>You may assume that each input would have exactly one solution.



- Example :

      Input: nums = [-1,2,1,-4], target = 1
      Output: 2
      Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).


- ## Solution:
```cpp
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) 
    {
        sort(nums.begin(),nums.end());
        int diff=INT_MAX;
        int ans;
        for(int i=0;i<nums.size();i++)
        {
            int lo=0;
            int hi=nums.size()-1;
            while(hi>lo)
            {
                if(hi==i)
                {
                    hi--;
                    continue;
                }
                if(lo==i)
                {
                    lo++;
                    continue;
                }
                int sum=nums[i]+nums[hi]+nums[lo];
                if(abs(sum-target)<diff)
                {
                    ans=sum;
                    diff=min(diff,abs(sum-target));
                }
                if(sum>target)
                hi--;
                else 
                lo++;
            }
        }
        return ans;
        
    }
};
```
