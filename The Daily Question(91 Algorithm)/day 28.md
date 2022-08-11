## 239. Sliding Window Maximum

### Idea
deque



### Code


```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        int[] res = new int[nums.length - k + 1]; //nums.length - k + 1 is the number of output

        Deque<Integer> queue = new LinkedList<>();

        for(int right = 0; right < nums.length; right++) {
            //right is the right border of the slide window

            while(!queue.isEmpty() && nums[right] >= nums[queue.peekLast()]){
                queue.removeLast();//if the element at the end of the queue is smaller than right, remove it.

            }

            queue.addLast(right);

            int left = right - k + 1;

            while(queue.peekFirst() < left) {
                queue.removeFirst();
            }

            if(right + 1 >= k) {
                //means window formation
                res[left] = nums[queue.peekFirst()];         
            }
        }

        return res;

    }
}


```

**Complexity Analysis**
- Time Complexity： O(N),
- Space Complexity： O(1)
