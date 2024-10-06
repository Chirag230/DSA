Given the root of a binary tree, the value of a target node target, and an integer k, return an array of the values of all nodes that have a distance k from the target node.

You can return the answer in any order.

class Solution {
public:
    void inorder(TreeNode*root,unordered_map<TreeNode*,TreeNode*>&m,unordered_map<TreeNode*,bool>&visited)
    {
        if(!root)
        return;
        if(root->left)
        {
            m[root->left]=root;
            inorder(root->left,m,visited);
        }
        visited[root]=false;
        if(root->right)
        {
            m[root->right]=root;
            inorder(root->right,m,visited);
        }
    }
    vector<int> distanceK(TreeNode* root, TreeNode* target, int k) 
    {
        unordered_map<TreeNode*,TreeNode*>m;
        unordered_map<TreeNode*,bool>visited;
        m[root]=NULL;
        inorder(root,m,visited);
        queue<TreeNode*>q;
        q.push(target);
        visited[target]=true;
        vector<int>ans;
        while(!q.empty())
        {
            int times =  q.size();
            if(k==0)
            {
                while(!q.empty())
                {
                    ans.push_back(q.front()->val);
                    q.pop();
                }
                break;   
            }
            k--;
            while(times>0)
            {
                            
                TreeNode*aage = q.front();
                q.pop();
                if(aage->left && visited[aage->left]!=true)
                {
                    q.push(aage->left);
                    visited[aage->left]=true;
                }
                if(aage->right && visited[aage->right]!=true)
                {
                    q.push(aage->right);
                    visited[aage->right]=true;
                }
                if(m[aage]!=NULL && visited[m[aage]]!=true)
                {
                    q.push(m[aage]);
                    visited[m[aage]]=true;
                }
                times--;
            }
        }
        return ans;
    }
};