# 1140. Stone Game II


## Approach:
 - Use dynamic programming to solve the problem. Create a 2D DP table to store the results of subproblems.
 - Initialize the DP table with the base cases where there are no more piles to choose from.
 - Iterate from the end of the piles array towards the beginning, considering different maximum numbers of stones the current player can take.
 - For each position and maximum number of stones, calculate the maximum score the current player can achieve by trying all possible moves and considering the opponent's score.
 - Use the suffix sums of the remaining piles to optimize the calculations.
 - Return the maximum score the first player can achieve starting from the first index with a maximum of 1 stone to take.
