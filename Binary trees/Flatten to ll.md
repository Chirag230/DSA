Given the root of a binary tree, flatten the tree into a "linked list":

The "linked list" should use the same TreeNode class where the right child pointer points to the next node in the list and the left child pointer is always null.
The "linked list" should be in the same order as a pre-order traversal of the binary tree.

void flatten(TreeNode* root) 
    {
        TreeNode*curr  = root;
        while(curr!=NULL)
        {
            if(curr->left==NULL)
            {
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
                curr->right=curr->left;
                TreeNode*temp = curr;
                curr=curr->left;
                temp->left=NULL;
            }
        }    
    }