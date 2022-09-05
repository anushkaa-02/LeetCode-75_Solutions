# Rotting Oranges
- ## Question:
>You are given an m x n grid where each cell can have one of three values:
>
>0 representing an empty cell,
>1 representing a fresh orange, or
>2 representing a rotten orange.
>Every minute, any fresh orange that is 4-directionally adjacent to a rotten orange becomes rotten.
>
>Return the minimum number of minutes that must elapse until no cell has a fresh orange. If this is impossible, return -1.

- Example :

      Input: grid = [[2,1,1],[0,1,1],[1,0,1]]
      Output: -1
      Explanation: The orange in the bottom left corner (row 2, column 0) is never rotten, because rotting only happens 4-directionally.

- ## Solution:
```cpp
struct Pos {
    int x;
    int y;
    Pos(int x=0, int y=0): x(x), y(y) {}
};

class Solution {
    int m, n; 
public:
    int orangesRotting(vector<vector<int>>& grid) {
        m = grid.size(), n = grid[0].size();
        int freshOrange = 0;
        queue<Pos> que;
        
        for(int y=0; y<m; y++) {
            for(int x=0; x<n; x++) {
                if(grid[y][x]==1) ++freshOrange;
                else if(grid[y][x]==2) que.push({x,y});
            }
        }
        int time = bfs(grid, que, freshOrange);
        return time;
    }
    
    int bfs(vector<vector<int>>& grid, queue<Pos>& que, int freshOrange) {
        int time=0;
        vector<Pos> directions = {{1,0}, {-1,0}, {0,1}, {0,-1}};
        while(!que.empty()) {
            int len = que.size();
            for(int i=0; i<len; i++) {
                int r = que.front().y, c = que.front().x; que.pop();
                for(auto d : directions) {
                    int x = c + d.x,  y = r + d.y; 
                    if(x<0 || y<0 || x>=n || y>=m || grid[y][x] != 1) continue;
                    grid[y][x] = 2;
                    --freshOrange;
                    que.push({x,y});
                }
            }
            if(que.size()!=0) ++time;
        }
       
        return (freshOrange == 0) ? time : -1;
    }
};
```
