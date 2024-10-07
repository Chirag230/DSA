    bool solve(string s,unordered_set<string>st,int index,vector<int>&dp)
    {
        if(index>=s.size())
        {
            return true;
        }
        if(st.find(s)!=st.end())
        {
            return true;
        }
        if(dp[index]!=-1)
        {
            return dp[index];
        }
        for(int len=1;len<=s.size();len++)
        {
            string subs=s.substr(index,len);
            if(st.find(subs)!=st.end() && solve(s,st,index+len,dp))
            {
                return dp[index]=true;
            }
        }
        return dp[index]=false;
    }
    bool wordBreak(string s, vector<string>& wordDict) 
    {
        unordered_set<string>st;
        for(auto i:wordDict)
        {
            st.insert(i);
        }
        int n=s.size();
        vector<int>dp(n,-1);
        return solve(s,st,0,dp);    
    }