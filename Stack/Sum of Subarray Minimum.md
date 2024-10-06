Given an array of integers arr, find the sum of min(b), where b ranges over every (contiguous) subarray of arr. Since the answer may be large, return the answer modulo 109 + 7.
Example 1:
Input: arr = [3,1,2,4]
Output: 17
Explanation: 
Subarrays are [3], [1], [2], [4], [3,1], [1,2], [2,4], [3,1,2], [1,2,4], [3,1,2,4]. 
Minimums are 3, 1, 2, 4, 1, 1, 2, 1, 1, 1.
Sum is 17


    int sumSubarrayMins(vector<int>& arr) 
    {
        const int MOD=1e9+7;
        vector<int>nsr;
        stack<pair<int,int>>s;
        int n=arr.size();
        for(int i=n-1;i>=0;i--)
        {
            if(s.empty())
            {
                nsr.push_back(n);
            }
            else if( s.size()>0 && s.top().first<=arr[i])
            {
                nsr.push_back(s.top().second);
            }
            else if(s.size()>0 && s.top().first>arr[i])
            {
                while( s.size()>0 && s.top().first>arr[i])
                {
                    s.pop();
                }
                if(s.empty())
                {
                    nsr.push_back(n);
                }
                else 
                {
                    nsr.push_back(s.top().second);
                }
            }
            s.push({arr[i],i});
        }
        reverse(nsr.begin(),nsr.end());
        
        for(int i=0;i<n;i++)
        {
            cout<<nsr[i]<<"::";
        }
        vector<int>nsl;
        stack<pair<int,int>>s1;
        for(int i=0;i<n;i++)
        {
            if(s1.empty())
            {
                nsl.push_back(-1);
            }
            else if( s1.size()>0 && s1.top().first<arr[i])
            {
                nsl.push_back(s1.top().second);
            }
            else if(s1.size()>0 && s1.top().first>=arr[i])
            {
                while( s1.size()>0 && s1.top().first>=arr[i])
                {
                    s1.pop();
                }
                if(s1.empty())
                {
                    nsl.push_back(-1);
                }
                else 
                {
                    nsl.push_back(s1.top().second);
                }
            }
            s1.push({arr[i],i});
        }
       long long ans = 0;
        for (int i = 0; i < n; i++)
        {
            int left = i - nsl[i];
            int right = nsr[i] - i;
            ans = (ans + (long long)left * right * arr[i]) % MOD;
        }
        
        return (int)ans;
    }