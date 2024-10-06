LEETCODE-1110
Given the root of a binary tree, each node in the tree has a distinct value.

After deleting all nodes with a value in to_delete, we are left with a forest (a disjoint union of trees).

Return the roots of the trees in the remaining forest. You may return the result in any order.

class Solution {
public:
    unordered_set<int>s;
    TreeNode* solve(TreeNode*root,vector<TreeNode*>&ans)
    {
         if (!root) 
         {
            return NULL;
        }

        root->left = solve(root->left, ans);
        root->right = solve(root->right, ans);

        if (s.find(root->val) != s.end()) 
        {
            if (root->left) ans.push_back(root->left);
            if (root->right) ans.push_back(root->right);
            return NULL; 
        }
        else        
        return root;
    }
    vector<TreeNode*> delNodes(TreeNode* root, vector<int>& to_delete) 
    {
         vector<TreeNode*> ans;
        if (to_delete.empty()) 
        {
            return ans;
        }
        if (root == nullptr) 
        {
            return ans;
        }
        for (int i = 0; i < to_delete.size(); i++) 
        {
            s.insert(to_delete[i]);
        }
        solve(root, ans);
        if (s.find(root->val) == s.end()) 
        {
            ans.push_back(root);
        }
        return ans;
    }
};