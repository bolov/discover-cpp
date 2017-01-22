---
title: Queue exercises
tags: []
keywords:
summary: "Queue exercises"
sidebar: exercises_sidebar
permalink: exercises-queue.html
---

## Queue

A Queue is a data structure, a collection in which entities are kept in order.
The oldest element added is the one removed. (FIFO).
[Queue on wikipedia](https://en.wikipedia.org/wiki/Queue_(abstract_data_type))

## Fixed max size queue

### Ex 1

Using a fixed-size C-array, implement a Queue class for integers.


```cpp
class Queue {
public:
    static const int max_size = 100;

private:
    //we use a C-array as a buffer for the queue
    //the queue's back is at the beggining of the buffer
    //the queue's front is at the end of the array
    int buffer_[max_size];

    // index to 1 past the front of the queue
    // for instance if the queue has 3 elements, they are at index 0,1,2 in buffer
    // front_ would be in this case 3
    int front_ = 0;


public:

    // modifiers

    void enqueue(int value)
    {
        // insert the value to the back of the queue (the beggining of the buffer)
        // all buffer elements will have to bo shifted 1 to the right
        // don't forget to update front_
    }

    int dequeue()
    {
        // remove from queue and return the front element
        // don't forget to update front_
    }

    // element access

    const int& front() const
    {
        // return a const reference to the front element
    }

    const int& back() const
    {
        // return a const reference to the back element
    }

    // size
    int size() const
    {
        // return the size (number of elements in the queue)
    }

    bool is_empty() const
    {
        // return True if queue contains 0 elements
        // hint: use size method
    }

    bool is_full() const
    {
        // return if queue if buffer is full
    }

    bool operator==(const Queue& rhs) const
    {
        // compare 2 queues.
        // return True if they have the same size and the same elements
    }

};

bool operator!=(const Queue& lhs, const Queue& rhs)
{
    // there is no special reason why operator== is a member of Queue and operator!= is outside the class as a free function
    // other than to implement both ways

    //hint: use operator==
    // the implementation should take just 1 line of code
}

```

Create a main where you test the Queue.
Add operations for each implemented method.

For `queue` and `dequeue` this could be a minimal testing:

```cpp
int main()
{
    Queue q;

    q.enqueue(10);
    q.enqueue(20);
    q.enqueue(30);

    cout << "deque: " << q.dequeue() << endl;
    cout << "deque: " << q.dequeue() << endl;

}
```

## Dynamic queue

### Ex 3

Using `std::vector` implement a queue without a max size limitation:

```cpp
class Queue {
private:
    std::vector<int> buffer_;

public:
    // same methods
};
```

Don't forget to test at every step!


