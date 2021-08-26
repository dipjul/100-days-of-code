# Day 4

## Java Collection Framework
Any group of individual objects which are represented as a single unit is known as the collection of the objects.
- The Collection interface(java.util.Collection) and Map interface(java.util.Map) are the two main "root" interfaces

### Advantages:
- Reduces programming effort
- Increases program speed and quality
- Consistent API

### Implementations of Data Structures
#### List
- ArrayList: dynamic arrays
- LinkedList: is an implementation of DoublyLinkedList
- Vector: dynamic arrays, legacy class, thread-safe, not recommended to be used in a single-threaded environment, use ArrayList instead
- Stack: implements Stack data structure, legacy class, use ArrayDeque instead

#### Set
- HashSet: insertion order not guaranteed, inserted based on their hashcode
- TreeSet: implementation of the self-balancing binary tree, natural ordering
- LinkedHashSet: similar to HashSet, uses doubly linked list, retains the ordering

#### Queue:
- LinkedList: implements Queue data structure
- ArrayDeque: allows users to add or remove an element from both sides of the queue
- Priority Queue: based on priority heap, used when objects are supposed to be processeed based on priority

#### Deque:
Double-ended queue, add and remove the elements from both ends of the queue, it extends queu interface
- LinkedList: linked list implementation
- ArrayDeque: array implementation

#### Map:
supports the key-value pair mapping for the data
- HashMap: uses Hashing
- LinkedHashMap: it uses a doubly linked list to store data, retains the ordering

#### Collections class: 
- has implemented basic algorithms like: binarySearch(), sort(), max(), min(), reverse(), fill()

### Collection Hierarchy:

![image](https://user-images.githubusercontent.com/20329508/130901767-67f72d97-bf04-426e-bfb9-7b29a38cd1c1.png)

### Iterable Interface: This is the root interface for the entire collection framework. The collection interface extends the iterable interface. Therefore, inherently, all the interfaces and classes implement this interface. The main functionality of this interface is to provide an iterator for the collections. They can be of two types:
- Iterator function: Gives iterator over a collection which can be used to traverse a collection or remove elements from the collection.
```java
    Iterator  iterator();
```
- for-each method: This takes action as an argument and performs the function on every item of the collection

### Generics:
```java
class Pair<T, S> {
    T x;
    S y;
}
```
#### Wildcards in generics:
The question mark (?) is known as the wildcard in generic programming. 
- It represents an unknown type. The wildcard can be used in a variety of situations such as the type of a parameter, field, or local variable; sometimes as a return type

```java
ArrayList<?> all = new ArrayList<>();
ArrayList<? extends Student> all2 = new ArrayList<>();
```
- Bound the ArrayList to only accept the Student or any descendants of Student class. This can be done by using the extends keyword. This is also called as the Upper Bounded Wildcards and is done by using extends keyword
```java

ArrayList<? super Student> all2 = new ArrayList<>();
```
- Bounded the ArrayList to only accept the Student or any ascendant of Student class. Here the Object class is the ascendant of Student class. Using the lower bound we can access the ascendant class and not the descendant class.
