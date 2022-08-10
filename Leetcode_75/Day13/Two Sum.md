# Two Sum
- ## Question:
>Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
>
>You may assume that each input would have exactly one solution, and you may not use the same element twice.
>
>You can return the answer in any order.

- Example :

      Input: nums = [2,7,11,15], target = 9
      Output: [0,1]
      Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

- ## Solution:
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int,int> m;
        vector<int> v;
        for(int i=0;i<nums.size();i++)
        {
            if(m.find(target-nums[i])!=m.end())
            {
                v.push_back(m[target-nums[i]]);
                v.push_back(i);
                return v;
            }
            m[nums[i]]=i;
        }
        return v;
    }
};
```
