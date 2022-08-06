# Flood Fill
- ## Question:
>An image is represented by an m x n integer grid image where image[i][j] represents the pixel value of the image.
>
>You are also given three integers sr, sc, and color. You should perform a flood fill on the image starting from the pixel image[sr][sc].
>
>To perform a flood fill, consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with color.
>
>Return the modified image after performing the flood fill

- Example :

      Input: image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, color = 0
      Output: [[0,0,0],[0,0,0]]
      Explanation: The starting pixel is already colored 0, so no changes are made to the image.
      
- ## Solution:
```cpp
class Solution {
public:
    void dfs(int i,int j,int initialColor,int newColor,vector<vector<int>>& image)
    {
        int n=image.size();
        int m=image[0].size();
        
        if(i<0 or j<0) return;
        if(i>=n or j>=m) return;
        
        if(image[i][j]!=initialColor) return;
        
        image[i][j]=newColor;
        
        dfs(i-1,j,initialColor,newColor,image);
        dfs(i+1,j,initialColor,newColor,image);
        dfs(i,j-1,initialColor,newColor,image);
        dfs(i,j+1,initialColor,newColor,image);

    }
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int newcolor) {
        int initialColor=image[sr][sc];
        if(initialColor!=newcolor)
            dfs(sr,sc,initialColor,newcolor,image);
        return image;
    }
};
```
## Tags
`Array` `DFS`
