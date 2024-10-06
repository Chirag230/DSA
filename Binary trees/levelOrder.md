vector<vector<int>> levelOrder(TreeNode* root) 
    {
        vector<vector<int>>ans;
        if(!root)
        return ans;
        queue<TreeNode*>q;
        q.push(root);
        while(!q.empty())
        {
            vector<int>use;
            int times =  q.size();
            while(times>0)
            {
                TreeNode* aage = q.front();
                use.push_back(aage->val);
                if(aage->left)
                {
                    q.push(aage->left);
                }
                if(aage->right)
                {
                    q.push(aage->right);
                }
                q.pop();
                times--;
            }
            ans.push_back(use);
        }    
        return ans;
    }