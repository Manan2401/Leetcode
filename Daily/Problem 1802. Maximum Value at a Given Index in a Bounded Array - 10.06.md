# 1802. Maximum Value at a Given Index in a Bounded Array

## Approach

 - Pick a sum at index, we can check if it works in O(1) by calculating the sum to the left and the sum to the right in O(1).

 - We can calculate the sum from 4 to 6 like this:
```
    (1 + 2 + 3 + 4 + 5 + 6)
-   (1 + 2 + 3)
-------------------------------
                 4 + 5 + 6
```

 - And the sum from 1 to n can be calculated using this equation n * (n + 1) / 2.

 - Now use binary search to find the maximum possible value at index.


<br></br>
## Python Code
```shell
class Solution:
    def maxValue(self, n: int, index: int, maxSum: int) -> int:
        def calc_sum(cnt, end):
            if cnt == 0:
                return 0
            start = max(end - cnt, 0)
            sum1 = end * (1 + end) // 2
            sum2 = start * (1 + start) // 2
            return sum1 - sum2

        maxSum -= n
        l, r = 0, maxSum
        while l <= r:
            mid = (l + r) // 2
            left_sum = calc_sum(index + 1, mid)
            right_sum = calc_sum(n - index - 1, mid - 1)
            if left_sum + right_sum <= maxSum:
                l = mid + 1
            else:
                r = mid - 1
        return l


```
