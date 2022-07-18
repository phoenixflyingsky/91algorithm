## 394. Decode String

### Idea
Use stack to simulate this process

### Code


```java
class Solution {
    public String decodeString(String s) {
        Deque<Integer> numStack = new ArrayDeque<>();//save the times
        Deque<String> strStack = new LinkedList<>();//save the string
        StringBuilder tail = new StringBuilder();//recode the string
        
        int len = s.length();
        for(int i = 0; i < len; i++) {
            char c = s.charAt(i);

            if(Character.isDigit(c)) {
                //Character.isDigit(c) means if the c is num 
                int num = c - '0';
                while(i + 1 < len && Character.isDigit(s.charAt(i + 1))) {
                    //the num may do not just single
                    num = num * 10 + s.charAt(i + 1) - '0';
                    i++;
                }    
                numStack.push(num);          
            }

            else if(c == '[') {
                //push the contents of tail to strStack
                strStack.push(tail.toString());
                tail = new StringBuilder();
            }

            else if(c == ']') {
                //cause the things in brackets are saved in the tail 
                //times are saved in the numStack
                //strStack contains string between two left brackets('[')

                StringBuilder temp = new StringBuilder();
                temp.append(strStack.pop());

                int times = numStack.pop();
                for(int j = 0; j < times; j++) {
                    temp.append(tail);
                }

                tail = temp;
            }

            else {
                tail.append(c);
            }

            //i++; 
            //we do not need i++, cause : for(int i = 0; i < len; i++)
        }

        return tail.toString();
    }
}


```

**Complexity Analysis**
- Time Complexity： O(N) 
- Space Complexity： O(N)
