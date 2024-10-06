A swap is defined as taking two distinct positions in an array and swapping the values in them.

A circular array is defined as an array where we consider the first element and the last element to be adjacent.

Given a binary circular array nums, return the minimum number of swaps required to group all 1's present in the array together at any location.

    int minSwaps(vector<int>& nums) 
    {
        int n = nums.size();
        int totalone=0;              
        for(int i=0;i<n;i++)
        {
            if(nums[i]==1)
            {
                totalone++;
            }
        }
        if(totalone==0)
        {
            return 0;
        }        
        for(int i=0;i<n;i++)
        {
            nums.push_back(nums[i]);
        }        
        int i=0;
        int j=0;
        int mini=INT_MAX;
        int one=0;
        while(j<2*n)
        {
            if(nums[j]==1)
            {
                one++;
            }
            while(j-i+1<totalone)
            {
                j++;
                if(nums[j]==1)
                {
                    one++;
                }
            }
            if(j-i+1==totalone)
            {
                mini=min(mini,totalone-one);    
                if(nums[i] == 1) 
                {
                    one--;
                }           
                i++;                                           
            }
            j++;  
        }
        return mini;
    }