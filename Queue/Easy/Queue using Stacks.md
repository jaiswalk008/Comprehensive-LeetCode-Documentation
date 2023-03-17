# [Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)
### Approach:
- The approach used in this solution is to maintain the order of elements in the queue using two stacks. 
- When a new element is pushed onto the queue, it is first moved to the second stack.
- Then, all the elements in the first stack are moved to the second stack in reverse order. 
- This maintains the order of the elements in the queue, with the oldest element at the top of the first stack.

**Time Complexity:**
- push() : O(N)
- pop : O(1)

**Space Complexity:** O(N)

**Code:**
```
class MyQueue {
public:
    stack <int> s1;
    stack <int>  s2;
    MyQueue() {  
    }
    void push(int x) {
        // moving elements from s1 to s2 to insert the new element
        while(!s1.empty()){
            int val = s1.top();
            s2.push(val);
            s1.pop();
        }
        s1.push(x);
        // Now inserting the elements from s2 to s1
        while(!s2.empty()){
            int val = s2.top();a
            s1.push(val);
            s2.pop();
        }
    }
    
    int pop() {
        int x = peek();
        s1.pop();
        return x;
    }
    
    int peek() return s1.top();
    
    bool empty() return (s1.empty());
};
```
