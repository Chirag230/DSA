 int subarraysDivByK(vector<int>& nums, int k) 
    {
        const int mod = 1e9+7;
        int n = nums.size();
        unordered_map<int,int>m;
        m[0]=1;
        int count =  0;
        int sum = 0 ;
        for(int i=0;i<n;i++)
        {
            sum +=nums[i];
            int f = sum%k;
            if(f<0)
            {
                f = f+k;
            }
            if(m.find(f)!=m.end())
            {
                count+=m[f];
            }
            m[f]++;
        }
        return count;
    }