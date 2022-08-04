## 447. Number of Boomerangs

### Idea
Use HashMap to record the distance between each point



### Code


```java

class Solution {
    public int numberOfBoomerangs(int[][] points) {
        int res = 0;

        for(int[] point : points) {
            Map<Integer, Integer> distance = new HashMap<>();

            for(int[] p : points) {
                int dis = (p[0] - point[0]) * (p[0] - point[0]) + (p[1] - point[1]) * (p[1] - point[1]);
                //dis is twice the actual distance

                distance.put(dis, distance.getOrDefault(dis, 0) + 1);
            }

            for(Map.Entry<Integer, Integer> entry : distance.entrySet()) {
                int m = entry.getValue();

                res += m * (m - 1);
            }
        }

        return res;

    }
}

```

**Complexity Analysis**
- Time Complexity： O(n^2)   
- Space Complexity： O(n)

### Key point  
Map.Entry<Integer, Integer> entry : distance.entrySet()  
distance.put(dis, distance.getOrDefault(dis, 0) + 1);
