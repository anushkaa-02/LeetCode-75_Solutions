# Search in Rotated Sorted Array
- ## Question:
>There is an integer array nums sorted in ascending order (with distinct values).
>
>Prior to being passed to your function, nums is possibly rotated at an unknown pivot index k (1 <= k < nums.length) such that the resulting array is [nums[k], >nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,5,6,7] might be rotated at pivot index 3 and become [4,5,6,7,0,1,2].
>
>Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums.
>
>You must write an algorithm with O(log n) runtime complexity.


- Example :

          Input: nums = [4,5,6,7,0,1,2], target = 3
          Output: -1

- ## Solution:
```cpp
class Solution {
public:
     int search(vector<int>& nums, int target) {
        int b = 0;
        int l = nums.size()-1;
        return Helper(nums, target, b,l);
    }
     int Helper(vector<int>& nums, int target,int i,int j){
        int mid = (i+j)/2;
        if(i>j){
            return -1;
        }
        if(nums[mid]==target){
           return mid;
        }
        if(nums[i]<=nums[mid]){
            if(target>=nums[i] and target<=nums[mid]){
                return Helper(nums,target,i,mid-1);
            }
            else{
               return  Helper(nums,target,mid+1,j);
            }
        }
        if(target>nums[mid] and target<=nums[j]){
           return Helper(nums,target,mid+1,j);
        }
        return   Helper(nums,target,i,mid);
    }
};
```
## Tags
`Array` `Binary Search`
