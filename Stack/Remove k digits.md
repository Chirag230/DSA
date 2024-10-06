Given string num representing a non-negative integer num, and an integer k, return the smallest possible integer after removing k digits from num.

Example 1:

Input: num = "1432219", k = 3
Output: "1219"
Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.


   string removeKdigits(string num, int k) {
        stack<char> st;
        int n=num.length();
        for(int i=0;i<n;i++)
        {
            if(st.empty())
            {
                st.push(num[i]);
            }
            else if(st.top()>num[i])
            {
                while(!st.empty() &&  st.top()>num[i] && k>0)
                {
                    st.pop();
                    k--;
                }
                st.push(num[i]);
            }
            else if(st.top()<=num[i])
                st.push(num[i]);
        }
        while(k>0)
        {
            st.pop();
            k--;
        }
        string ans;
        while(!st.empty())
        {
            ans.push_back(st.top());
            st.pop();
        }
        reverse(ans.begin(),ans.end());
        if(ans=="") return"0";
       int i = 0;
        while (ans[i] == '0') 
        {
            i++;
        }
    return (i < ans.size()) ? ans.substr(i) : "0";

        return ans;
    }