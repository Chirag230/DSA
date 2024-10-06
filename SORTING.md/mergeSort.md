 void merge(int arr[], int low, int mid, int high)
    {
         // Your code here
        int temp[high - low + 1];
        int index=0;
        int left=low;
        int right=mid+1;
        while(left<=mid && right<=high)
        {
            if(arr[left]<=arr[right])
            {
                temp[index]=arr[left];
                index++;
                left++;
            }
            else
            {
                temp[index]=(arr[right]);
                index++;
                right++;
            }        
        }
        while(left<=mid)
        {
            temp[index]=(arr[left]);
            index++;
            left++;
        }
        while(right<=high)
        {
            temp[index]=(arr[right]);
            index++;
            right++;
        }
        for(int i=low;i<=high;i++)
        {
            arr[i]=temp[i-low];
        }
    }
    public:
    void mergeSort(int arr[], int l, int r)
    {
        //code here
         if(l>=r)
        return;
        int mid=(r+l)/2;
        mergeSort(arr,l,mid);
        mergeSort(arr,mid+1,r);
        merge(arr,l,mid,r);
    }