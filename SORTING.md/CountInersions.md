Given an integer array arr[] of size n, the task is to find the count inversions of the given array. Two array elements arr[i] and arr[j] form an inversion if arr[i] > arr[j] and i < j.


 long long int  count=0;
    void merge(long long arr[],int start,int mid,int end)
    {
        long long temp[end-start+1];
        int i=start;
        int j=mid+1;
        int index=0;
        while(i<=mid && j<=end)
        {
            if(arr[i]<=arr[j])
            {
                temp[index]=arr[i];
                i++;
                index++;
            }
            else
            {
                temp[index]=arr[j];
                count+=mid-i+1;
                j++;
                index++;
            }
        }
        while(i<=mid)
        {
            temp[index]=(arr[i]);
            index++;
            i++;
        }
        while(j<=end)
        {
            temp[index]=(arr[j]);
            index++;
            j++;
        }
        for(int k=start;k<=end;k++)
        {
            arr[k]=temp[k-start];
        }
    }
    void mergesort(long long arr[],int start,int end)
    {
        if(start>=end)
        return;
        int mid = (start+end)/2;
        mergesort(arr,start,mid);
        mergesort(arr,mid+1,end);
        merge(arr,start,mid,end);
    }
    long long int inversionCount(long long arr[], int n) 
    {
        // Your Code Here
        int start = 0;
        int end = n-1;
        mergesort(arr,start,end);
        return count;
    }