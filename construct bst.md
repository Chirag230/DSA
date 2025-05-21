Given the root of a binary search tree, return a balanced binary search tree with the same node values. If there is more than one answer, return any of them.

A binary search tree is balanced if the depth of the two subtrees of every node never differs by more than 1.

class Solution {
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
};