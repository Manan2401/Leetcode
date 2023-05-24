# 2542. Maximum Subsequence Score

## Approach:
 - Create pairs of (nums2[i], nums1[i]) for each corresponding element in nums1 and nums2. This pairs array will represent the efficiency and values of each pair.

 - Sort the pairs array in descending order based on the efficiency value. This step ensures that pairs with higher efficiency values are considered first.

 - Initialize a priority queue, pq, to track the top k values.

 - Initialize variables res (result) and totalSum to 0.

 - Iterate over each pair in the sorted pairs array.

 - Add the value (pair[1]) to the priority queue pq and update the totalSum by adding the value.

 - If the size of pq exceeds k, remove the smallest value from pq and subtract it from the totalSum.
 
 - If the size of pq is equal to k, calculate the current score by multiplying the totalSum with the efficiency value (pair[0]). Update the result (res) with the maximum score.

 - Return the maximum score (res) as the final result.

<br></br>
## Python Code
```shell
class Solution:
    def maxScore(self, nums1, nums2, k):
        total = res = 0
        heap = []
        
        pairs = zip(nums1, nums2)
        
        sorted_pairs = sorted(pairs, key=lambda x: -x[1])
        
        for pair in sorted_pairs:
            num1, num2 = pair  
            heappush(heap, num1)
            total += num1
            if len(heap) > k:
                total -= heappop(heap)
            if len(heap) == k:
                res = max(res, total * num2)
        
        return res
```
