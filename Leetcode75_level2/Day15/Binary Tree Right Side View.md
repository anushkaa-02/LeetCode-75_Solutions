# Binary Tree Right Side View
- ## Question:
>Given the root of a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.


- Example :

      Input: root = [1,null,3]
      Output: [1,3]
      
- ## Solution:
```cpp
class Solution{
public:
    vector<int> rightSideView(TreeNode* root)
    {
        if(root==NULL)
        {
            return {};
        }
        vector<int> ans;
        queue<TreeNode*> q;
        q.push(root);
        q.push(NULL);
        while(q.size()!=0)
        {
            auto node=q.front();
            q.pop();
            if(node==NULL)
            {
                continue;
            }
            else if(q.front()==NULL)
            {
                ans.push_back(node->val);
                if(node->left) q.push(node->left);
                if(node->right) q.push(node->right);
                q.push(NULL);
            }
            else
            {
                if(node->left) q.push(node->left);
                if(node->right) q.push(node->right);
            }
        }
        return ans;
        
    }
};
```
