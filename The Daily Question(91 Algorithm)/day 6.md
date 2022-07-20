## 768. Max Chunks To Make Sorted II

### Idea
Using monotonic incremental stack



### Code


```java

class Solution {
    public int maxChunksToSorted(int[] arr) {

        Deque<Integer> stack = new ArrayDeque<>();

        for(int num : arr) {
            int temp = Integer.MIN_VALUE;

            while(!stack.isEmpty() && stack.peek() > num) {
                //this means the num is smaller than the stack.peek(), so we need to merge them into one
                //Because it is monotonically increasing, the first pop-up must be the largest, so we only need to record the value of the first pop-up
                temp = Math.max(temp, stack.pop());
            }

            if(temp == Integer.MIN_VALUE) {
                stack.push(num);//Num does not need to be merged with the previous block, so it is pushed into the stack
            }
            else {
                stack.push(temp);
            }
        }

        return stack.size();
    }
}

```

**Complexity Analysis**
- Time Complexity： O(N) 
- Space Complexity： O(N)
