# Symmetric Tree
- ## Question:
>Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

- Example :

      Input: root = [1,2,2,3,4,4,3]
      Output: true
      
- ## Solution:
```cpp
class Solution {
public:
    bool CheckSymmetry(TreeNode * Lsub , TreeNode * Rsub)
{
    if(Lsub ==NULL && Rsub==NULL)
        return 1;
    if(Lsub ==NULL || Rsub ==NULL)
        return 0;
    if(Lsub ->val != Rsub ->val)
        return 0;
     return CheckSymmetry(Lsub ->left ,Rsub ->right) &&  CheckSymmetry(Lsub->right ,Rsub->left); 
    
}
bool isSymmetric(TreeNode* root) {
   int a= CheckSymmetry(root->left ,root->right);
    return a;
}
};
```
