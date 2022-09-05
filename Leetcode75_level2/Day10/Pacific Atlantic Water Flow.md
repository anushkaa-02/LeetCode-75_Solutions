# Pacific Atlantic Water Flow
- ## Question:
>There is an m x n rectangular island that borders both the Pacific Ocean and Atlantic Ocean. The Pacific Ocean touches the island's left and top edges, and the >Atlantic Ocean touches the island's right and bottom edges.
>
>The island is partitioned into a grid of square cells. You are given an m x n integer matrix heights where heights[r][c] represents the height above sea level of the >cell at coordinate (r, c).
>
>The island receives a lot of rain, and the rain water can flow to neighboring cells directly north, south, east, and west if the neighboring cell's height is less >than or equal to the current cell's height. Water can flow from any cell adjacent to an ocean into the ocean.
>
>Return a 2D list of grid coordinates result where result[i] = [ri, ci] denotes that rain water can flow from cell (ri, ci) to both the Pacific and Atlantic oceans.

- Example :

      Input: heights = [[1,2,2,3,5],[3,2,3,4,4],[2,4,5,3,1],[6,7,1,4,5],[5,1,1,2,4]]
      Output: [[0,4],[1,3],[1,4],[2,2],[3,0],[3,1],[4,0]]
      Explanation: The following cells can flow to the Pacific and Atlantic oceans, as shown below:
      [0,4]: [0,4] -> Pacific Ocean 
             [0,4] -> Atlantic Ocean
      [1,3]: [1,3] -> [0,3] -> Pacific Ocean 
             [1,3] -> [1,4] -> Atlantic Ocean
      [1,4]: [1,4] -> [1,3] -> [0,3] -> Pacific Ocean 
             [1,4] -> Atlantic Ocean
      [2,2]: [2,2] -> [1,2] -> [0,2] -> Pacific Ocean 
             [2,2] -> [2,3] -> [2,4] -> Atlantic Ocean
      [3,0]: [3,0] -> Pacific Ocean 
             [3,0] -> [4,0] -> Atlantic Ocean
      [3,1]: [3,1] -> [3,0] -> Pacific Ocean 
             [3,1] -> [4,1] -> Atlantic Ocean
      [4,0]: [4,0] -> Pacific Ocean 
             [4,0] -> Atlantic Ocean
      Note that there are other possible paths for these cells to flow to the Pacific and Atlantic oceans.
      
- ## Solution:
```cpp
class Solution {
    void bfs(vector<vector<int>>& heights, vector<vector<bool>>& ocean, int sr, int sc){
        int horizontal[] = {-1, 0, 1, 0};
        int vertical[] = {0, 1, 0, -1};
        int m = heights.size();
        int n = heights[0].size();
        queue<pair<int, int>> q;
        for(int i=0; i<m; i++){
            q.push({i, sr});
            ocean[i][sr] = true;
        }
        for(int i=0; i<n; i++){
            if (!ocean[sc][i]){
                q.push({sc, i});
                ocean[sc][i] = true;
            }
        }
        while(!q.empty()){
            pair<int, int> curr = q.front();
            q.pop();
            int curR = curr.first;
            int curC = curr.second;
            for(int i=0; i<4; i++){
                int r = curR + horizontal[i];
                int c = curC + vertical[i];
                if (r>= 0 && r<m && c>=0 && c<n && !ocean[r][c] && heights[curR][curC] <= heights[r][c]){
                    ocean[r][c] = true;
                    q.push({r, c});
                }
            }
        }
    }
public:
    vector<vector<int>> pacificAtlantic(vector<vector<int>>& heights) {
        int m = heights.size();
        int n = heights[0].size();
        vector<vector<int>> output;
        if (m == 1 && n == 1){
            output.push_back({0, 0});
            return output;
        }
        vector<vector<bool>> pacific(m, vector<bool>(n, false));
        bfs(heights, pacific, 0, 0);
        vector<vector<bool>> atlantic(m, vector<bool>(n, false));
        bfs(heights, atlantic, n-1, m-1);
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if (pacific[i][j] && atlantic[i][j]){
                    output.push_back({i, j});
                }
            }
        }
        return output;
    }
};
```
