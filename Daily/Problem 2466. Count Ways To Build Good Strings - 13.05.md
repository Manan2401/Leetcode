# 2466. Count Ways To Build Good Strings

## Approach:
 - The problem can be solved using dynamic programming. We can define dp[i] as the total number of valid strings of length i. A valid string is one that contains no more than k consecutive identical characters, where k is the minimum of the number of zeros and the number of ones.

 - We can compute dp[i] by considering all the valid strings of length i-1. To count the number of valid strings of length i that end with a zero, we can count the number of valid strings of length i-1 that end with a one, and vice versa. We can then add these two values to get dp[i].

 - Finally, we can compute the answer as the sum of dp[i] for i = low to high.

<br></br>
## Python Code:
```shell
from collections import Counter

class Solution:
    def countGoodStrings(self, low: int, high: int, zero: int, one: int) -> int:
        dp = Counter({0: 1})
        mod = 10 ** 9 + 7
        for i in range(1, high + 1):
            z = dp[i - zero]
            o = dp[i - one]
            n = (z + o) % mod
            dp[i] = n
        
        ans = sum(dp[i] for i in range(low, high + 1)) % mod
        return ans
```
