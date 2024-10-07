You are given an integer mountain array arr of length n where the values increase to a peak element and then decrease.

Return the index of the peak element.

Your task is to solve it in O(log(n)) time complexity.

 

Example 1:

Input: arr = [0,1,0]

Output: 1


    int peakIndexInMountainArray(vector<int>& arr) 
    {
        int n = arr.size();        
        int l = 0;
        int r = n-1;        
        while(l < r) //always 2 element ho
        {            
            int mid = l + (r-l)/2;            
            if(arr[mid] < arr[mid+1])
            l = mid+1;
            else
            r = mid;            
        }        
        return l;
    }