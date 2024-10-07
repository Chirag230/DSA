string longestPalindrome(string s) 
    {
        int maxi=1;
        int n = s.size();
        int start=0;
        int end=0;
        vector<vector<bool>>dp(n+1,vector<bool>(n+1,false));
        for(int len=1;len<=n;len++)
        {
            for(int i=0;i+len-1<n;i++)
            {
                int j=i+len-1;
                if(i==j)
                {
                    dp[i][j]=true;                    
                }
                else if(i+1==j)
                {
                    dp[i][j] =(s[i]==s[j]);
                    
                }
                else
                {
                    dp[i][j] = ((s[i]==s[j]) && (dp[i+1][j-1]==true));
                }
                if((dp[i][j]==true) && len>maxi)
                {
                    maxi=len;
                    start=i;
                    end=j;
                }
            }
        }
        string ans;
        for(int i=start;i<=end;i++)
        {
            ans+=s[i];
        }
        return ans;
    }