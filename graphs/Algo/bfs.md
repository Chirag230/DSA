 vector<int> bfsOfGraph(int V, vector<int> adj[]) 
    {
        // Code here
        vector<int>visited(V,false);
        queue<int>q;
        q.push(0);
        visited[0]=true;
        vector<int>ans;
        while(!q.empty())
        {
            int aage = q.front();
            q.pop();
            ans.push_back(aage);
            for(auto i:adj[aage])
            {
                if(!visited[i])
                {
                    visited[i]=true;
                    q.push(i);
                }
            }
        }
        return ans;        
    }