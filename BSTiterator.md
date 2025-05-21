class BSTIterator {
public:
    stack<TreeNode*> s;
    void pushAll(TreeNode* node)
    {
        while (node != NULL) 
        {
            s.push(node);
            node = node->left;
        }
    }
    BSTIterator(TreeNode* root) 
    {
        pushAll(root);
    }
    
    int next() 
    {
        TreeNode* tmp=s.top();
        s.pop();
        pushAll(tmp->right);
        return tmp->val;
    }
    
    bool hasNext() 
    {
        return !s.empty();   
    }
};