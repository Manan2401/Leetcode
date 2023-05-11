# 1035. Uncrossed Lines

## Approach:
 - The problem can be solved using dynamic programming. We can define a two-dimensional array dp, where dp[i][j] represents the maximum number of uncrossed lines between the first i elements of nums1 and the first j elements of nums2. The base case is dp[0][j] = 0 and dp[i][0] = 0, since there are no elements in either array.

 - For each element nums1[i-1] in nums1 and each element nums2[j-1] in nums2, we can either include or exclude the current element. If nums1[i-1] is equal to nums2[j-1], then we can include it in the uncrossed lines, and the maximum number of uncrossed lines is dp[i-1][j-1] + 1. Otherwise, we can exclude it, and the maximum number of uncrossed lines is the maximum of dp[i-1][j] and dp[i][j-1].

 - The final answer is dp[m][n], where m and n are the lengths of nums1 and nums2 respectively.

<br></br>
## Python Code:
```shell
class Solution:
    def maxUncrossedLines(self, nums1: List[int], nums2: List[int]) -> int:
        m, n = len(nums1), len(nums2)
        if m < n:
            nums1, nums2, m, n = nums2, nums1, n, m
        dp = [0] * (n + 1)
        for i in range(1, m + 1):
            prev = 0
            for j in range(1, n + 1):
                curr = dp[j]
                if nums1[i-1] == nums2[j-1]:
                    dp[j] = prev + 1
                else:
                    dp[j] = max(dp[j-1], curr)
                prev = curr
        return dp[n]
```
