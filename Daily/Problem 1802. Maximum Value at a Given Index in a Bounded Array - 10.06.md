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
