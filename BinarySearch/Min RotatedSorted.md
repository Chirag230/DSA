   int findMin(vector<int>& arr) 
    {
        int n=arr.size();
        int ans=5001;
        int low=0;
        int high=n-1;
        while(low<=high)
        {
            int mid = low+(high-low)/2;
            if(arr[mid]<=arr[high])
            {
                ans=min(ans,arr[mid]);
                high=mid-1;
            }
            else if(arr[mid]>=arr[low])
            {
                ans=min(ans,arr[low]);
                low=mid+1;
            }
        }    
        return ans;
    }