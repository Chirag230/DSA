Given two strings s and t, return the number of distinct subsequences of s which equals t.

The test cases are generated so that the answer fits on a 32-bit signed integer.

 

Example 1:

Input: s = "rabbbit", t = "rabbit"
Output: 3
Explanation:
As shown below, there are 3 ways you can generate "rabbit" from s.
rabbbit
rabbbit
rabbbit


   int solve(string s,string t,int i,int j)
    {
        if(j<0)
        {
            return 1;
        }
        if(i<0)
        {
            return 0;
        }
        if(s[i]==t[j])
        {
            return solve(s,t,i-1,j-1)+solve(s,t,i-1,j);
        }
        else
        {
            return solve(s,t,i-1,j);
        }
    }
    int numDistinct(string s, string t) 
    {
        int n=s.size();
        int m=t.size();    
        return solve(s,t,n-1,m-1);
    }