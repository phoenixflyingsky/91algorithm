## 26. Remove Duplicates from Sorted Array

### Idea
fast & slow pointers



### Code


```java

class Solution {

    public void switchNum(int[] nums, int fast, int slow) {  
        int temp = nums[fast];
        nums[fast] = nums[slow];
        nums[slow] = temp;
    }

    public int removeDuplicates(int[] nums) {
        //fast & slow pointers
        int fast = 0, slow = 0;

        while(fast < nums.length) {
            int fastNum = nums[fast];
            int slowNum = nums[slow];

            if(fastNum != slowNum) {
                slow++;

                switchNum(nums, fast, slow);
                fast++;
            }
            else {
                fast++;
            }
        } 

        return slow + 1;//cause slow is the index, it starts at 0, so we need plus one

    }
}

```

**Complexity Analysis**
- Time Complexity： O(N),
- Space Complexity： O(1),
