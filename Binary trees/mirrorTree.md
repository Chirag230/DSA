void mirror(Node* node) 
    {
        // code here
        if(!node)
        return;
        Node*l=node->left;
        Node*r=node->right;
        node->left=r;
        node->right=l;
        mirror(node->left);
        mirror(node->right);
    }


    void mirror(Node* node) 
    {
        if (node == NULL) return;
        mirror(node->left);
        mirror(node->right);
        swap(node->left, node->right);
    }