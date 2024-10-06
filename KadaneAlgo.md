INTEGERS CAN BE NEGATIVE ALSO



  int maxSubArray(vector<int>& nums) 
    {
        int n = nums.size();
        int sum=nums[0];
        int ans=nums[0];
        for(int i=1;i<n;i++)
        {
            sum=max(sum+nums[i],nums[i]);
            ans=max(ans,sum);
        }   
        return ans;
    }

    2nd  solution

class Solution {
public:
    int maxSubArray(vector<int>& arr) 
    {
        int n = arr.size();
        long long maxi = LONG_MIN; 
        long long sum = 0;

        int start = 0;
        int ansStart = -1, ansEnd = -1;
        for (int i = 0; i < n; i++) 
        {
            if (sum == 0) start = i; 
            sum += arr[i];
            if (sum > maxi) 
            {
                maxi = sum;
                ansStart = start;
                ansEnd = i;
            }
            if (sum < 0) 
            {
                sum = 0;
            }
        }

        cout<<"ARRAY STARTS AT"<<ansStart<<endl;
        cout<<"ARRAY END AT"<<ansEnd<<endl;
        return maxi;
    }
};