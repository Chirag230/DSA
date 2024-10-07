Given an array of non-negative integers arr, you are initially positioned at start index of the array. When you are at index i, you can jump to i + arr[i] or i - arr[i], check if you can reach any index with value 0.

Notice that you can not jump outside of the array at any time.
Input: arr = [4,2,3,0,3,1,2], start = 5
Output: true
Explanation: 
All possible ways to reach at index 3 with value 0 are: 
index 5 -> index 4 -> index 1 -> index 3 
index 5 -> index 6 -> index 4 -> index 1 -> index 3 

    bool solve(vector<int>&arr,int start,int n,unordered_set<int>&s)
    {
        if(start>=n)
        {
            return false;
        }
        if(start<0)
        {
            return false;
        }
        if(s.find(start)!=s.end())//cycle
        {
            return false;
        }
        s.insert(start);
        if(arr[start]==0)
        {
            return true;
        }
        bool op1=solve(arr,start-arr[start],n,s);
        bool op2=solve(arr,start+arr[start],n,s);
        return op1||op2;
    }
    bool canReach(vector<int>& arr, int start) 
    {
        int n=arr.size();
        if(arr[start]==0)
        return true;
        unordered_set<int>s;
        return solve(arr,start,n,s);    
    }