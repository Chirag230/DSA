class Solution {
public:
    void solve(int node,TreeNode*root)
    {
        if(node<root->val)
        {
            if(root->left==NULL)
            {
                root->left=new TreeNode(node);
                return;
            }
            else
            {
                solve(node,root->left);
            }
        }
        else if(root->val < node)
        {
            if(root->right==NULL)
            {
                root->right = new TreeNode(node);
                return;
            }
            else
            {
                solve(node,root->right);
            }
        }
    }
    TreeNode* bstFromPreorder(vector<int>& preorder) 
    {
        TreeNode*ans = new TreeNode(preorder[0]);
        for(int i=1;i<preorder.size();i++)
        {
            solve(preorder[i],ans);
        }   
        return ans; 
    }
};