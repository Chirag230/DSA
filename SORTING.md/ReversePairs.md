Given an integer array nums, return the number of reverse pairs in the array.
A reverse pair is a pair (i, j) where:
0 <= i < j < nums.length and
nums[i] > 2 * nums[j].
 

Example 1:

Input: nums = [1,3,2,3,1]
Output: 2
Explanation: The reverse pairs are:
(1, 4) --> nums[1] = 3, nums[4] = 1, 3 > 2 * 1
(3, 4) --> nums[3] = 3, nums[4] = 1, 3 > 2 * 1    
    long count = 0;

    void merge(vector<int>& nums, int start, int mid, int end) 
    {
        vector<int> temp(end - start + 1, 0);
        int i = start;
        int j = mid + 1;
        int index = 0;

        while (i <= mid && j <= end) 
        {
            if (nums[i] <= nums[j]) 
            {
                temp[index++] = nums[i++];
            } 
            else 
            {
                temp[index++] = nums[j++];
            }
        }

        while (i <= mid) 
        {
            temp[index++] = nums[i++];
        }

        while (j <= end) 
        {
            temp[index++] = nums[j++];
        }

        for (int k = start; k <= end; k++) 
        {
            nums[k] = temp[k - start];
        }
    }

    void solve(vector<int>& nums, int start, int mid, int end) 
    {
        int j = mid + 1;
        for (int i = start; i <= mid; i++) 
        {
            while (j <= end && nums[i] > 2LL * nums[j]) 
            {
                j++;
            }
            count += (j - (mid + 1));
        }
    }

    void mergesort(vector<int>& nums, int start, int end) 
    {
        if (start >= end) return;

        int mid = start + (end - start) / 2;
        mergesort(nums, start, mid);
        mergesort(nums, mid + 1, end);
        solve(nums, start, mid, end);
        merge(nums, start, mid, end);
    }

    int reversePairs(vector<int>& nums) 
    {
        count = 0;
        mergesort(nums, 0, nums.size() - 1);
        return count;
    }