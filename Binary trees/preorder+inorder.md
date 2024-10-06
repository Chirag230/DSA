    TreeNode*solve(vector<int>&preorder,vector<int>&inorder,int &idx,int start,int end,unordered_map<int,int>&m)
    {
        if(start>end)
        {
            return NULL;
        }
        TreeNode*root=new TreeNode(preorder[idx]);
        int index = m[preorder[idx]];
        idx++;
        root->left=solve(preorder,inorder,idx,start,index-1,m);
        root->right=solve(preorder,inorder,idx,index+1,end,m);

        return root;
    }
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) 
    {
        unordered_map<int,int> m;
        for(int i=0;i<inorder.size();i++)
        {
            m[inorder[i]]=i;
        }
        int n=inorder.size();
        int idx=0;
       return solve(preorder,inorder,idx,0,n-1,m);
    }