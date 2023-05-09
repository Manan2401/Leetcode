# 54. Spiral Matrix


## Brute Force Approach:
Use a stack and a 2D array to traverse the matrix in spiral order. It starts at the top-left corner of the matrix and pushes the coordinates onto the stack. It then pops the coordinates from the stack and checks if they are within the boundaries of the matrix and if they have been visited before. If they have not been visited, the value at that coordinate is added to the answer list and the coordinate is marked as visited. The program then checks the next coordinate in the direction of traversal (which is determined by the direction array) and pushes it onto the stack. If the next coordinate is out of bounds or has been visited before, the direction of traversal is changed by incrementing the index of the direction array. The program continues to pop coordinates from the stack until it is empty, at which point it returns the answer list.

## Code:
```shell
def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
  m = len(matrix)
  n = len(matrix[0])
  answer = []
  direction = [[1,0],[0,-1],[-1,0],[0,1]]
  visited = []
  for i in range(m):
      visited.append([0]*n)
  def traverse(coord, index):
      if coord[0] >= m or coord[0] < 0 or coord[1] >= n or coord[0] < 0 or visited[coord[0]][coord[1]] == 1:
          return
      answer.append(matrix[coord[0]][coord[1]])
      visited[coord[0]][coord[1]] = 1
      coord2 = [a + b for a, b in zip(coord, direction[index])]
      if coord2[0] >= m or coord2[0] < 0 or coord2[1] >= n or coord2[0] < 0 or visited[coord2[0]][coord2[1]] == 1:
          index = (index + 1) % 4
      coord2 = [a + b for a, b in zip(coord, direction[index])]
      traverse(coord2, index)
  traverse([0,0],3)
  return answer
```
## Complexity:
### Time:
O(M*N)
### Space:
O(M*N)
<br></br>

## Optimal Approach:
We start by initializing the top, bottom, left, and right pointers to the edges of the matrix. We then use a single loop to traverse the matrix in a spiral order by moving the pointers inward after each traversal. We continue this process until we have visited all elements of the matrix.

## Code:
```shell
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        result = []
        if not matrix or not matrix[0]:
            return result
        m, n = len(matrix), len(matrix[0])
        top, bottom, left, right = 0, m - 1, 0, n - 1
        while top <= bottom and left <= right:
            # Traverse right
            for i in range(left, right + 1):
                result.append(matrix[top][i])
            top += 1
            # Traverse down
            for i in range(top, bottom + 1):
                result.append(matrix[i][right])
            right -= 1
            # Traverse left
            if top <= bottom:
                for i in range(right, left - 1, -1):
                    result.append(matrix[bottom][i])
                bottom -= 1
            # Traverse up
            if left <= right:
                for i in range(bottom, top - 1, -1):
                    result.append(matrix[i][left])
                left += 1
        return result
```
<br></br>
## Python 1-line code:
```shell
def spiralOrder(self, matrix):
    return matrix and [*matrix.pop(0)] + self.spiralOrder([*zip(*matrix)][::-1])
```
## Complexity:
### Time:
O(M*N)
### Space:
O(1)
