## 142. Linked List Cycle II

### Idea
Use the Fast and Slow Pointers to find if the LinkedList is the loop, and then use the ListNode index_1 = slow and ListNode index_2 = head; to get the the node where the cycle begins



### Code


```java

/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;

            if(slow == fast) {
                ListNode index_1 = slow;
                ListNode index_2 = head;
                while(index_1 != index_2) {
                    index_1 = index_1.next;
                    index_2 = index_2.next;
                }
                return index_1;
            }
        }

        return null;
        
    }
}

```

**Complexity Analysis**
- Time Complexity： O(N)   
- Space Complexity： O(1) 
