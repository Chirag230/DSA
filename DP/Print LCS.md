void solve(string &s, string &t, vector<vector<int>> &dp, string &current, set<string> &ans, int n, int m, vector<vector<set<string>>> &memo) 
{
    if (n == 0 || m == 0) 
    {
        string r=current;
        reverse(r.begin(),r.end());
        ans.insert(r);
        return;
    }

    if (memo[n][m].find(current) != memo[n][m].end()) 
    {
        return;
    }

    if (s[n-1] == t[m-1]) 
    {
        current.push_back(s[n-1]);
        solve(s, t, dp, current, ans, n-1, m-1, memo);
        current.pop_back();
    } 
    else 
    {
        if (dp[n-1][m] == dp[n][m]) 
        {
            solve(s, t, dp, current, ans, n-1, m, memo);
        }
        if (dp[n][m-1] == dp[n][m]) 
        {
            solve(s, t, dp, current, ans, n, m-1, memo);
        }
    }

    memo[n][m].insert(current);
}
    vector<string> all_longest_common_subsequences(string s, string t) 
    {
        // Code here
        int n=s.size();
        int m =t.size();
        vector<vector<int>>dp(n+1,vector<int>(m+1,0));
        for(int i=1;i<=n;i++)
        {
            for(int j=1;j<=m;j++)
            {
                if(s[i-1]==t[j-1])
                {
                    dp[i][j]=1+dp[i-1][j-1];
                }
                else
                {
                    dp[i][j]=max(dp[i-1][j],dp[i][j-1]);
                }
            }
        }
        set<string> ans;
        string current;
        vector<vector<set<string>>> memo(n + 1, vector<set<string>>(m + 1));
        solve(s, t, dp, current, ans, n, m, memo);
        vector<string> result(ans.begin(), ans.end());
        sort(result.begin(), result.end());
        return result;
    }