Given two strings pattern and str which may be of different size, You have to return 1 if the wildcard pattern i.e. pattern, matches with str else return 0. All characters of the string str and pattern always belong to the Alphanumeric characters.

The wildcard pattern can include the characters ? and *
‘?’ – matches any single character.
‘*’ – Matches any sequence of characters (including the empty sequence).

Note: The matching should cover the entire str (not partial str).

Examples:

Input: pattern = "ba*a?", str = "baaabab"
Output: 1
Explanation: replace '*' with "aab" and 
'?' with 'b'.
class Solution {
  public:
    /*You are required to complete this method*/
    bool solve(string pattern,string str,int i,int j)
    {
        if(i<0 && j<0)
        {
            return true;
        }
        if(i<0 && j>=0)
        {
            return false;
        }
        if(j<0 && i>=0)
        {
            for(int index=0;index<=i;i++)
            {
                if(pattern[index]!='*')
                {
                    return false;
                }
            }
            return  true;
        }
        if(pattern[i]==str[j] || pattern[i]=='?')
        {
            return solve(pattern,str,i-1,j-1);
        }
        else if(pattern[i]=='*')
        {
            return solve(pattern,str,i-1,j) || solve(pattern,str,i,j-1);
        }
        else
        {
            return false;
        }
    }
    int wildCard(string pattern, string str) 
    {
        // code here
        int n=pattern.size();
        int m=str.size();
        return solve( pattern, str,n-1,m-1);
    }
};