# 744. Find Smallest Letter Greater Than Target

## Python Code
```shell
class Solution:
    def nextGreatestLetter(self, letters: List[str], target: str) -> str:
        for i in letters:
            if i > target:
                return i
        return letters[0]
```
