You are given an integer array nums. Two players are playing a game with this array: player 1 and player 2.
Player 1 and player 2 take turns, with player 1 starting first. Both players start the game with a score of 0. At each turn, the player takes one of the numbers from either end of the array (i.e., nums[0] or nums[nums.length - 1]) which reduces the size of the array by 1. The player adds the chosen number to their score. The game ends when there are no more elements in the array.
Return true if Player 1 can win the game. If the scores of both players are equal, then player 1 is still the winner, and you should also return true. You may assume that both players are playing optimally.

2 approach!!!!!

 int solveforAlice(vector<int>&nums,int i,int j)
    {
        if(i>j)
        return 0;

        int op1 = nums[i]  + min(solveforAlice(nums,i+2,j),solveforAlice(nums,i+1,j-1));
        int op2 = nums[j]  +min(solveforAlice(nums,i+1,j-1),solveforAlice(nums,i,j-2));

        return max(op1,op2);
    }
    bool predictTheWinner(vector<int>& nums) 
    {
        int n=nums.size();
        int sum=0;
        for(int i=0;i<n;i++)
        {
            sum+=nums[i];
        }
        int s = solveforAlice(nums,0,n-1);
        if(s>=sum-s)
        {
            return true;
        }
        else
        return false;
    }



     int n;
    int t[23][23];
    
    //Player1 - Player2
    int maxDiff(vector<int>& nums, int l, int r) {
        
        if(l == r)
            return nums[l];
        
        if(t[l][r] != -1)
            return t[l][r];
        
        int take_left  = nums[l] - maxDiff(nums, l+1, r);
        int take_right = nums[r] - maxDiff(nums, l, r-1);
        
        return t[l][r] = max(take_left, take_right);
    }
    
    bool PredictTheWinner(vector<int>& nums) {
        n = nums.size();
        memset(t, -1, sizeof(t));
        return maxDiff(nums, 0, n-1) >= 0;
            
    }