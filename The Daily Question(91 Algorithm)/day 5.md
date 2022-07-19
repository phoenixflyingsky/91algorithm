## 232. Implement Queue using Stacks

### Idea
Use two stacks to simulate the queue


### Code


```java

class MyQueue {
    Deque<Integer> inPut;
    Deque<Integer> outPut;

    public MyQueue() {
        inPut = new ArrayDeque<>();
        outPut = new ArrayDeque<>();
    }
    
    public void push(int x) {
        inPut.push(x);
    }
    
    public int pop() {  
        if(outPut != null && !outPut.isEmpty()) {
            return outPut.pop();
        }

        while(inPut != null && !inPut.isEmpty()) {
            outPut.push(inPut.pop());           
        }

        return outPut.pop();  
    }
        
    public int peek() {
         if(outPut != null && !outPut.isEmpty()) {
            return outPut.peek();
        }

        while(inPut != null && !inPut.isEmpty()) {
            outPut.push(inPut.pop());      
        }

        return outPut.peek();  
    }
    
    public boolean empty() {
        return (outPut.isEmpty() && inPut.isEmpty());
    }
}

/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue obj = new MyQueue();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.peek();
 * boolean param_4 = obj.empty();
 */

```

**Complexity Analysis**
- Time Complexity： O(N) 
- Space Complexity： O(N)
