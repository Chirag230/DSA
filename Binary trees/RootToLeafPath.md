    vector<vector<int>>result;
    void solve(TreeNode*root,vector<int>&use)
    {
        use.push_back(root->val);    
        if (!root->left && !root->right) 
        {
            result.push_back(use);
            use.pop_back(); 
            return;
        }
        if (root->left) 
        {
            solve(root->left, use);
        }
        if (root->right) 
        {
            solve(root->right, use);
        }
        use.pop_back();
    }
    bool hasPathSum(TreeNode* root, int targetSum) 
    {
        if(!root)
        return false;
        vector<int>use;
        solve(root,use);   
        for(int i=0;i<result.size();i++)
        {
            int sum=0;
            for(int j=0;j<result[i].size();j++)
            {
                sum+=result[i][j];
            }
            if(sum==targetSum)
            {
                return true;
            }
        } 
        return false;
    }