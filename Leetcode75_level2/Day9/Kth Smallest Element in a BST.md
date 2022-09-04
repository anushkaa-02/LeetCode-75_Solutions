# Kth Smallest Element in a BST
- ## Question:
>Given the root of a binary search tree, and an integer k, return the kth smallest value (1-indexed) of all the values of the nodes in the tree.


- Example :

      Input: root = [5,3,6,2,4,null,null,1], k = 3
      Output: 3
 
 
- ## Solution:
```cpp
class Solution {
    public:
    int kthSmallest(TreeNode* root, int k) {
    const int leftCount = countNodes(root->left);

    if (leftCount == k - 1)
      return root->val;
    if (leftCount >= k)
      return kthSmallest(root->left, k);
    return kthSmallest(root->right, k - 1 - leftCount);  // leftCount < k
  }

 private:
  int countNodes(TreeNode* root) {
    if (!root)
      return 0;
    return 1 + countNodes(root->left) + countNodes(root->right);
  }
};
```
