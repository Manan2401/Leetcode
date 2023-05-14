# 1799. Maximize Score After N Operations

## Approach:
 - The given problem can be solved using dynamic programming. The basic idea is to consider all possible pairs of numbers in the given array and calculate their gcd. Then, we can use a bitmask to represent all possible subsets of indices and use dynamic programming to calculate the maximum score for each subset.

 - To calculate the maximum score for a given subset of indices, we can iterate over all possible pairs of indices in the subset and calculate their gcd. We can then add the product of this gcd and half the number of indices in the subset to the maximum score for the subset obtained by removing these indices from the original subset.

 - The maximum score for the original subset can then be obtained by considering all possible subsets of indices and choosing the one with the maximum score.\

<br></br>
## Python Code:
```shell
class Solution:
    def maxScore(self, nums: List[int]) -> int:
        n = len(nums)
        gcd_matrix = [[0] * n for _ in range(n)]
        for i in range(n):
            for j in range(i+1, n):
                gcd_matrix[i][j] = gcd_matrix[j][i] = gcd(nums[i], nums[j])
        
        dp = [0] * (1 << n)
        for state in range(1, 1 << n):
            cnt = bin(state).count('1')
            if cnt % 2 == 1:
                continue
            for i in range(n):
                if not (state & (1 << i)):
                    continue
                for j in range(i+1, n):
                    if not (state & (1 << j)):
                        continue
                    nextState = state ^ (1 << i) ^ (1 << j)
                    dp[state] = max(dp[state], dp[nextState] + cnt // 2 * gcd_matrix[i][j])
        return dp[(1 << n) - 1]
```
