   void solve(Node*root,int lvl,vector<int>&ans)
    {
        if(!root)
        return;
        if(ans.size()==lvl)
        {
            ans.push_back(root->data);
        }
        if(root->right)
        solve(root->right,lvl+1,ans);
        if(root->left)
        solve(root->left,lvl+1,ans);
    }
    vector<int> rightView(Node *root)
    {
       // Your Code here
       vector<int>ans;
       solve(root,0,ans);
       return ans;
    }
  
  
  
  
  
  
  
    vector<int> rightSideView(TreeNode* root) 
    {
        vector<int>ans;
        if(!root)
        return ans;
        queue<TreeNode*>q;
        q.push(root);
        while(!q.empty())
        {
            int save;
            int times=q.size();
            while(times>0)
            {
                TreeNode*aage = q.front();
                save = aage->val;
                if(aage->left)
                {
                    q.push(aage->left);
                }
                if(aage->right)
                {
                    q.push(aage->right);
                }
                q.pop();
                times--;
            }
            ans.push_back(save);
        }
        return ans;
    }

    
Left View of Binary Tree
Difficulty: EasyAccuracy: 33.74%Submissions: 504K+Points: 2
Given a Binary Tree, return Left view of it. Left view of a Binary Tree is set of nodes visible when tree is visited from Left side. The task is to complete the function leftView(), which accepts root of the tree as argument. If no left view is possible, return an empty tree.

vector<int> leftView(Node *root)
{
   // Your code here
   if(!root)
   return {};
   vector<int>ans;
   queue<Node*>q;
   q.push(root);
   while(!q.empty())
   {
       int times=q.size();
       for(int i=1;i<=times;i++)
       {
           Node*aage=q.front();
           q.pop();
           if(i==1)
           {
               ans.push_back(aage->data);
           }
           if(aage->left)
           {
               q.push(aage->left);
           }
           if(aage->right)
           {
               q.push(aage->right);
           }
       }
   }
   return ans;
}