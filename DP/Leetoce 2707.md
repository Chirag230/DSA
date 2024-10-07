You are given a 0-indexed string s and a dictionary of words dictionary. You have to break s into one or more non-overlapping substrings such that each substring is present in dictionary. There may be some extra characters in s which are not present in any of the substrings.

Return the minimum number of extra characters left over if you break up s optimally.

 

Example 1:

Input: s = "leetscode", dictionary = ["leet","code","leetcode"]
Output: 1
Explanation: We can break s in two substrings: "leet" from index 0 to 3 and "code" from index 5 to 8. There is only 1 unused character (at index 4), so we return 1.

   int solve(int i, string& s, unordered_set<string>& st, int &n,vector<int>&dp) 
    {
        if(i >= n) 
        {
            return 0;
        }       
        if(dp[i]!=-1)
        {
            return dp[i];
        }
        int result = 1 + solve(i+1, s, st, n,dp);
        for(int j = i; j < n; j++) 
        {
            string curr = s.substr(i, j-i+1);
            if(st.count(curr)) 
            {
                //valid substring
                result = min(result, solve(j+1, s, st, n,dp));
            }
        }

        return  dp[i]=result;
    }

    int minExtraChar(string s, vector<string>& dict) 
    {
        int n = s.length();
        unordered_set<string> st(begin(dict), end(dict));
        vector<int>dp(n+1,-1);
        return solve(0, s, st, n,dp);
    }