## 35. Search Insert Position

### Idea
binary search



### Code


```java

class Solution {
    public int searchInsert(int[] nums, int target) {
        //binary search
        int left = 0;
        int right = nums.length - 1;

        while(left <= right) {
            int mid = (right - left) / 2 + left;
            
            if(nums[mid] == target) {
                return mid;
            }
            if(mid == right || mid == left || left == right) {
                break;
            }
            else if(nums[mid] > target) {
                right = mid;
            }
            else if(nums[mid] < target) {
                left = mid;
            }
        }

        if(nums[right] < target) {
            return right + 1;
        }
        else if(nums[left] > target) {
            return left;
        }
        return right;
    }
}

```

**Complexity Analysis**
- Time Complexity： O(log N),
- Space Complexity： O(1),
