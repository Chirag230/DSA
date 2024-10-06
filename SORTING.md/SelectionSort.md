Selection sort is a simple and efficient sorting algorithm that works by repeatedly selecting the smallest (or largest) element from the unsorted portion of the list and moving it to the sorted portion of the list. 

void selectionSort(int arr[], int n)
    {
       //code here
       for(int i=0;i<n;i++)
       {
           int index=i;
           for(int j=i+1;j<n;j++)
           {
               if(arr[j]<arr[index])
               {
                   index=j;
               }
           }
           if(index!=i)
           {
               swap(arr[i],arr[index]);
           }
       }
    }