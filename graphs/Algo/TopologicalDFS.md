public:
	//Function to return list containing vertices in Topological order. 
	void dfs(int node,vector<int>adj[],vector<int>&visited,stack<int>&st)
	{
	    visited[node]=true;
	    for(auto i:adj[node])
	    {
	        if(!visited[i])
	        {
	            dfs(i,adj,visited,st);
	        }
	    }
	    st.push(node);
	}
	vector<int> topoSort(int V, vector<int> adj[]) 
	{
	    // code here
	    stack<int>st;
	    vector<int>ans;
	    vector<int>visited(V,false);
	    for(int i=0;i<V;i++)
	    {
	        if(!visited[i])
	        {
	            dfs(i,adj,visited,st);
	        }
	    }
	    while(!st.empty())
	    {
	        int uppar=st.top();
	        ans.push_back(uppar);
	        st.pop();
	    }
	    return ans;
	}