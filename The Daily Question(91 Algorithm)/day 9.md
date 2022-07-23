## 109. Convert Sorted List to Binary Search Tree

### Idea
use the Fast and Slow Pointers to find the mid node, and then Divide and Conquer



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
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode sortedListToBST(ListNode head) {
        //corner case
        if(head == null) {
            return null;
        }

        else if(head.next == null) {
            return new TreeNode(head.val);
        }

        //Use the Fast and Slow Pointers to find the mid Node
        ListNode slow = head;
        ListNode fast = head;
        ListNode pre = null; //Pre is the previous node of the slow Node

        while(fast != null && fast.next != null) {
            pre = slow;
            slow = slow.next;
            fast = fast.next.next;
        }

        pre.next = null;//Unlinks the node ！！！！！！！！！

        //recursion
        TreeNode node = new TreeNode(slow.val);
        node.left = sortedListToBST(head);
        node.right = sortedListToBST(slow.next);

        return node;
    }
}


```

**Complexity Analysis**
- Time Complexity： O(NlogN) Each layer uses a while loop (fast and slow pointer) to find its own middle point, so each layer is O(N), and there are altogether logN layers, so the total time complexity is O(NlogN)
- Space Complexity： O(logN)  Recursion is a total of logN layers, so O(logN) additional space is required in general      
