Number of next greater elements to the right of the given index element. 
void merge(vector<pair<int, int>>& v, int start, int mid, int end, vector<int>& count) 
{
    vector<pair<int, int>> t;
    int i = start;
    int j = mid + 1;
    int k = 0;

    while (i <= mid && j <= end) 
    {
        if (v[i].first < v[j].first) 
        {
            t.push_back(v[i]);
            count[v[i].second] += end - j + 1;
            i++;
        } 
        else 
        {
            t.push_back(v[j]);
            j++;
        }
    }

    while (i <= mid) 
    {
        t.push_back(v[i]);
        i++;
    }

    while (j <= end) 
    {
        t.push_back(v[j]);
        j++;
    }

    for (int q = start; q <= end; q++) 
    {
        v[q] = t[q - start];
    }
}

void mergeSort(vector<pair<int, int>>& v, vector<int>& count, int start, int end) 
{
    if (start < end) 
    {
        int mid = (start + end) / 2;
        mergeSort(v, count, start, mid);
        mergeSort(v, count, mid + 1, end);
        merge(v, start, mid, end, count);
    }
}

vector<int> count_NGE(int n, vector<int>& arr, int queries, vector<int>& indices) {
    vector<pair<int, int>> v;
    for (int i = 0; i < n; i++) 
    {
        v.push_back({arr[i], i});
    }

    vector<int> count(n, 0);
    mergeSort(v, count, 0, n - 1);

    vector<int> ans;
    for (int i = 0; i < queries; i++) 
    {
        ans.push_back(count[indices[i]]);
    }

    return ans;
}