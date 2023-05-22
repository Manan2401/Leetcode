# 347. Top K Frequent Elements

## Approach:
This code utilizes the Counter class from the collections module to count the frequency of elements in a given list of integers. It then retrieves the k most frequent elements and returns them in a list.


<br></br>
## Python Code:
```shell
from collections import Counter
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        x = Counter(nums)
        y = x.most_common()
        res=[]
        for i in range(k):
            res.append(y[i][0])
        return res

```
