This is basically DERIVED  from Longest INCREASING SUBSEQUENCE!!

int alternatingMaxLength(vector<int>& arr) 
{
    // Code here
    int n = arr.size();
    int las[n][2];
    for (int i = 0; i < n; i++)
    {
        las[i][0] = las[i][1] = 1;
    }
    int res = 1;
    for (int i = 1; i < n; i++) 
    {
        for (int j = 0; j < i; j++) 
        {
            if (arr[j] < arr[i] && las[i][0] < las[j][1] + 1)
                las[i][0] = las[j][1] + 1;
    
            if (arr[j] > arr[i] && las[i][1] < las[j][0] + 1)
                las[i][1] = las[j][0] + 1;
        }
        if (res < max(las[i][0], las[i][1]))
            res = max(las[i][0], las[i][1]);
    }
    return res;
}