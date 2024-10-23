    class MinMax 
    {
        public:
        int min;
        int max;
        bool isBST;
        int size;
    
        MinMax() 
        {
            min = INT_MAX;
            max = INT_MIN;
            isBST = true;
            size = 0;
        }
    };
    
    MinMax findLargestBST(Node* root) 
    {
        if (root == nullptr) 
        {
            return MinMax();
        }
    
        MinMax leftMinMax = findLargestBST(root->left);
        MinMax rightMinMax = findLargestBST(root->right);
    
        MinMax m;
    
        if (!leftMinMax.isBST || !rightMinMax.isBST || leftMinMax.max >= root->data || rightMinMax.min <= root->data) {
            m.isBST = false;
            m.size = max(leftMinMax.size, rightMinMax.size);
            return m;
        }
    
        m.isBST = true;
        m.size = leftMinMax.size + rightMinMax.size + 1;
        m.min = root->left ? leftMinMax.min : root->data;
        m.max = root->right ? rightMinMax.max : root->data;
    
        return m;
    }
    
    int largestBst(Node* root) {
        return findLargestBST(root).size;
    }