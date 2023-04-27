# 319. Bulb Switcher

## Intuition
 - A light switch is a toggle with two states,offandon, and in this problem the initial state isoff, so reason tells us that the bulbs that will beonat the end are those with an odd number of divisors.
 - Consider lightbulbk, where0 <= k <= n-1. For every divisordofk, d//k is also a divisor, and reason also tells us thatd*(d//k) = k. Also,kcan have an odd number of distinct divisors if and only ifk = d*dfor exactly one divisord, which is true if and only if kis a perfect square.
 - From 2) above, the answer to the problem is the integer part of the square root ofn.
 
 ## Python Code:
 ```shell
 class Solution:     
    def bulbSwitch(self, n: int) -> int:
        return isqrt(n) 
 ```
 
 
