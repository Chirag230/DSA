   vector<int> postOrder(Node* root) 
    {
        // code here
        stack<Node*>s;
        vector<int>ans;
        s.push(root);
        while(!s.empty())
        {
            Node* uppar=s.top();
            ans.push_back(uppar->data);
            s.pop();
            if(uppar->left)
            {
                s.push(uppar->left);
            }
            if(uppar->right)
            {
                s.push(uppar->right);
            }
        }
        reverse(ans.begin(),ans.end());
        return ans;
    }


        vector<int> postOrder(Node* root) 
    {
        // code here
        stack<Node*>s;
        vector<int>ans;
        Node*use=root;
        while(!s.empty() || use!=NULL)
        {
            if(use!=NULL)
            {
                s.push(use);
                use=use->left;
            }
            else
            {
                Node*temp=s.top()->right;
                if(temp==NULL)
                {
                    temp=s.top();
                    s.pop();
                    ans.push_back(temp->data);
                    while(!s.empty() && s.top()->right==temp)
                    {
                        temp=s.top();
                        s.pop();
                        ans.push_back(temp->data);
                    }
                }
                else
                {
                    use=temp;
                }
            }
        }
        return ans;
    }