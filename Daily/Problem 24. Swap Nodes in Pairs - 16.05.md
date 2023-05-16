# 24. Swap Nodes in Pairs

## Approach:
The approach used in the code is to traverse the linked list and swap adjacent pairs of nodes. This is done iteratively by maintaining a current pointer that points to the previous node before the pair to be swapped. The swapping is done by modifying the next pointers of the nodes.

## Python Code:
```shell
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:

        if not head or not head.next: return head

        dummy = ListNode(0)
        dummy.next = head
        curr = dummy

        while curr.next and curr.next.next:
            first = curr.next
            second = curr.next.next
            curr.next = second
            first.next = second.next
            second.next = first
            curr = curr.next.next
        
        return dummy.next
```
