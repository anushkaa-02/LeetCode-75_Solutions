# Number of Islands
- ## Question:
>Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.
>
>An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

- Example :

      Input: grid = [
        ["1","1","1","1","0"],
        ["1","1","0","1","0"],
        ["1","1","0","0","0"],
        ["0","0","0","0","0"]
      ]
      Output: 1
      
- ## Solution:
```cpp
class Solution{
public:
int numIslands(vector<vector<char>>& grid) {
        int count=0, i, j, r=grid.size(), c=grid[0].size();
        for(i=0; i<r; i++) {
            for(j=0; j<c; j++) {
                if(grid[i][j]=='1') {
                    help(grid, i, j);
                    count++;
                }
            }
        }
        return count;
    }
    void help(vector<vector<char>>& grid, int i, int j) {
        if(i<0 || j<0 || i>=grid.size() || j>=grid[0].size())
            return;
        if(grid[i][j]=='0')
            return;
        grid[i][j]='0';
        help(grid, i+1, j);
        help(grid, i-1, j);
        help(grid, i, j+1);
        help(grid, i, j-1);
    }
};
```

## Tags
