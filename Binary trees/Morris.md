   vector<int> inorderTraversal(TreeNode* root) 
    {
        TreeNode*curr = root;
        vector<int>ans;
        while(curr!=NULL)
        {
            if(curr->left==NULL)
            {
                ans.push_back(curr->val);
                curr=curr->right;
            }
            else
            {
                TreeNode*leftchild=curr->left;
                while(leftchild->right!=NULL)
                {
                    leftchild=leftchild->right;
                }
                leftchild->right=curr;
                //Ab pichla connection todna hai
                TreeNode*temp = curr;
                curr=curr->left;
                temp->left=NULL;

            }
        }    
        return ans;
    }