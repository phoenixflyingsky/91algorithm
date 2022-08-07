## Delete Sublist to Make Sum Divisible By K  
https://binarysearch.com/problems/Delete-Sublist-to-Make-Sum-Divisible-By-K

### Idea
prefix & hashmap  
very, very interesting question



### Code


```java

import java.util.*;

class Solution {
    public int solve(int[] nums, int k) {
        // use prefix & hashmap

        int totalSum = 0;
        for(int num : nums) {
            totalSum += num;
        }

        int r0 = totalSum % k;//remainder of sum
        if(r0 == 0) {
            return 0;
        }

        int res = Integer.MAX_VALUE;
        Map<Integer, Integer> map = new HashMap<>();
        //initialize
        map.put(0, -1);

        int preSum = 0;// this is the prefix

        for(int j = 0; j < nums.length; j++) {
            preSum += nums[j];
            int r = preSum % k;//remainder of prefix

            int rr = r - r0;
            if(rr < 0) {
                rr = (rr + k) % k;
            }

            if(map.containsKey(rr)) {
                int i = map.get(rr) + 1;//we got the num before i(casue we need preSum[i - 1] % k == r - r0), so we need plus 1(one)
                res = Math.min(res, j - i + 1);
            }

            map.put(preSum % k, j);
        }

        return res >= nums.length ? -1 : res;
        
    }
}

```

**Complexity Analysis**
- Time Complexity： O(N)   
- Space Complexity： O(N) 
