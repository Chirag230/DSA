int longestIncreasingSubsequence(int arr[], int n)
{
    
    vector<int> dp(n,1);
    vector<int> hash(n,1);
    
    for(int i=0; i<=n-1; i++)
    {
        
        hash[i] = i; // initializing with current index
        for(int j = 0; j <=i-1; j ++)
        {
            
            if(arr[j]<arr[i] && 1 + dp[j] > dp[i])
            {
                dp[i] = 1 + dp[j];
                hash[i] = j;
            }
        }
    }
    
    int ans = -1;
    int lastIndex =-1;
    
    for(int i=0; i<=n-1; i++)
    {
        if(dp[i]> ans)
        {
            ans = dp[i];
            lastIndex = i;
        }
    }
    
    vector<int> temp;
    temp.push_back(arr[lastIndex]);
    
    while(hash[lastIndex] != lastIndex)
    { 
        lastIndex = hash[lastIndex];
        temp.push_back(arr[lastIndex]);    
    }
    
    // reverse the array 
    reverse(temp.begin(),temp.end());
}