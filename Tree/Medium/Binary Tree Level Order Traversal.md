# [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

### Approach:
- We start at the root node and visit each level of the binary tree in a left-to-right order.
- We use a queue to keep track of the nodes at each level.
- We process each level by first getting the size of the queue, which represents the number of nodes at the current level. 
- Then, we iterate over the nodes at the current level, add their values to a vector, and enqueue their children (if any) into the queue for the next level.


**Code:**
```
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        
        vector<vector<int>> res;
        if(root==NULL) return res;
        queue<TreeNode*> q;
        q.push(root);
        vector<int> level;
        while(!q.empty()){  
            int level_size= q.size();
            level.clear();
            
            while(level_size--){
                TreeNode* fr= q.front(); 
                q.pop();
                level.push_back(fr->val);
                if(fr->left) q.push(fr->left);
                if(fr->right) q.push(fr->right);
            }
            res.push_back(level);   
        }
        return res;
    }
};
```
