Given two strings s and t of lengths m and n respectively, return the minimum window substring of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".

   string minWindow(string s, string t) 
    {
        int n = s.size();
        int m = t.size();   
        if(n<m) return "";
        if(s==t)    return s;
        unordered_map<char,int>m1;
        for(int i=0;i<m;i++)
        {
            m1[t[i]]++;
        } 
        int count=m;
        int i=0;
        int j=0;
        int len=INT_MAX;
        int start_index=-1;
        while(j<n)
        {
            if(m1[s[j]]>0)
            {
                count--;
            }
            m1[s[j]]--;
            while(count==0)
            {
                if(j-i+1 < len)
                {
                    len=j-i+1;
                    start_index=i;
                }

                m1[s[i]]++;
                if(m1[s[i]]>0)
                {
                    count++;
                }
                i++;
            }
            j++;
        }
        if(len==INT_MAX)
        return "";
        else
        return s.substr(start_index,len);
    }