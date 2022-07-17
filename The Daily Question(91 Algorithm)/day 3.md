## 1381. Design a Stack With Increment Operation

### Idea

build an array(int[] stack) to save the data, and then build an array(int[] auxiliaryAdd) to save the increments.    
This question is very interesting: 
- we use an array (int[] stack) to save the data. 
- we also use an auxiliary array(int[] auxiliaryAdd) to record each Inc operation. Specifically, if the Inc operation is to Increments the bottom k elements of the stack by val, then we will auxiliaryAdd[k - 1] to add Val, because, in this algorithm, we only need to know the specific value of the elements at the top of the stack. So, we just need to store the increment of each element. 

### Code


```java
class CustomStack {
    int[] stack;//store data
    int[] auxiliaryAdd; // the auxiliary array to store the increments
    int len;// the length about this stack
    int top = -1;// the num in the stack

    public CustomStack(int maxSize) {
        this.len = maxSize;
        this.stack = new int[this.len];
        this.auxiliaryAdd = new int[this.len];
    }
    
    public void push(int x) {
        if(this.top < (this.len - 1)) {
            this.top++;
            this.stack[this.top] = x;         
        }
    }
    
    public int pop() {
        if(this.top < 0) {
            return -1;
        }

        int temp = this.stack[this.top] + this.auxiliaryAdd[this.top];

        if(this.top > 0) {
            this.auxiliaryAdd[this.top - 1] += this.auxiliaryAdd[this.top]; //superimpose the previous increase
        }

        auxiliaryAdd[top] = 0; // we need to initialize this auxiliaryAdd[top] !!!!!!
 
        this.top--;

        return temp;
    }
    
    public void increment(int k, int val) {
        if(this.top == -1) {
            return;// this means if the stack has none num, we do not need to do anything
        }


        int temp = Math.min(k - 1, this.top);

        auxiliaryAdd[temp] += val;// this step is superimpose,  not just auxiliaryAdd[temp] = val; !!!
    }
}

/**
 * Your CustomStack object will be instantiated and called as such:
 * CustomStack obj = new CustomStack(maxSize);
 * obj.push(x);
 * int param_2 = obj.pop();
 * obj.increment(k,val);
 */


```

**Complexity Analysis**
- Time Complexity： O(1)  (just get the num from the array)
- Space Complexity： O(N) (cause we build two arrays to save data and increment)
