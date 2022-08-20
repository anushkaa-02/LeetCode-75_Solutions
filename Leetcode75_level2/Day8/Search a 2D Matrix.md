# Search a 2D Matrix
- ## Question:
>Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:
>
- Integers in each row are sorted from left to right.
- The first integer of each row is greater than the last integer of the previous row.

- Example :

      Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
      Output: true
      
 
- ## Solution:
```cpp
class Solution {
public:
    bool searchMatrix(const vector<vector<int>>& matrix, int target) {
        const auto linear = makeLinear(matrix);
        return std::binary_search(linear.begin(), linear.end(), target);
    }
private:
   std::vector<int> makeLinear(const std::vector<std::vector<int>> & input)
   {
    std::vector<int> result{};
    result.reserve(input[0].size() * input.size());
    for (const auto& row : input)
    {
        for (const auto& element : row)
        {
            result.emplace_back(element);
        }
    }
    return result;
   }
};
```

##
