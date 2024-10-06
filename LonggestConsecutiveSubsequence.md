class Solution {
public:
    int longestConsecutive(vector<int>& nums) 
    {
        int n=nums.size();
        if(n==0)    
        return 0;
        unordered_set<int>s;
        for(int i=0;i<n;i++)
        {
            s.insert(nums[i]);
        }    
        int maxi=0;
        for(auto i:s)
        {
            if(s.find(i-1)==s.end())
            {
                int count=1;
                int small=i;
                while(s.find(small+1)!=s.end())
                {
                    count=count+1;
                    small=small+1;
                }
                maxi=max(maxi,count);
            }
        }
        return maxi;
    }
};