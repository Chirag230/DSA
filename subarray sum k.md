INPUT CAN BE NEGATIVE NUMBERS
    int subarraySum(vector<int>& nums, int k) 
    {
        unordered_map<int,int>m;
        int n=nums.size();
        if(n==1 && nums[0]!=k)
        {
            return 0;
        }
        m[0]=1;
        int sum=0;
        int cnt=0;
        for(int i=0;i<n;i++)
        {
            sum+=nums[i];
            if(m.find(sum-k)!=m.end())
            {
                cnt+=m[sum-k];
            }
            m[sum]++;
        }
        return cnt;
    }