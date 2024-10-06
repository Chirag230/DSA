 vector<int> majorityElement(vector<int>& nums) 
    {
        int n = nums.size();
        vector<int>ans;        
        if(n==1)
        {
            ans.push_back(nums[0]);
            return ans;
        }
        int element1=0;
        int count1=0;
        int element2=0;
        int count2=0;
       

        for(int i=0;i<n;i++)
        {
           if (nums[i] == element1) 
           {
                count1++;
           } 
            else if (nums[i] == element2) 
            {
                count2++;
            } 
            else if (count1 == 0) 
            {
                element1 = nums[i];
                count1 = 1;
            } 
            else if (count2 == 0) 
            {
                element2 = nums[i];
                count2 = 1;
            } 
            else 
            {
                count1--;
                count2--;
            }           
        }
        count1 = 0;
        count2 = 0;
        for (int i : nums) 
        {
            if (i == element1) 
            {
                count1++;
            } 
            else if (i == element2) 
            {
                count2++;
            }
        }

        if (count1 > n / 3) 
        {
            ans.push_back(element1);
        }
        if (count2 > n / 3) 
        {
            ans.push_back(element2);
        }

        return ans;
    }