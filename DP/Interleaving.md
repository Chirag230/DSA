Given strings s1, s2, and s3, find whether s3 is formed by an interleaving of s1 and s2.

An interleaving of two strings s and t is a configuration where s and t are divided into n and m 
substrings
 respectively, such that:

s = s1 + s2 + ... + sn
t = t1 + t2 + ... + tm
|n - m| <= 1
The interleaving is s1 + t1 + s2 + t2 + s3 + t3 + ... or t1 + s1 + t2 + s2 + t3 + s3 + ...
Note: a + b is the concatenation of strings a and b.

 bool solve(string s1,string s2,string s3,int i,int j,int k,vector<vector<vector<int>>>&dp)
    {
        if(i==s1.size() && j==s2.size() && k==s3.size())
        {
            return true;
        }
        if(k>=s3.size())
        {
            return false;
        }
        if(dp[i][j][k]!=-1)
        {
            return dp[i][j][k];
        }
        bool result=false;
        if(i<s1.size() && s1[i]==s3[k])
        {
            result=solve(s1,s2,s3,i+1,j,k+1,dp);
        }
        if(!result && j<s2.size() && s2[j]==s3[k])
        {
            result=solve(s1,s2,s3,i,j+1,k+1,dp);
        }
        return dp[i][j][k]=result;
    }
    bool isInterleave(string s1, string s2, string s3) 
    {
        int l1=s1.size();
        int l2=s2.size();
        int n=s3.size();
        if(l1+l2!=n)
        return false;
        vector<vector<vector<int>>>dp(l1+1,vector<vector<int>>(l2+1,vector<int>(n+1,-1)));
        return solve(s1,s2,s3,0,0,0,dp);
    }


    ---------------------------------------------------------------------------------------------------------------------------
    class Solution {
public:
    bool solve(string s1, string s2, string s3, int i, int j, int k, vector<vector<vector<int>>>& dp) 
    {
        if (i < 0 && j < 0 && k < 0) 
        {
            return true;
        }
        if (k < 0) 
        {
            return false;
        }
        
        if (dp[i + 1][j + 1][k + 1] != -1) 
        {
            return dp[i + 1][j + 1][k + 1];
        }
        
        bool op1 = false;
        bool op2 = false;
        
        if (i >= 0 && s3[k] == s1[i]) 
        {
            op2 = solve(s1, s2, s3, i - 1, j, k - 1, dp);
        }
        if (j >= 0 && s3[k] == s2[j]) 
        {
            op1 = solve(s1, s2, s3, i, j - 1, k - 1, dp);
        }
        
        return dp[i + 1][j + 1][k + 1] = op1 || op2;
}

    bool isInterleave(string s1, string s2, string s3) 
    {
        int n = s1.size();
        int m = s2.size();
        int s = s3.size();
        
        if (n + m != s) 
        {
            return false;
        }
        
        if (n == 0) 
        {
            return s2 == s3;
        }
        
        if (m == 0) 
        {
            return s1 == s3;
        }
        
        vector<vector<vector<int>>> dp(n + 1, vector<vector<int>>(m + 1, vector<int>(s + 1, -1)));
        return solve(s1, s2, s3, n - 1, m - 1, s - 1, dp);
    }
};