class Solution
{
	public:
	   //Function to find the shortest distance of all the vertices
    	   //from the source vertex S.
	    vector <int> dijkstra(int V, vector<vector<int>> adj[], int S) {

		priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;

		vector<int> result(V, INT_MAX);

		result[S] = 0;
		pq.push({0, S});
		//NOTE - You can add a visited vector to avoid revisiting a node again and again. It will reduce the time complexity.

		while(!pq.empty()) {

		    int d  = pq.top().first;
		    int node = pq.top().second;
		    pq.pop();

		    for(auto &vec : adj[node]) {

			int adjNode = vec[0];
			int dist    = vec[1];

			if(d + dist < result[adjNode]) {

			    result[adjNode] = d + dist;
			    pq.push({d+dist, adjNode});

			}

		    }

		}

		return result;

	    }
}; 


-------------------------------------------------------
Dijkstra on 2D MATRIX
 vector<vector<int>> directions{{1,1}, {0,1},{1,0},{0,-1},{-1,0},{-1, -1},{1, -1},{-1, 1}};
    bool isSafe(int x, int y,int m,int n) 
    {
        if(x>=0 && x<m && y>=0 && y<n)  
        return true;
        else
        return false;
    };
    int shortestPathBinaryMatrix(vector<vector<int>>& grid) 
    {
        int m = grid.size();
        int n = grid[0].size();
        if(m == 0 || n == 0 || grid[0][0] != 0)
        return -1;

        vector<vector<int>> result(m, vector<int>(n, INT_MAX));
        priority_queue<pair<int, pair<int, int>>,vector<pair<int, pair<int, int>>>,greater<pair<int, pair<int, int>>>>pq;
        
        pq.push({0, {0, 0}});
        result[0][0] = 0;
  
        while(!pq.empty()) 
        {
            int d  = pq.top().first;
            pair<int, int> node = pq.top().second;
            pq.pop();

            int x = node.first;
            int y = node.second;
                
            for(auto dir:directions) 
            {
                int x_   = x + dir[0];
                int y_   = y + dir[1];
                int dist = 1;

                if(isSafe(x_, y_,m,n) && grid[x_][y_] == 0 && d+dist < result[x_][y_]) 
                {
                    pq.push({d+dist, {x_, y_}});
                    grid[x_][y_] = 1;
                    result[x_][y_] = d + dist;
                }
            }
        }
        
        if(result[m-1][n-1] == INT_MAX)
            return -1;
        
        return result[m-1][n-1]+1;
    }