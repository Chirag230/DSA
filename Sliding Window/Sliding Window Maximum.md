 vector<int> maxSlidingWindow(vector<int>& nums, int k) 
{
    int n = nums.size();
    vector<int>ans;
    deque<int>deq;
    for(int i=0;i<n;i++)
    {
        while(!deq.empty() && deq.front()<=i-k)
        {
            deq.pop_front();
        }
        while(!deq.empty() && nums[i]>nums[deq.back()])
        {
            deq.pop_back();
        }
        deq.push_back(i);
        if(i+1-k>=0)
        {
            ans.push_back(nums[deq.front()]);
        }
    }
    return ans;
}


MONOTONIC DECREASING STACK