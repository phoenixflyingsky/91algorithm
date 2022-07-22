## 24. Swap Nodes in Pairs

### Idea
Use iterations to simulate the process



### Code


```java

/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode swapPairs(ListNode head) {
        //corner case
        if(head == null || head.next == null) {
            return head;
        }

        ListNode dummy = new ListNode();
        dummy.next = head;

        ListNode pre = dummy;
        ListNode curr = dummy.next;
        ListNode next = curr.next;

        while(curr != null && next != null) {
            pre = swap(pre, next);
            curr = pre.next;
            if(curr != null) {
                next = curr.next;
            }
        }

        return dummy.next;
    }

    private ListNode swap(ListNode pre, ListNode next) {
        ListNode curr = pre.next;
        ListNode res = curr;

        ListNode temp = next.next;

        pre.next = next;
        next.next = curr;
        curr.next = temp;

        return res;
    }
}

```

**Complexity Analysis**
- Time Complexity： O(N) 
- Space Complexity： O(1)
