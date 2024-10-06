void dfs(int node,vector<int>adj[],vector<bool>&visited,vector<int>&ans)
    {
        visited[node]=true;
        ans.push_back(node);
        for(auto i:adj[node])
        {
            if(!visited[i])
            dfs(i,adj,visited,ans);
        }
    }
    vector<int> dfsOfGraph(int V, vector<int> adj[]) 
    {
        // Code here
        vector<int>ans;
        vector<bool>visited(V,false);
        for(int i=0;i<V;i++)
        {
            if(!visited[i])
            {
                dfs(i,adj,visited,ans);
            }
        }
        return ans;
    }