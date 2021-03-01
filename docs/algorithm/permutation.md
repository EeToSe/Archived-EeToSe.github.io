---
layout: default
title: permutation
parent: assignment
grand_parent: Algorithms
nav_order: 2
---
<img align="right" src="/assets/image/queues.png" alt = "hi" width="400">
# Deques and RandomizedQueues
## Background
### Stack
Implementations of this API with different data structures
* Array  - [fixed-length](https://algs4.cs.princeton.edu/13stacks/FixedCapacityStack.java.html) & [resizing](https://algs4.cs.princeton.edu/13stacks/ResizingArrayStack.java.html)
* [Linked lists](https://algs4.cs.princeton.edu/13stacks/Stack.java.html)

### Queue
Implementations of this API with different data structures
* [Array](https://algs4.cs.princeton.edu/13stacks/ResizingArrayQueue.java.html)  - tricker
* [Linked lists](https://algs4.cs.princeton.edu/13stacks/Queue.java.html)

### Generic
The notation <Item> after the class name in each of APIs defines the name Item as a type parameter, i.e. you could use this symbolic placeholder for some concrete type. For example, Stack of Strings as code below.

```java
Stack<String> stack = new Stack<String>();
stack.push("Test");
...
String next = stack.pop();   
```  
### Autoboxing
In conclusion, **autoboxing** -> casting a primitive type to a wrapper type; **unboxing** -> casting a wrapper type to a primitive type.

``` java
Stack<Integer> stack = new Stack<Integer>();
stack.push(17);        // autoboxing (int -> Integer)
int i = stack.pop();   // unboxing   (Integer -> int)
```

### Iteration
Why? Java supports elegant "foreach" client code, see the example code below.

```java
public Iterator<Item> iterator() {
    return new ArrayIterator();
}

// an iterator, doesn't implement remove() since it's optional
private class ArrayIterator implements Iterator<Item> {
    private int i = 0;
    public boolean hasNext()  {
      return i < n;    
    }
    public void remove() {
      throw new UnsupportedOperationException();  
    }

    public Item next() {
        if (!hasNext()) throw new NoSuchElementException();
        return a[i++];
    }
}
```
---
## Spec
Write a generic data type for a deque and a randomized queue.
* Implement elementary data structures using arrays and linked lists
* Introduce generics and iterators

## Mistakes made
1. Implementation of instance methods, the case of empty Deque is not taken good care of.
2. It is better to add a reference to previous item compared with the method currentNode.next.next when it comes to finding the second last node. The latter one takes linear time while the former consumes constant time.
3. To generate a randomized array, instead of creating a copy and shuffle, we could create an index array and shuffle.
4. To be sovled, some test cases about timing(RandomizedQueue enqueue, data strcuture resizedArray)
5. Use camelCase
