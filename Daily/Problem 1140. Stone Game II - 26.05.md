# 1140. Stone Game II


## Approach:
 - Use dynamic programming to solve the problem. Create a 2D DP table to store the results of subproblems.
 - Initialize the DP table with the base cases where there are no more piles to choose from.
 - Iterate from the end of the piles array towards the beginning, considering different maximum numbers of stones the current player can take.
 - For each position and maximum number of stones, calculate the maximum score the current player can achieve by trying all possible moves and considering the opponent's score.
 - Use the suffix sums of the remaining piles to optimize the calculations.
 - Return the maximum score the first player can achieve starting from the first index with a maximum of 1 stone to take.


<br></br>
## Python Code:

```shell
class Solution:
    def stoneGameII(self, piles):
        n = len(piles)
        suffix_sums = [0] * (n + 1)
        suffix_sums[n - 1] = piles[n - 1]
        for i in range(n - 2, -1, -1):
            suffix_sums[i] = suffix_sums[i + 1] + piles[i]

        dp = [[0] * (n + 1) for _ in range(n)]

        for i in range(n - 1, -1, -1):
            for m in range(1, n + 1):
                if i + 2 * m >= n:
                    dp[i][m] = suffix_sums[i]
                else:
                    for x in range(1, 2 * m + 1):
                        opponent_score = dp[i + x][max(x, m)]
                        score = suffix_sums[i] - opponent_score
                        dp[i][m] = max(dp[i][m], score)
        
        return dp[0][1]
```
