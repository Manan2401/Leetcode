# 1491. Average Salary Excluding the Minimum and Maximum Salary

## Python Code (One line):
```shell
class Solution:
    def average(self, salary: List[int]) -> float:
        return (sum(salary) - max(salary) - min(salary)) / (len(salary) - 2)
```
