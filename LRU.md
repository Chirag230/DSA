class LRUCache {
public:
    list<int>dll;
    unordered_map<int,pair<list<int>::iterator,int>>m;
    int n;
    LRUCache(int capacity) 
    {
        this->n=capacity;
    }
    void solve(int key)
    {
       dll.erase(m[key].first);
        dll.push_front(key);
        m[key].first=dll.begin();
    }
    int get(int key) 
    {
        if(m.find(key)==m.end())
        {
            return -1;
        }    

        solve(key);
        return m[key].second;
    }
    
    void put(int key, int value) 
    {
        if(m.find(key)!=m.end()) 
        {
            m[key].second=value;
            solve(key);
        }  
        else
        {
            dll.push_front(key);
            m[key]={dll.begin(),value};
            n--;
        }
        if(n<0)
        {
            int f = dll.back();
            m.erase(f);
            dll.pop_back();
            n++;
        }
    }
};