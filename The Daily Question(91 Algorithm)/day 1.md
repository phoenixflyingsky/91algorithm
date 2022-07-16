## 989. Add to Array-Form of Integer


### Idea

just add the end of two numbers

### Code


```java
class Solution {
    public List<Integer> addToArrayForm(int[] num, int k) {
        List<Integer> res = new ArrayList<>();
        int len = num.length;
        int carry = 0;
        int index = len - 1;

        while(index >= 0 && k > 0) {
            int temp = k % 10;
            int total = temp + num[index] + carry;

            //update
            carry = total / 10;
            total = total % 10;

            //put the num to res
            res.add(0, total);

            //update
            index--;
            k = k / 10;
        }

        while(index >= 0) {
            int total = num[index] + carry;

            //update
            carry = total / 10;
            total = total % 10;

            //put the num to res
            res.add(0, total);

            //update
            index--;
        }

        while(k > 0) {
            int total = k % 10 + carry;

            //update
            carry = total / 10;
            total = total % 10;

            //put the num to res
            res.add(0, total);

            //update
            k = k / 10;
        }

        if(carry != 0) {
            res.add(0, carry);
        }

        return res;

    }
}
```

**Complexity Analysis**
- Time Complexity： O(N) 
- Space Complexity： O(N)
