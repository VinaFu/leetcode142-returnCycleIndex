# leetcode142-returnCycleIndex

          # Definition for singly-linked list.
          # class ListNode:
          #     def __init__(self, x):
          #         self.val = x
          #         self.next = None

          class Solution:
              def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
                  slow = fast = head
                  while fast and fast.next:
                      slow = slow.next
                      fast = fast.next.next         
                      if slow == fast:              // find a loop
                          slow = head               // slow start from beginning
                          while slow!=fast:         // keep going until reach the entry of loop
                              slow = slow.next
                              fast = fast.next
                          return slow               // now slow == fast, reach the entry of the loop.
                          
                          
可以理解为：每次见面的长度都固定且一致，但是一个在loop外，一个在loop内。
一旦找到下一个见面点：cross。让s/f速度变成一样。到见面的时候，就是开头的地方。
	
	H - slow move to entry
	x - fast move to entry
	until they meet(same speed), that's entry.
	
	resources from:
1. https://leetcode.com/problems/linked-list-cycle-ii/discuss/44783/Share-my-python-solution-with-detailed-explanation
2. https://www.youtube.com/watch?v=q9aTM-6__Ho&t=282s
