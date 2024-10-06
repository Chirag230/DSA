bool solve(TreeNode*root,int sum,int targetSum)
    {
        if(!root)
        return false;
        sum+=root->val;
        if(root->left==NULL && root->right==NULL)
        {
            return (sum==targetSum);
        }
        bool l=solve(root->left,sum,targetSum);
        bool r=solve(root->right,sum,targetSum);
        return l||r;
    }
    bool hasPathSum(TreeNode* root, int targetSum) 
    {
        if(!root)
        return false;
        if(root->left==NULL && root->right==NULL)
        {
            return (root->val==targetSum);
        }    
        return solve(root,0,targetSum);
    }