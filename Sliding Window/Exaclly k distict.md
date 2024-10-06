Given a string of lowercase alphabets, count all possible substrings (not necessarily distinct) that have exactly k distinct characters. 

Example 1:

Input: S = "aba", K = 2
Output:3
Explanation:The substrings are: "ab", "ba" and "aba".
Input: S = "abaaca", K = 1
Output: 7
Explanation: The substrings are: "a", "b", "a", "aa", "a", "c", "a". 

long long int solve(string &s,int k)
    {
        int n=s.size();
    	int start=0;
    	int end=0;
    	long long int count=0;
    	unordered_map<char,int>m;
    	while(end<n)
    	{
    	    m[s[end]]++;
    	    while(m.size()>k)
    	    {
    	        m[s[start]]--;
    	        if(m[s[start]]==0)
    	        {
    	            m.erase(s[start]);
    	        }
    	        start++;
    	       // cout<<start<<" ";
    	    }
    	    count+=end-start+1;
    	    end++;
    	}
    	return count;
    }
    long long int substrCount (string s, int k) 
    {
    	//code here.
    	return solve(s,k)-solve(s,k-1);
    }