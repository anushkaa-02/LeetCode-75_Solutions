# Maximum Product Subarray
- ## Question:
>Given an integer array nums, find a contiguous non-empty subarray within the array that has the largest product, and return the product.
>
>The test cases are generated so that the answer will fit in a 32-bit integer.
>
>A subarray is a contiguous subsequence of the array.


- Example :

      Input: nums = [2,3,-2,4]
      Output: 6
      Explanation: [2,3] has the largest product 6.

- ## Solution:
```cpp
class Solution {
public:
    int maxProduct(vector<int>& a) {
        int choice1,choice2;
        int maxm=a[0],minm=a[0],ans=a[0];
        for(int i=1;i<a.size();i++){
            choice1=minm*a[i];
            choice2=maxm*a[i];
            maxm=max(a[i],max(choice1,choice2));
            minm=min(a[i],min(choice1,choice2));
            ans=max(maxm,ans);
        }
        return ans;
    }
};
```
