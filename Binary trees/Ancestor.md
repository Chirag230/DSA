 bool solve(Node* root, int target, vector<int>& ans) 
  {
    if (root == NULL) 
    {
        return false;
    }

    if (root->data == target) 
    {
        return true;
    }
    if (solve(root->left, target, ans) || solve(root->right, target, ans)) {
        ans.push_back(root->data);
        return true;
    }
    return false;
}
    // Function should return all the ancestor of the target node
    vector<int> Ancestors(struct Node *root, int target) 
    {
        // Code here
        
        if(root->left==NULL && root->right==NULL && root->data==target)
        {
            return {};
        }
        vector<int>ans;
        solve(root,target,ans);
        return ans;
    }