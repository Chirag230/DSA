class Solution
{
	public:
	//Function to find sum of weights of edges of the Minimum Spanning Tree.
    int spanningTree(int V, vector<vector<int>> adj[])
    {
        // code here
        priority_queue<pair<int,int>,vector<pair<int,int>>,greater<pair<int,int>>>mini;
        int sum=0;
        vector<int>visited(V,false);
        mini.push({0,0});
        while(!mini.empty())
        {
            int cost = mini.top().first;
            int node = mini.top().second;
            mini.pop();
            if(visited[node]==true)
            {
                continue;
            }
            visited[node]=true;
            sum+=cost;
            for(auto i:adj[node])
            {
                int neighbour = i[0];
                int weight = i[1];
                
                if(visited[neighbour]==false)
                {
                    mini.push({weight,neighbour});
                }
            }
        }
        return sum;
    }
};