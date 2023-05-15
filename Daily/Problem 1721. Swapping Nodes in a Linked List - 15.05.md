# Swapping Nodes in a Linked List

## Python Code:
```shell
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def swapNodes(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        # Pointer one
        cur = head
        for i in range(k-1):
            cur = cur.next

        # Storing the left pointer which need to be swap 
        left = cur
        # Storing the right pointer which need to be swap
        right = head 

        # Iterating over the list to get the correct right pointer
        while cur.next:
            cur = cur.next
            right = right.next

        # Swap left pointer & right pointer node value
        left.val,right.val = right.val,left.val

        return head
```
