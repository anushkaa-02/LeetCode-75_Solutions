# Validate Binary Search Tree
- ## Question:
>Given the root of a binary tree, determine if it is a valid binary search tree (BST).
>
A valid BST is defined as follows:
>
>The left subtree of a node contains only nodes with keys less than the node's key.
>The right subtree of a node contains only nodes with keys greater than the node's key.
>Both the left and right subtrees must also be binary search trees.

- Example :

      Input: root = [2,1,3]
      Output: true
      

- ## Solution:
```cpp
class Solution {
public:
    bool solve(TreeNode* root,long long int minimum,long long int maximum){
        if(root==NULL) return true;
        
        if(root->val>=maximum || root->val <= minimum) return false;
        
        return solve(root->left,minimum,root->val) && solve(root->right,root->val,maximum);
    }
    bool isValidBST(TreeNode* root) {
        return solve(root,LLONG_MIN,LLONG_MAX);
    }
};
```
## Tags
`Tree` `DFS`
