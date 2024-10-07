Given an array nums of integers, return the length of the longest arithmetic subsequence in nums.

Note that:

A subsequence is an array that can be derived from another array by deleting some or no elements without changing the order of the remaining elements.
A sequence seq is arithmetic if seq[i + 1] - seq[i] are all the same value (for 0 <= i < seq.length - 1).
 

Example 1:

Input: nums = [3,6,9,12]
Output: 4
Explanation:  The whole array is an arithmetic sequence with steps of length = 3.


 int longestArithSeqLength(vector<int>& arr) 
    {
        int n=arr.size();
        vector<vector<int>>dp(n,vector<int>(10001,1));
        int maxi=1;
        for(int i=1;i<n;i++)
        {
            for(int j=0;j<i;j++)
            {
                int diff = arr[i]-arr[j]+500;
                dp[i][diff] = max(dp[j][diff]+1,2);
                maxi=max(maxi,dp[i][diff]);
            }
        }
        return maxi;
    }