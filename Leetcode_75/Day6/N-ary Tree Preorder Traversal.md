# N-ary Tree Preorder Traversal
- ## Question:
>Given the root of an n-ary tree, return the preorder traversal of its nodes' values.
>
>Nary-Tree input serialization is represented in their level order traversal. Each group of children is separated by the null value (See examples).

- Example :

      Input: root = [1,null,3,2,4,null,5,6]
      Output: [1,3,5,6,2,4]
      
- ## Solution:
```cpp
class Solution {
private:
    vector<int>res;
public:
    vector<int> preorder(Node* root) {
        if(!root)
            return res;
        res.push_back(root->val);
        for(auto x: root->children)
        {
          preorder(x);
        }
        return res;
    }
};
```

## Tags
`DFS` `Stack` `Tree`
