class Solution 
public:
    void inorder(TreeNode*root,vector<int>&ans)
    {
        if(!root)
        return;
        inorder(root->left,ans);
        ans.push_back(root->val);
        inorder(root->right,ans);
    }
    TreeNode*construct(vector<int>&ans,int start,int end)
    {
        if(start>end)
        {
            return NULL;
        }
        int mid = start+(end-start)/2;
        TreeNode*naya = new TreeNode(ans[mid]);
        naya->left=construct(ans,start,mid-1);
        naya->right=construct(ans,mid+1,end);
        return naya;
    }
    TreeNode* balanceBST(TreeNode* root) 
    {
        vector<int>ans;
        inorder(root,ans);
        int n = ans.size();
        TreeNode*naya = construct(ans,0,n-1);
        return naya;
    }