Given an integer array arr and an integer difference, return the length of the longest subsequence in arr which is an arithmetic sequence such that the difference between adjacent elements in the subsequence equals difference.

A subsequence is a sequence that can be derived from arr by deleting some or no elements without changing the order of the remaining elements.

 

Example 1:

Input: arr = [1,2,3,4], difference = 1
Output: 4
Explanation: The longest arithmetic subsequence is [1,2,3,4].


   int longestSubsequence(vector<int>& arr, int difference) 
    {
        int n=arr.size();
        vector<int>dp(n,1);
        int maxi=1;
        unordered_map<int,int>m;
        m[arr[0]]=0;
        for(int i=1;i<n;i++)
        {
            if(m.find(arr[i]-difference)!=m.end())
            {
                dp[i]=dp[m[arr[i]-difference]]+1;
            }
            maxi=max(dp[i],maxi);
            m[arr[i]]=i;
        }    
        return maxi;
    }