# 2140. Solving Questions With Brainpower

## Approach:
 - We can solve this problem using dynamic programming. We'll create an array dp of length n+1 to store the maximum number of points that can be earned by starting at each question. We'll iterate through the array in reverse order, starting at index n-1, and fill in the dp array as follows:
 - For each question, we'll calculate the maximum number of points that can be earned by answering that question, and add it to the maximum number of points that can be earned by starting at the next question (i.e., the question that can be reached by jumping from the current question).
 - We'll take the maximum of the above two values and store it in dp[i].
 - Once we've filled in the dp array, the maximum number of points that can be earned by starting at the first question (i.e., the question at index 0) will be stored in dp[0].
 
 <br></br>

## Python Code:
```shell
class Solution:
    def mostPoints(self, questions: List[List[int]]) -> int:
        n = len(questions)
      
        max_points = [0] * (n + 1)
     
        for i in range(n - 1, -1, -1):
            points, jump = questions[i]
           
            next_question = min(jump + i + 1, n)
            points_from_this_question = points + max_points[next_question]
            max_points[i] = max(points_from_this_question, max_points[i + 1])
        
        return max_points[0]
```
