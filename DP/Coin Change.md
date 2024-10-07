You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

 

Example 1:

Input: coins = [1,2,5], amount = 11
Output: 3
Explanation: 11 = 5 + 5 + 1

int solve(int index,vector<int>&coins,int amount,vector<vector<int>>&dp)
    {
        if(index==0)
        {
            if((amount%coins[0])==0)
            {
                return amount/coins[0];
            }
            else
            {
                return 1e9;
            }
        }
        if(dp[index][amount]!=-1)
        {
            return dp[index][amount];
        }
        int op1=INT_MAX;
        if(amount>=coins[index])
        {
            op1 = 1+solve(index,coins,amount-coins[index],dp);
        }
        int op2  = 0+solve(index-1,coins,amount,dp);
        return dp[index][amount]=min(op2,op1);
    }
    int coinChange(vector<int>& coins, int amount) 
    {
        int n = coins.size();
        vector<vector<int>>dp(n,vector<int>(amount+1,-1));
        int ans =  solve(n-1,coins,amount,dp);    
        if(ans>=1e9)
        return -1;
        else 
        return ans;
    }