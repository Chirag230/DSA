MORRIS TRAVERSAL
vector<int> preorderTraversal(TreeNode* root) 
    {
        TreeNode*curr  = root;
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
                TreeNode*leftchild  = curr->left;
                while(leftchild->right!=NULL)
                {
                    leftchild=leftchild->right;
                }
                leftchild->right=curr->right;
                ans.push_back(curr->val);
                TreeNode*temp = curr;
                curr = curr->left;
                temp->left=NULL;
            }
        }    
        return ans;
    }