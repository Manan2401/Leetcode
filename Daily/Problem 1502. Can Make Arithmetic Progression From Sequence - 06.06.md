# 1502. Can Make Arithmetic Progression From Sequence

## Python Code:
```shell
class Solution:
    def canMakeArithmeticProgression(self, arr: List[int]) -> bool:
        arr.sort()
        if len(arr)<2:
            return True
        diff = arr[1]-arr[0]
        for i in range(1, len(arr)):
            if diff!=arr[i]-arr[i-1]:
                return False
        return True

```
