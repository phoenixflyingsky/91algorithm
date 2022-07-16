## 821. Shortest Distance to a Character

### Idea
- First loop: traverse from left to right to find the nearest c on the left.
- Second loop:  traverse from right to left to find the nearest c on the right.
### Code


```java
class Solution {
    public int[] shortestToChar(String s, char c) {
        int len = s.length();
        int[] res = new int[len]; 

        int minNum = Integer.MIN_VALUE / 2; //make sure the num is smaller enough
        int pre = minNum; //the distance of the nearest C on the left
        for(int i = 0; i < len; i++) {
            if(s.charAt(i) == c) {
                pre = i;
            }

            res[i] = i - pre;//make sure the distance of nearest C on the left
        }

        int maxNum = Integer.MAX_VALUE / 2; //make sure the num is larger enough
        int later = maxNum; // the distance of the nearest C on the right
        for(int i = len - 1; i >= 0; i--) {
            if(s.charAt(i) == c) {
                later = i;
            }

            res[i] = Math.min(res[i], (later - i));
        }

        return res;
    }
}


```

**Complexity Analysis**
- Time Complexity： O(N) 
- Space Complexity： O(1) (  The return value is not included in the space complexity.  )


