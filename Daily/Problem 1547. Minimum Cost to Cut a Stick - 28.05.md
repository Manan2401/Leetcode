# 1547. Minimum Cost to Cut a Stick

## Approach
 - Sort the cuts in ascending order.
 - Create a 2D array dp of size (m+2) x (m+2) (where m is the number of cuts) to store the minimum cost for each subinterval.
 - Iterate over the lengths l from 2 to m+1.
 - For each length l, iterate over the starting indices i from 0 to m+1-l.
 - Calculate the ending index j as i + l.
 - Initialize dp[i][j] with a maximum value.
 - Iterate over the cutting points k from i+1 to j-1.
 - Calculate the cost of cutting the interval [cuts[i-1], cuts[j-1]] at point cuts[k-1].
 - Update dp[i][j] by taking the minimum between the current value and the cost of the new cut.
 - Calculate the left and right lengths of the interval before and after the cuts using the indices i and j.
 - Update dp[i][j] by adding the length of the interval [cuts[i-1], cuts[j-1]].
 - Repeat steps 3-9 until all subintervals of different lengths are processed.
 - Return dp[0][m+1] as the minimum cost to cut the stick.
