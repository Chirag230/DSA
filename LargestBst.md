bool isdataidBST(Node* root, int mindata, int maxdata) {
        if (root == nullptr) return true;
        if (root->data >= maxdata || root->data <= mindata) return false;
        return isdataidBST(root->left, mindata, root->data) &&
               isdataidBST(root->right, root->data, maxdata);
    }
     int countNodes(Node* root) {
        if (root == nullptr) return 0;
        return 1 + countNodes(root->left) + countNodes(root->right);
    }
    int largestBst(Node *root)
    {
    	if (root == nullptr) return 0;
        if (isdataidBST(root, INT_MIN, INT_MAX)) {
            // If the current node is a dataid BST,
            // return the size of the entire subtree
            return countNodes(root);
        } else {
            // If not, explore left and right subtrees
            int left = largestBst(root->left);
            int right = largestBst(root->right);
            return max(left, right);
        }
    }