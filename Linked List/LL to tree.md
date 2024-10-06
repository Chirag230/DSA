void convert(Node *head, TreeNode *&root) 
{
    // Your code here
    queue<TreeNode*>q;
    root = new TreeNode(head->data);
    q.push(root);
    Node*temp = head->next;
    while(!q.empty() && temp!=NULL)
    {
        TreeNode*aage = q.front();
        if(!aage->left)
        {
            TreeNode*use = new TreeNode(temp->data);
            temp = temp->next;
            q.push(use);
            aage->left = use;
        }
        else
        {
            TreeNode*use = new TreeNode(temp->data);
            temp = temp->next;
            q.push(use);
            aage->right = use;
            q.pop();
        }
    }
}