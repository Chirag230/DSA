Given the root of a binary search tree and an integer k, return true if there exist two elements in the BST such that their sum is equal to k, or false otherwise.

class bstprev{
    public:
    stack<TreeNode*>s2;
    bstprev(TreeNode*root)
    {
        pushAll(root);
    }
    void pushAll(TreeNode* node)
    {
        while (node != NULL) 
        {
            s2.push(node);
            node = node->right;
        }
    }
    bool hasprev()
    {
        if(s2.empty())
        {
            return false;
        }
        else
        {
            return true;
        }
    }
    int prev()
    {
        TreeNode*temp = s2.top();
        s2.pop();
        pushAll(temp->left);
        return temp->val;
    }
 };
 class bstnext{
    public:
    stack<TreeNode*>s1;
    bstnext(TreeNode*root)
    {
        pushAll(root);
    }
    void pushAll(TreeNode* node)
    {
        while (node != NULL) 
        {
            s1.push(node);
            node = node->left;
        }
    }
    bool hasnext()
    {
        if(s1.empty())
        {
            return false;
        }
        else
        {
            return true;
        }
    }
    int next()
    {
        TreeNode*temp = s1.top();
        s1.pop();
        pushAll(temp->right);
        return temp->val;
    }

 };
class Solution {
public:
    bool findTarget(TreeNode* root, int k) 
    {
        if(!root)return false;
        bstnext l(root);
        bstprev r(root);
        int i=l.next();
        int j=r.prev();
        while(i<j)
        {
            if(i+j==k)
            return true;
            else if(i+j >k)
            {
                j=r.prev();
            }
            else
            {
                i=l.next();
            }
        }
        return false; 
    }
};