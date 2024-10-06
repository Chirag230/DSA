vector<int> topoSort(int V, vector<int> adj[]) 
	{
	    // code here
	    vector<int>indegree(V,0);
	    for(int i=0;i<V;i++)
	    {
	        for(auto it:adj[i])
	        {
	            indegree[it]++;
	        }
	    }
	    queue<int>q;
	    for(int i=0;i<indegree.size();i++)
	    {
	        if(indegree[i]==0)
	        {
	            q.push(i);
	        }
	    }
	    vector<int>ans;
	    while(!q.empty())
	    {
	        int aage = q.front();
	        ans.push_back(aage);
	        q.pop();
	        for(auto i:adj[aage])
	        {
	            indegree[i]--;
	            if(indegree[i]==0)
	            {
	                q.push(i);
	            }
	        }
	    }
	    return ans;
	}