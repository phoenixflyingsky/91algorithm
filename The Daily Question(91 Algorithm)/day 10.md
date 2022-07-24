## 160. Intersection of Two Linked Lists

### Idea
Use two pointers 



### Code


```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        // use two pointers

        ListNode pointerA = headA;
        ListNode pointerB = headB;

        while(pointerA != pointerB) {
            if(pointerA == null) {
                pointerA = headB;
            }
            else {
                pointerA = pointerA.next;
            }

            if(pointerB == null) {
                pointerB = headA;
            }
            else {
                pointerB = pointerB.next;
            }        
        }

        return pointerA;
        
    }
}


```

**Complexity Analysis**
- Time Complexity： O(1)   
- Space Complexity： O(m + n)  m is the length of headA LinkedList, n is the length of headB LinkedList
