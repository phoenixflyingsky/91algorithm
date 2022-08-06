## 30. Substring with Concatenation of All Words

### Idea
slide window



### Code


```java

class Solution {
    public List<Integer> findSubstring(String s, String[] words) {
        List<Integer> res = new ArrayList<>();
        int num = words.length;
        int wordLen = words[0].length();
        int stringLen = s.length();

        for(int i = 0; i < wordLen; i++) {
            if(i + num * wordLen > stringLen) {
                //If the length exceeds the length of S, then the following cannot be correct
                break;
            }

            Map<String, Integer> differ = new HashMap<>();//the differ between windows and words
            

            for(int j = 0; j < num; j++) {
                //Initialized window, length is num * wordLen, store each word

                String word = s.substring(i + j * wordLen, i + (j + 1) * wordLen);
                //shows each word
                differ.put(word, differ.getOrDefault(word, 0) + 1);
            }

            for(String word : words) {
                //Calculate the difference between words and window
                differ.put(word, differ.getOrDefault(word, 0) - 1);
                if(differ.get(word) == 0) {
                    differ.remove(word);
                }
            }

            for(int start = i; start < stringLen - num * wordLen + 1; start += wordLen) {
                if(start != i) {
                    //Firstly record the word on the right, and then delete the word on the left

                    //record the words on the right
                    String word = s.substring(start + (num - 1) * wordLen, start + num * wordLen);
                    differ.put(word, differ.getOrDefault(word, 0) + 1);
                    if(differ.get(word) == 0) {
                        differ.remove(word);
                    }

                    //delete the word on the left
                    word = s.substring(start - wordLen, start);
                    differ.put(word, differ.getOrDefault(word, 0) - 1);
                    if(differ.get(word) == 0) {
                        differ.remove(word);
                    }
                }

                if(differ.isEmpty()) {
                    res.add(start);
                }
            }
        }

        return res;
    }
}

```

**Complexity Analysis**
- Time Complexity： O(ls×n),  ls is the length of the s, n is the length of each word
- Space Complexity： O(m×n), m is the number of the words, n is the length of each word
