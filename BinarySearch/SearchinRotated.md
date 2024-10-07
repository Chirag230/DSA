int search(vector<int>& nums, int target) 
    {
        int n=nums.size();
        int start=0;
        int end=n-1;
        int ans=-1;
        while(start<=end)
        {
            int mid = start+(end-start)/2;
            if(nums[mid]==target)
            {
                ans=mid;
                break;
            }         
            else if(nums[mid]<=nums[end])//right sorted
            {
                if(nums[mid]<=target && target<=nums[end])
                {
                    start=mid+1;
                }
                else
                {
                    end=mid-1;
                }
            }   
            else if(nums[start]<=nums[mid])//left sorted
            {
                if(nums[start]<=target && target<=nums[mid])
                {
                    end=mid-1;
                }
                else
                {
                    start=mid+1;
                }
            }
        }   
        return ans; 
    }