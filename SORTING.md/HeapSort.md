Heap sort is NOT at all a Divide and Conquer algorithm. It uses a heap data structure to efficiently sort its element and not a “divide and conquer approach” to sort the elements.  

    void heapify(int arr[], int n, int i)  
    {
      // Your Code Here
       int largest = i;
        int l=2*i+1;
        int r=2*i+2;
        
        if(l<n && arr[l]>arr[largest])
        largest = l;
        
        if(r<n && arr[r]>arr[largest])
        largest = r;
        
        if(largest!=i)
        {
            swap(arr[i],arr[largest]);
            heapify(arr,n,largest);
        }
    }

    public:
    //Function to build a Heap from array.
    void buildHeap(int arr[], int n)  
    { 
    // Your Code Here
    for(int i=(n/2)-1;i>=0;i--)
        heapify(arr,n,i);
    }

    
    public:
    //Function to sort an array using Heap Sort.
    void heapSort(int arr[], int n)
    {
        //code here
          buildHeap(arr,n);
         for(int i=n-1;i>0;i--)
         {
            swap(arr[i],arr[0]);
            heapify(arr,i,0);
         }
    }