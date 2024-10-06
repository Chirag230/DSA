Given a circular integer array nums of length n, return the maximum possible sum of a non-empty subarray of nums.A circular array means the end of the array connects to the beginning of the array. Formally, the next element of nums[i] is nums[(i + 1) % n] and the previous element of nums[i] is nums[(i - 1 + n) % n].

    int solve1(vector<int>& nums,int n)
    {
        int sum=nums[0];
        int ans = nums[0];
        for(int i=1;i<n;i++)
        {
            sum = max(sum + static_cast<int>(nums[i]), static_cast<int>(nums[i]));
            ans=max(ans,sum);
        }
        return ans;
    }
    int solve2(vector<int>& nums,int n)
    {
        int sum=nums[0];
        int ans = nums[0];
        for(int i=1;i<n;i++)
        {
            sum = min(sum + static_cast<int>(nums[i]), static_cast<int>(nums[i]));
            ans=min(ans,sum);
        }
        return ans;
    }
    int maxSubarraySumCircular(vector<int>& nums) 
    {
        int n=nums.size();
        int sum=0;
        for(int i=0;i<n;i++)
        {
            sum+=nums[i];
        }
        int maxsum = solve1(nums,n);
        int minsum = solve2(nums,n);
        int op = sum-minsum;
        if(maxsum>0)
        return max(op,maxsum);
        else
        return maxsum;
    }