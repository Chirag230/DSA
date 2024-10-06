   vector<int> inOrder(Node* root)
    {
        //code here
        vector<int>ans;
        stack<Node*>s;
        Node*use=root;
        while(true)
        {
            if(use!=NULL)
            {
                s.push(use);
                use=use->left;
            }
            else
            {
                if(s.empty())
                {
                    break;
                }
                use=s.top();
                s.pop();
                ans.push_back(use->data);
                use=use->right;
            }
        }
        return ans;
    }