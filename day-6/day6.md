# Day 6

## List Interface in Java 
![image](https://user-images.githubusercontent.com/20329508/131224420-2f657b14-75ae-44e6-8795-1ac11db169d7.png)

Declaration: The List interface is declared as:

```java
public abstract interface List extends Collection
```
The List Interface is implemented by four classes:
- ArrayList
- LinkedList
- Vector
- Stack

| Method	| Description |
| ---- | ----------- |
| `get(int index)` |	This method returns element at the specified index.|
| `set(int index, E element)`	| This method replaces element at given index with new element. This function returns the element which was just replaced by new element. Since it is a generic function, so "E" here is denotes the type of element in the List. |
| `indexOf(element)`	| This method returns the first occurrence of the given element or -1 if the element is not present in the list. |
| `listIterator()` |	List interface has an enhanced version of the iterator. The iterator in Collection interface allows us to traverse only in the forward direction, where as a List iterator is an ehnaced iterator and it allows us to traverse in both forward and backward directions. |
| `listIterator(int index)`	| This function returns an iterator pointing to the element at index "index". |
| `remove(int index)` |	This method removes an element from the specified index. It shifts subsequent elements(if any) to left and decreases their indexes by 1. |
| `remove(element)` |	This method is used to remove the first occurrence of the given element in the list. |

## ListIterator
The ListIterator works only with the List interface in Java and it is inherited from the Iterator interface. So, it includes all functionalities of the iterator interface.
- It works only with Lists like ArrayList, Vector, LinkedLists.
- It is inherited from the Iterator interface. So, it includes all functionalities of the iterator interface.
- In addition to `next()`, `hashNext()` and `remove()`, it provides the below methods:
  - `hasPrevious()` - It is used to check if we have previous item for the item pointed by current iterator or not.
  - `previous()` - It returns the previous element of the list, and moves the iterator one position back.
  - `add()` - It is used to add an item while iterating through the List.
  - `set()` - replaces the element returned by either next() or previous() with the specified element
  - `nextIndex()` - returns the index of the element that the next() method will return
  - `previousIndex()` - returns the index of the element that the previous() method will return

## ArrayLists in Java 
- present in java.util package
- Dynamic size
- Rich library

Like dynamic arrays in other languages, ArrayLists in Java also uses normal arrays internally to implement dynamic resizing.
- It internally uses arrays.
- If internal array becomes full, do the following:
    - Create a new array of double size.
    - Copy elements from previous array to this newly created array.
    - Free space allocated to old array.

- The two major advantages of arrays are:
  - Cache Friendliness.
  - Random access of elements.

##  ArrayList Methods 
```
add(obj) --------> Amortized O(1)

size()    -------
isEmpty() -------  \____  Worst Case O(1)
get()------------  /
set() -----------

contains()  ----------------  
indexOf()   ----------------  \
lastIndexOf()  -------------    ------ Worst Case O(N)
remove() [both versions] ---  /
add(index, obj)  -----------
```

##  LinkedList in Java 
- present in java.util package
- This class is an implementation of the LinkedList data structure which is a linear data structure where every element is stored as a separate object with a data part and address part. 
- The elements are linked using pointers and addresses called nodes
- Two paticular cases for using it:
  - It can be used as an ArrayList when the list type operation is performed for eg, insertion, deletion, remove, etc. It implements all the functions of the List interface just like an ArrayList.
  - It can be also be used as an ArrayDeque when queue or dequeue type of operations are performed, thus implementing the Deque interface.

![image](https://user-images.githubusercontent.com/20329508/131225005-5b9f365a-8dcd-42be-9e02-9ed061146f4d.png)

### Advantages 
- Dynamic Memory allocation
- elements don’t need contiguous memory locations
- Insert and delete operations are less expensive

### Disadvantages 
- nodes cannot be accessed directly
- less cache-friendly as compare to ArrayList

### Methods common to both LinkedList and ArrayList

|Method |	Description |	Time Complexity |
| ----- | ----------- | --------------- |
| add(E e) | 	This method Appends the specified element to the end of this list. | 	Theta(1) | 
| add(int index, E element) | 	This method Inserts the specified element at the specified position in this list. | 	Theta(index) | 
| contains(Object o) | 	This method returns true if this list contains the specified element. | 	O(n) | 
| remove(int index) | 	This method removes the element at the specified position in this list. | 	Theta(index) | 
| remove(Object o) | 	This method removes the first occurrence of the specified element from this list, if it is present. | 	O(n) | 
| get(int index) | 	This method returns the element at the specified position in this list. | 	Theta(index) | 
| set(int index, E element) | 	This method replaces the element at the specified position in this list with the specified element. | 	Theta(index) | 
| indexOf(Object o) | 	This method returns the index of the first occurrence of the specified element in this list, or -1 if this list does not contain the element. | 	O(n) | 
| lastIndexOf(Object o) | 	This method returns the index of the last occurrence of the specified element in this list, or -1 if this list does not contain the element. | 	O(n) | 
| isEmpty() | 	This method is used to check if a list is empty or not. | 	O(1) | 

### Methods implementing Queue interface

| Method | 	Description | 
| ----- | ----------- |
| add(E e) | 	This method Appends the specified element to the end of this list. Throws exception when element cannot be added to the list. | 
| remove() | 	This method retrieves and removes the head (first element) of this list. Throws exception when the list is empty. | 
| element() | 	This method retrieves, but does not remove, the head (first element) of this list. Throws exception when the list is empty. | 
| offer(E e) | 	This method Adds the specified element as the tail (last element) of this list. Returns null when element cannot be added to the list . | 
| poll() | 	This method retrieves and removes the head (first element) of this list. Returns null when the list is empty. | 
| peek() | 	This method retrieves, but does not remove, the head (first element) of this list. Returns null when the list is empty. | 

### Methods implementing DeQueue interface


| Method | 	Description | 	Unsuccesful Response |
| ----- | ----------- | --------------- |
| addFirst(E e) | 	This method Inserts the specified element at the beginning of this list. | 	Throws Exception | 
| addLast(E e) | 	This method Appends the specified element to the end of this list. | 	Throws Exception | 
| removeFirst() | 	This method removes and returns the first element from this list. | 	Throws Exception | 
| removeLast() | 	This method removes and returns the last element from this list. | 	Throws Exception | 
| getFirst() | 	This method returns the first element in this list. |	Throws Exception | 
| getLast() | 	This method returns the last element in this list. | Throws Exception | 
| offerFirst(E e) | 	This method Inserts the specified element at the front of this list. | 	Returns Null | 
| offerLast(E e) | 	This method Inserts the specified element at the end of this list. | 	Returns Null | 
| pollFirst() | 	This method retrieves and removes the first element of this list, or returns null if this list is empty. | 	Returns Null | 
| pollLast() | 	This method retrieves and removes the last element of this list, or returns null if this list is empty. | 	Returns Null | 
| peekFirst() | 	This method retrieves, but does not remove, the first element of this list, or returns null if this list is empty. | 	Returns Null | 
| peekLast() | 	This method retrieves, but does not remove, the last element of this list, or returns null if this list is empty. | 	Returns Null | 


