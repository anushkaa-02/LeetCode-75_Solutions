# Invert Binary Tree
- ## Question:
>Given the root of a binary tree, invert the tree, and return its root.


- Example :

      Input: root = [4,2,7,1,3,6,9]
      Output: [4,7,2,9,6,3,1]


- ## Solution:
```cpp
class Solution {
public:

TreeNode* work(TreeNode* root){
    if(root==NULL)return NULL;
    TreeNode* temp=root->left;
    root->left=work(root->right);
    root->right=work(temp); // root->left is now become root->right,that why i store the address in temp;
    return root;
}
TreeNode* invertTree(TreeNode* root) {
    return work(root);
}
};
```
## Tags
`Tree` `DFS`
