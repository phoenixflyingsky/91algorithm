## 1. Two Sum

### Idea
hashmap



### Code


```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        //use hashmap
        Map<Integer, Integer> store = new HashMap<>();

        for(int i = 0; i < nums.length; i++) {
            int temp = target - nums[i];
            if(store.containsKey(temp)) {
                return new int[] {store.get(temp), i};
            }
            else {
                store.put(nums[i], i);
            }
        }

        return null;

    }
}


```

**Complexity Analysis**
- Time Complexity： O(N)   
- Space Complexity： O(N) 
