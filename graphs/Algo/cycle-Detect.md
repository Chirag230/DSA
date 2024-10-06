  //bfs also dfs below
  bool detect(int src, vector<int> adj[], int vis[]) 
    {
    vis[src] = 1;

    queue<pair<int, int>> q;
    q.push({src, -1});

    while (!q.empty())
    {
        int node = q.front().first;
        int parent = q.front().second;
        q.pop();


        for (auto adjacentNode : adj[node]) 
        {
            if (!vis[adjacentNode])
            {
                vis[adjacentNode] = 1;
                q.push({adjacentNode, node});
            }
            
            else if (parent != adjacentNode) 
            {
                return true;
            }
        }
    }
    return false;
}

bool isCycle(int V, vector<int> adj[]) 
{

    int vis[V] = {0};
    for (int i = 0; i < V; i++) 
    {
        if (!vis[i]) 
        {
            if (detect(i, adj, vis))
                return true;
        }
    }
    return false;
}
------------------------------------------------------------------------------------------------------------------
class Solution {
  public:
    // Function to detect cycle in an undirected graph.
    bool dfs(vector<int>adj[],vector<bool>&visited,int node,int parent)
    {
        visited[node]=true;
        for(auto i:adj[node])
        {
            if(!visited[i])
            {
                if (dfs(adj, visited, i, node)) 
                {
                    return true;
                }   
            }
            else if(visited[i]==true && i!=parent)
            {
                return true;
            }
        }
        return false;
    }
    bool isCycle(int V, vector<int> adj[]) 
    {
        // Code here
        bool ans=false;
        vector<bool>visited(V,false);
        for(int i=0;i<V;i++)
        {
            if(visited[i]==false)
            {
                if (dfs(adj, visited, i, -1)) 
                {
                    return true;
                }
            }
        }
        return ans;
    }
};