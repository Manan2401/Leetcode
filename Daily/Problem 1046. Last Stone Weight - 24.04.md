# 1046. Last Stone Weight

## Intuition
 - To solve this problem, we can use a priority queue to keep track of the heaviest stones.
 - At each turn, we can pop the two heaviest stones from the heap, smash them together according to the given rules, and then push the resulting stone (if any) back onto the heap.
 - We repeat this process until there is at most one stone left in the heap.

<br></br>
## Python Solution
```shell
class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        # Invert the values of the stones and create a heap from them
        inverted_stones = [-n for n in stones]
        heapq.heapify(inverted_stones)
        
        # Continue until there is only one stone left in the heap
        while len(inverted_stones) > 1:
            # Pop the two heaviest stones from the heap
            heaviest = heapq.heappop(inverted_stones)
            second_heaviest = heapq.heappop(inverted_stones)
            
            # If the second heaviest stone is heavier than the heaviest stone, push the difference back onto the heap
            if second_heaviest > heaviest:
                heapq.heappush(inverted_stones, heaviest - second_heaviest)
        
        # Add a dummy value to the heap to avoid index out-of-bounds errors
        inverted_stones.append(0)
        # Return the absolute value of the remaining stone (inverted back to its original value)
        return abs(inverted_stones[0])

```

<br></br>
## C++ Solution
```shell
class Solution {
public:
    int lastStoneWeight(vector<int>& a) {
        priority_queue<int>pq(a.begin(),a.end());

        while(pq.size() > 1)
        {
            int a = pq.top();
            pq.pop();
            int b = pq.top();
            pq.pop();

            if(a != b)
                pq.push(abs(a-b));
        }
        return pq.empty() ? 0 : pq.top();
    }
};
```

<br></br>
## Complexity
 - Time complexity: O(NLogN)
 - Space complexity: O(N)
