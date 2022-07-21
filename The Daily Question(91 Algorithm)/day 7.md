## 61. Rotate List


### Idea
Firstly, calculate the point to be truncated: k%len.   
Then cut it directly and connect the head to the tail (note that when k = = len, the head should be returned directly).



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
    public ListNode rotateRight(ListNode head, int k) {
        //corner case
        if(head == null || head.next == null || k == 0) {
            return head;
        }

        int len = 0;// the length of head

        ListNode dummy = new ListNode();
        dummy.next = head;

        ListNode last = dummy;

        while(last.next != null) {
            len++;
            last = last.next;
        }

        int cut = len - k % len;

        if(cut == len) {
            return head;//pay attention: cause if cut == len ,  ListNode res = pre.next;(pre.next == null), and we will return null, so we need to return head if cut == len
        } 

        ListNode pre = dummy;

        for(int i = 0; i < cut; i++) {
            pre = pre.next;
        }

        ListNode res = pre.next;
        pre.next = null;
        last.next = head;

        return res;
    }
}


```

**Complexity Analysis**
- Time Complexity： O(N) 
- Space Complexity： O(1)
