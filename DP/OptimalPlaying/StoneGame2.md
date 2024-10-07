Alice and Bob continue their games with piles of stones.  There are a number of piles arranged in a row, and each pile has a positive integer number of stones piles[i].  The objective of the game is to end with the most stones. 
Alice and Bob take turns, with Alice starting first.  Initially, M = 1.
On each player's turn, that player can take all the stones in the first X remaining piles, where 1 <= X <= 2M.  Then, we set M = max(M, X).
The game continues until all the stones have been taken.
Assuming Alice and Bob play optimally, return the maximum number of stones Alice can get.

int n;

int solveforAlice(vector<int>& piles, int person, int index, int M, vector<vector<vector<int>>>& dp) 
{
    if (index >= piles.size()) 
    {
        return 0;
    }
    if (dp[person][index][M] != -1) 
    {
        return dp[person][index][M];
    }

    int stones = 0;
    int result = (person == 1) ? -1 : INT_MAX;

    for (int x = 1; x <= min(2 * M, n - index); x++) 
    {
        stones += piles[index + x - 1];
        if (person == 1) 
        {
            result = max(result, stones + solveforAlice(piles, 0, index + x, max(M, x), dp));
        } 
        else 
        {
            result = min(result, solveforAlice(piles, 1, index + x, max(M, x), dp));
        }
    }

    return dp[person][index][M] = result;
}

int stoneGameII(vector<int>& piles) 
{
    n = piles.size();
    vector<vector<vector<int>>> dp(2, vector<vector<int>>(n + 1, vector<int>(n + 1, -1)));
    return solveforAlice(piles, 1, 0, 1, dp);
}