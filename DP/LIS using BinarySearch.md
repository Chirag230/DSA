vector<char> temp;
        int len = 1;
        temp.push_back(s[0]);
        
        for(int i = 1; i < s.size(); i++)
        {
            if (s[i] > temp.back())
            {
                len++;
                temp.push_back(s[i]);
            }
            else
            {
                auto it = std::lower_bound(temp.begin(), temp.end(), s[i]);
                *it = s[i];
            }
        }    
    return len;