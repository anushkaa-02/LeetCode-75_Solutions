# Path Sum III
- ## Question:
>Given the root of a binary tree and an integer targetSum, return the number of paths where the sum of the values along the path equals targetSum.
>
>The path does not need to start or end at the root or a leaf, but it must go downwards (i.e., traveling only from parent nodes to child nodes).

- Example :

      Input: root = [10,5,-3,3,2,null,11,3,-2,null,1], targetSum = 8
      Output: 3
      Explanation: The paths that sum to 8 are shown.

- ## Solution:
```cpp
class Solution {
private:
    int result;
    int target;
public:
    void dfs(TreeNode* root, long curSum) {
        if(!root) {
            return ;
        }
        curSum += root->val;
        if(curSum == target) {
            result++;
        }
        dfs(root->left, curSum);
        dfs(root->right, curSum);
    }
    
    void traverse(TreeNode* root) {
        if(!root) {
            return ;
        }
        traverse(root->right);
        traverse(root->left);
        dfs(root, 0);
    }
    
    int pathSum(TreeNode* root, int targetSum) {
        result = 0;
        target = targetSum;
        traverse(root);
        return result;
    }
};
```

## Tags
`Tree` `DFS`
