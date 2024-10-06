class Solution {
public:
    vector<vector<int>> verticalTraversal(TreeNode* root) 
    {
        queue<pair<TreeNode*,pair<int,int>>>q;
        map<int,map<int,multiset<int>>>m;//yahan multiset set use karna pada kyunki same value ho rhi thi nodes ki!!!
        q.push({root,{0,0}});
        while(!q.empty())
        {
            TreeNode*aage = q.front().first;
            int lvl = q.front().second.first;
            int vertical  =q.front().second.second;
            q.pop();
            if(aage->left)
            {
                q.push({aage->left,{lvl+1,vertical-1}});
            }
            if(aage->right)
            {
                q.push({aage->right,{lvl+1,vertical+1}});
            }
            m[vertical][lvl].insert(aage->val);
        }
        vector<vector<int>>ans;
        for(auto i:m)
        {
            vector<int>use;
            for(auto j:i.second)
            {
                use.insert(use.end(),j.second.begin(),j.second.end());
            }
            ans.push_back(use);
        }
        return ans;
    }
};