# 1318. Minimum Flips to Make a OR b Equal to c

## Approach
Consider the i'th bit of c. There are two cases:

 - The i'th bit is equal to 0
This means the i'th bit in a and b must both be 0. We need to flip any of the 1-bits to 0.

 - The i'th bit is equal to 1
This means either the i'th bit in a or the i'th bit in b must be 1. If neither are 1, we must flip at least one bit.  

<br></br>
## Python Code
```shell
class Solution:
    def minFlips(self, a: int, b: int, c: int) -> int:
        flip = 0
        for i in range(31):
            if (c >> i) & 1:
                flip += ((a >> i) & 1) == 0 and ((b >> i) & 1) == 0
            else:
                flip += (a >> i) & 1
                flip += (b >> i) & 1
        return flip
```
