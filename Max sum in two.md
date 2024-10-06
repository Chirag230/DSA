Given two sorted arrays of distinct integers arr1 and arr2. Each array may have some elements in common with the other array. Find the maximum sum of a path from the beginning of any array to the end of any array. You can switch from one array to another array only at the common elements.

Note:  When we switch from one array to other,  we need to consider the common element only once in the result.

Examples : 

Input: arr1 = [2, 3, 7, 10, 12] , arr2 = [1, 5, 7, 8]
Output: 35


int maxPathSum(vector<int> &arr1, vector<int> &arr2) 
    {
        // Code here
        int i=0;
        int j=0;
        int sum1=0;
        int sum2=0;
        int ans=0;
        while(i<arr1.size() && j<arr2.size())
        {
            if(arr1[i]<arr2[j])
            {
                sum1+=arr1[i];
                i++;
            }
            else if(arr2[j]<arr1[i])
            {
                sum2+=arr2[j];
                j++;
            }
            if(arr1[i]==arr2[j])
            {
                ans+=max(sum1,sum2)+arr1[i];
                i++;
                j++;
                sum1=0;
                sum2=0;
            }
        }
        while(i<arr1.size())
        {
            sum1+=arr1[i];
            i++;
        }
        while(j<arr2.size())
        {
            sum2+=arr2[j];
            j++;
        }
        ans+=max(sum1,sum2);
        return ans;
    }