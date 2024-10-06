 auto comp = [&](pair<char,int>& p1, pair<char,int>& p2) {
        if(p1.first == p2.first) {
            return p1.second < p2.second;
        }
        return p1.first > p2.first;
    };