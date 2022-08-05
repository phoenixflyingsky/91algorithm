### Idea
slide window



### Code


```java

class Solution {
    public int lengthOfLongestSubstring(String s) {
        if(s.length() == 0) {
            return 0;
        }
        Map<Character, Integer> map = new HashMap<>();
        int len = s.length();

        int first = 0;
        int end = 0;
        int res = 1;

        for(int i = 0; i < len; i++) {
            char ch = s.charAt(i);

            if(!map.containsKey(ch) || (map.containsKey(ch) && (map.get(ch) < first))) {
                //char do not in the current substring
                res = Math.max(end - first + 1, res);
                map.put(ch, i);
            }

            else{
                if(i > 0 && s.charAt(i) == s.charAt(i - 1)) {
                    //Special case: for example, the second "b" in the abba means to restart the calculation
                    first = i;
                    map.clear();
                }
                else {
                    first = map.get(ch) + 1;
                }
                
                res = Math.max(end - first + 1, res);
                map.put(ch, i);
            }

            end++;
        }

        return res;

    }
}

```

**Complexity Analysis**
- Time Complexity： O(n)   
- Space Complexity： O(n)
