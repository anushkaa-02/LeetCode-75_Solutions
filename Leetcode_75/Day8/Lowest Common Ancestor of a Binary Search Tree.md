# Lowest Common Ancestor of a Binary Search Tree
- ## Question:
>Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.
>
>According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as >descendants (where we allow a node to be a descendant of itself).”

- Example :

      Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
      Output: 6
      Explanation: The LCA of nodes 2 and 8 is 6.
      

- ## Solution:
```cpp
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if (!root)
            return nullptr;
        if ((root->val <= p->val && root->val >= q->val) || 
           root->val >= p->val && root->val <= q->val)
            return root;
    
        auto left = lowestCommonAncestor(root->left, p, q);
        auto right = lowestCommonAncestor(root->right, p, q);
        
        if (!left)
            return right; 
        return left;
    }
};
```
