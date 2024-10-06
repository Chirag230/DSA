    vector<int> preOrder(Node* root)
    {
        //code here
        stack<Node*>s;
        vector<int>ans;
        s.push(root);
        while(!s.empty())
        {
            Node* uppar=s.top();
            ans.push_back(uppar->data);
            s.pop();
            if(uppar->right)
            {
                s.push(uppar->right);
            }
            if(uppar->left)
            {
                s.push(uppar->left);
            }
        }
        return ans;
    }