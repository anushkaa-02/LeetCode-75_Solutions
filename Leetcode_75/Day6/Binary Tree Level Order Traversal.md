# Binary Tree Level Order Traversal
- ## Question:
>Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

- Example :

      Input: root = [3,9,20,null,null,15,7]
      Output: [[3],[9,20],[15,7]]
      
- ## Solution:
```cpp
class Solution {
public:
    vector<vector<int>> ans;
    
    void dfs(TreeNode* root, int level){
        if(!root)
            return;
        if(level==ans.size()){
            ans.push_back({});
        }
        ans[level].push_back(root->val);
        dfs(root->left,level+1);
        dfs(root->right,level+1);
    }
    vector<vector<int>> levelOrder(TreeNode* root) {
        
        dfs(root,0);
        return ans;
    }
};
```

## Tags 
`BFS` `Tree`
