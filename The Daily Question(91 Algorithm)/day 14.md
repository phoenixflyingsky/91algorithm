## 100. Same Tree


### Idea
dfs



### Code


```java
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
    public boolean isSameTree(TreeNode p, TreeNode q) {
        //corner case
        if(p == null && q == null) {
            return true;
        }
        else if(p == null || q == null) {
            return false;
        }

        //compare the val of root
        if(p.val != q.val) {
            return false;
        }

        //compare left and right
        boolean leftEqual = isSameTree(p.left, q.left);
        boolean rightEqual = isSameTree(p.right, q.right);

        return leftEqual && rightEqual;
    }
}


```

**Complexity Analysis**
- Time Complexity： O(min(m,n))   
- Space Complexity： O(height)  height indicates the height of the binary tree
