# 1572. Matrix Diagonal Sum

## Python Code:
```shell
class Solution:
    def diagonalSum(self, mat: List[List[int]]) -> int:
        size = len(mat)
        index = 0
        diagonal_sum = 0

        for j in range(size):
            diagonal_sum += mat[j][index] + mat[j][size - index - 1]
            index += 1

        if size % 2 == 1:
            diagonal_sum -= mat[size // 2][size // 2]

        return diagonal_sum
```
