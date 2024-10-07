   int countSubstrings(string s) 
    {
        int cnt=0;
        int n = s.size();
        vector<vector<bool>>dp(n+1,vector<bool>(n+1,false));
        for(int len=1;len<=n;len++)
        {
            for(int i=0;i+len-1<n;i++)
            {
                int j = i+len-1;
                if(i==j)
                {
                    dp[i][j]=true;
                }
                else if(i+1==j)
                {
                    dp[i][j] = (s[i]==s[j]);
                }
                else
                {
                    dp[i][j] = ((s[i]==s[j]) && (dp[i+1][j-1]==true));
                }
                cnt+=dp[i][j];
            }
        }
        return cnt;
    }