 vector <int> dijkstra(int V, vector<vector<int>> adj[], int S)
    {
        // Code here
        set<pair<int,int>>s;
        vector<int>result(V,INT_MAX);
        result[S]=0;
        s.insert({0,S});
        while(!s.empty())
        {
            int dis  = s.begin()->first;
            int node = s.begin()->second;
            s.erase(s.begin());
            for(auto &it:adj[node])
            {
                int adjNode = it[0];
                int d = it[1];
                if(dis+d<result[adjNode])
                {
                    if(result[adjNode]!=INT_MAX)
                    {
                        s.erase({result[adjNode],adjNode});
                    }
                    result[adjNode]=dis+d;
                    s.insert({dis+d,adjNode});
                }
            }
        }
        return result;
    }