# Balanced Binary Tree
- ## Question:
>Given a binary tree, determine if it is height-balanced.
>
>For this problem, a height-balanced binary tree is defined as:
>
>a binary tree in which the left and right subtrees of every node differ in height by no more than 1.


- Example :

      Input: root = [3,9,20,null,null,15,7]
      Output: true

- ## Solution:
```cpp
class Solution {
public:
    int check(TreeNode* root, bool &ans)
    {
        if (!root)return true;
        
        int lh = check(root->left,ans);
        int rh = check(root->right,ans);
        if(abs(lh-rh)>1)
        {
            ans= false;
        }
        return 1+max(lh,rh); 
    }
    bool isBalanced(TreeNode* root) 
    {
        bool ans=true;
        check(root,ans);
        return ans;
    }
};
```

## Tags
`Tree` `DFS`
