Given a string s, find the length of the longest substring without repeating characters.

 int lengthOfLongestSubstring(string s) 
    {
        int n = s.size();
        int i=0;
        int j=0;
        unordered_map<char,int>m;
        int len=0;
        while(j<n)
        {
            
            m[s[j]]++;
            while(j-i+1 > m.size())
            {
                m[s[i]]--;
                if(m[s[i]]==0)
                {
                    m.erase(s[i]);
                }
                i++;
            }
            
            len=max(len,j-i+1);
            j++;
        }    
        return len;
    }