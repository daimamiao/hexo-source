---
title: 'LeetCode 155:Min Stack'
date: 2016-08-16 09:36:11
tags: [LeetCode, Stack]
categories: LeetCode
thumbnail:
---
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time. <!--more-->

- push(x) -- Push element x onto stack.
- pop() -- Removes the element on top of the stack.
- top() -- Get the top element.
- getMin() -- Retrieve the minimum element in the stack.

**Example:**
```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```

### Code
```c
class MinStack {
private:
    stack<int> s;
    stack<int> min;
public:
    /** initialize your data structure here. */
    MinStack() {
        
    }
    
    void push(int x) {
        s.push(x);
        if (min.empty() || min.top() >= x) {
            min.push(x);
        }
    }
    
    void pop() {
        int temp = s.top();
        s.pop();
        if (temp == min.top()) {
            min.pop();
        }
    }
    
    int top() {
        return s.top();
    }
    
    int getMin() {
        return min.top();
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
```

#### deque
```c
class MinStack {
public:
    /** initialize your data structure here. */
    MinStack() {}

    deque<int> a;
    deque<int> b;

    void push(int x) {
        if(a.empty() && b.empty()){
            a.push_back(x);                     // push first number
            b.push_back(x);
        }else{
            a.push_back(x);                   
            if(x<b.back()){             // push the smaller number to the end of b, otherwise to the front of b
                b.push_back(x);
            }else if(x>b.back()){
                b.push_front(x);
            }else{
                b.push_back(x);
            }
        }
    }
    
    void pop() {
        if(a.back()>b.back()){                      // pop the bigger number at the front of b, otherwise pop the last element ( minimum number ) of b
            b.pop_front();
        }else if(a.back()==b.back()){
            b.pop_back();
        }
        a.pop_back();
    }
    
    int top() {
        return a.back();
    }
    
    int getMin() {
        return b.back();
    }
};
```