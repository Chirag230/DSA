string solve(TreeNode*root,vector<TreeNode*>&ans,unordered_map<string,int>&m)
  {
      if(root==NULL)
      {
          return "N";
      }
      string s = to_string(root->val) + ","+solve(root->left,ans,m)+","+solve(root->right,ans,m);
      if(m[s]==1)
      {
          ans.push_back(root);
      }
      m[s]++;
      return s;
  }
    vector<TreeNode*> findDuplicateSubtrees(TreeNode* root) 
    {
        unordered_map<string,int>m;
        vector<TreeNode*>ans;
        solve(root,ans,m);
        return ans;
    }