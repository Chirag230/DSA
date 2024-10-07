int solve(vector<vector<int>>& books, int shelfWidth, int index,vector<int>&dp) 
    {
    
        if (index == books.size()) 
        {
            return 0;
        }
        if(dp[index]!=-1)
        return dp[index];
        int currentWidth = 0;
        int currentHeight = 0;
        int minHeight = INT_MAX;

        for (int i = index; i < books.size(); ++i) 
        {
            currentWidth += books[i][0]; 
            if (currentWidth > shelfWidth) 
            {
                break; 
            }
            currentHeight = max(currentHeight, books[i][1]); 
            minHeight = min(minHeight, currentHeight + solve(books, shelfWidth, i + 1,dp));
        }
        
        return dp[index]=minHeight;
}
    int minHeightShelves(vector<vector<int>>& books, int shelfWidth) 
    {
        int n = books.size();
        int i=0;
        vector<int>dp(n,-1);
        return solve(books,shelfWidth,i,dp);
    }