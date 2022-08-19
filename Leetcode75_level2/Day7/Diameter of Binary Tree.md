# Diameter of Binary Tree
- ## Question:
>Given the root of a binary tree, return the length of the diameter of the tree.
>
>The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.
>
>The length of a path between two nodes is represented by the number of edges between them.


- Example :

      Input: root = [1,2,3,4,5]
      Output: 3
      Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].

- ## Solution:
```cpp
class Solution {
    pair<int, int> helper(TreeNode* root){
        if (root == NULL){
            return make_pair(0, 0);
        }
        pair<int, int> left = helper(root->left);
        pair<int, int> right = helper(root->right);
        
        int depth = max(left.second+1, right.second+1);
        int diameter = max(left.first, right.first);
        diameter = max(diameter, left.second + right.second);
        return make_pair(diameter, depth);
    }
public:
    int diameterOfBinaryTree(TreeNode* root) {
        if (root == NULL){
            return 0;
        }
        pair<int, int> p = helper(root);
        return p.first;
    }
};
```
