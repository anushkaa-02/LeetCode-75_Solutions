# Spiral Matrix
- ## Question:
>Given an m x n matrix, return all elements of the matrix in spiral order.

- Example :

      Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
      Output: [1,2,3,6,9,8,7,4,5]



- ## Solution:
```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        int m = matrix.size() ;
        int n = matrix[0].size() ;
        
        int nums = m*n ; 
        int hs = 0;      
        int he = n-1 ;   
        int vs = 0 ;     
        int ve = m-1 ;  
        int i = 0 ;
        int j = 0 ;
        vector<int> ans ;
        while(nums){
            vs++ ;
            while(nums && j <= he){
                ans.push_back(matrix[i][j++]) ;
                nums-- ;
            }
            j-- ;
            i++ ;
            he--;
            while(nums && i <= ve){
                ans.push_back(matrix[i++][j]) ;
                nums-- ;
            }
            i-- ;
            j-- ;
            ve-- ;
            while(nums && j >= hs){
                ans.push_back(matrix[i][j--]) ;
                nums-- ;
            }
            j++;
            i--;
            hs++ ;
            while(nums && i >= vs){
                ans.push_back(matrix[i--][j]) ;
                nums-- ;
            }
            i++;
            j++;
        }
        return ans ;
    }
};
