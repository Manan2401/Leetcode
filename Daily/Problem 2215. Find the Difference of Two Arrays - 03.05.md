# 2215. Find the Difference of Two Arrays

## Python Code:
```shell
class Solution:
    def findDifference(self, nums1: List[int], nums2: List[int]) -> List[List[int]]:
        l = [i for i in nums1 if i not in nums2]
        r = [j for j in nums2 if j not in nums1]
        return [set(l),set(r)]
```

