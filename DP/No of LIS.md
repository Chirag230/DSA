Given an integer array nums, return the number of longest increasing subsequences.

Notice that the sequence has to be strictly increasing.

 

Example 1:

Input: nums = [1,3,5,4,7]
Output: 2
Explanation: The two longest increasing subsequences are [1, 3, 4, 7] and [1, 3, 5, 7].

int findNumberOfLIS(vector<int>& nums) 
{
    int n=nums.size();
    vector<int>dp(n,1);
    vector<int>count(n,1);
    for(int i=1;i<n;i++)
    {
        for(int j=0;j<i;j++)
        {
            if(nums[i]>nums[j])
            {
                if(dp[i]<dp[j]+1)
                {
                    dp[i]=dp[j]+1;
                    count[i]=count[j];
                }
                else if(dp[i]==dp[j]+1)
                {
                    count[i]+=count[j];
                }
            }                
        }
    }  
    int maxi=1;
    for(int i=0;i<dp.size();i++)
    {
        maxi=max(maxi,dp[i]);
    }  
    int ans=0;
    for(int i=0;i<count.size();i++)
    {
        if(dp[i]==maxi)
        {
            ans+=count[i];
        }
    }
    return ans;
}