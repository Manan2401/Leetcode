# 2130. Maximum Twin Sum of a Linked List
## Approach:
 - To find the maximum twin sum, we need to pair up the elements in the linked list in a way that maximizes the sum of each pair.
 - We can achieve this by rearranging the elements in the linked list.
 - First, we need to reverse the first half of the linked list. This can be done using the two-pointer technique, where one pointer moves at a normal pace (slow pointer), and the other pointer moves twice as fast (fast pointer).
 - While reversing the first half, we also keep track of the previous pointer to the slow pointer, as we will need it later to calculate the sum.
 - After reversing the first half, we adjust the pointers if the length of the linked list is odd.
 - Finally, we iterate through the reversed first half and the second half, calculating the sum of each pair and keeping track of the maximum sum encountered.
 
 <br></br>
 ## Python Code:
 ```shell
 class Solution:
    def pairSum(self, head: Optional[ListNode]) -> int:
        slow_ptr = head
        fast_ptr = head
        prev_ptr = None
        while fast_ptr and fast_ptr.next:
            fast_ptr = fast_ptr.next.next
            next_node = slow_ptr.next
            slow_ptr.next = prev_ptr
            prev_ptr = slow_ptr
            slow_ptr = next_node

        max_sum = float('-inf')
        while slow_ptr:
            max_sum = max(max_sum, slow_ptr.val + prev_ptr.val)
            slow_ptr = slow_ptr.next
            prev_ptr = prev_ptr.next
        return max_sum

 ```
