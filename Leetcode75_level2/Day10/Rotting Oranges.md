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
