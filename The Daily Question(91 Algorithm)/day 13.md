## 104. Maximum Depth of Binary Tree

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
    public int maxDepth(TreeNode root) {
        //dfs  
        //corner case
        if(root == null) {
            return 0;
        }

        int leftMax = maxDepth(root.left);
        int rightMax = maxDepth(root.right);

        return Math.max(leftMax, rightMax) + 1;

    }
}

```

**Complexity Analysis**
- Time Complexity： O(N)   
- Space Complexity： O(height)  height indicates the height of the binary tree
