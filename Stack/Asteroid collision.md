  vector<int> asteroidCollision(vector<int>& asteroids) 
    {
        int n =  asteroids.size();
        stack<int>st;
        for(int i=0;i<n;i++)
        {
            while(!st.empty() && asteroids[i]<0 && st.top()>0)
            {
                int sum = st.top()+asteroids[i];
                if(sum==0)
                {
                    asteroids[i]=0;
                    st.pop();
                }
                else if(sum>0)
                {
                    asteroids[i]=0;
                }
                else if(sum<0)
                {
                    st.pop();
                }
            }
            if(asteroids[i]!=0)
            {
                st.push(asteroids[i]);
            }
        }
        vector<int>ans(st.size());
        for(int i=ans.size()-1;i>=0;i--)
        {
            ans[i]=st.top();
            st.pop();
        }
        return ans;
    }

We are given an array asteroids of integers representing asteroids in a row.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.
Example 1:

Input: asteroids = [5,10,-5]
Output: [5,10]
Explanation: The 10 and -5 collide resulting in 10. The 5 and 10 never collide.