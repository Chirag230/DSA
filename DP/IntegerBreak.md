Given an integer n, break it into the sum of k positive integers, where k >= 2, and maximize the product of those integers.

Return the maximum product you can get.

 

Example 1:

Input: n = 2
Output: 1
Explanation: 2 = 1 + 1, 1 × 1 = 1.


  int solve(int n,vector<int>&dp)
    {
        if(n==1)
        return 1;
        if(dp[n]!=-1)
        {
            return dp[n];
        }
        int maxi=INT_MIN;
        for(int i=1;i<n;i++)
        {
            int p = i*max(n-i,solve(n-i,dp));
            maxi=max(maxi,p);
        }
        return dp[n]=maxi;
    }
    int integerBreak(int n) 
    {
        vector<int>dp(n+1,-1);
        return solve(n,dp); 
    }