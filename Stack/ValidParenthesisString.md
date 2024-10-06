Given a string s containing only three types of characters: '(', ')' and '*', return true if s is valid.

The following rules define a valid string:

Any left parenthesis '(' must have a corresponding right parenthesis ')'.
Any right parenthesis ')' must have a corresponding left parenthesis '('.
Left parenthesis '(' must go before the corresponding right parenthesis ')'.
'*' could be treated as a single right parenthesis ')' or a single left parenthesis '(' or an empty string "".
 

Example 1:

Input: s = "()"
Output: true
Example 2:

Input: s = "(*)"
Output: true
Example 3:

Input: s = "(*))"
Output: true


bool checkValidString(string s) 
    {
        int n=s.size();    
        int open=0;
        for(int i=0;i<n;i++)
        {
            if(s[i]=='(' || s[i]=='*')
            {
                open++;
            }
            else if(s[i]==')')
            {
                open--;
            }
            if(open<0)
            {
                return false;
            }
        }
        int close=0;
        for(int i=n-1;i>=0;i--)
        {
            if(s[i]==')' || s[i]=='*')
            {
                close++;
            }
            else if(s[i]=='(')
            {
                close--;
            }
            if(close<0)
            {
                return false;
            }
        }
        return true;
    }





      bool checkValidString(string s) 
    {
        int n=s.size();    
        stack<int>open;
        stack<int>aster;
        for(int i=0;i<n;i++)
        {
            if(s[i]=='(')
            {
                open.push(i);
            }
            else if(s[i]=='*')
            {
                aster.push(i);
            }
            else
            {
                if(!open.empty())
                {
                    open.pop();
                }
                else if(!aster.empty())
                {
                    aster.pop();
                }
                else
                {
                    return false;
                }
            }
        }
        while(!open.empty() && !aster.empty())
        {
            if(open.top()>aster.top())
            {
                return false;
            }
            open.pop();
            aster.pop();
        }
        return open.empty();
    }