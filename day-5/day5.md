# Day 4
## Methods in Collection

- size() 	This method is used to return the number of elements in the collection.
- isEmpty() 	This method returns true if this collection contains no elements.
- contains(Object o) 	This method returns true if the collection contains the specified element.
- add(E e) 	This method is used to add an object of type E to the collection.
- remove(Object o) 	This method is used to remove the given object from the collection. If there are duplicate values, then this method removes the first occurrence of the object.
- Iterator iterator() 	This method returns an iterator over the elements in this collection.
- Object[] toArray() 	This method is used to return an array containing all of the elements in this collection.
- T[] toArray(T[] arr) 	This method takes a collection of type T and converts the same array if it has enough space else creates a separate array.
- stream() 	Introduced in Java 1.8, this method is used to return a sequential Stream with this collection as its source. The conversion is done in a pipelined way.
- parallelStream() 	Introduced in Java 1.8, this method returns a parallel Stream with this collection as its source. The conversion is done in a pipelined way.
- containsAll(Collection c) 	This method returns true if the collection contains all of the elements in the given collection.
- addAll(Collection c) 	This method adds all the elements in the given collection to this collection.
- removeAll(Collection c) 	This method is used to remove all the objects mentioned in the given collection from the collection.
- removeIf(Predicate filter) 	This method is used to removes all the elements of this collection that satisfy the given predicate. 

## Iterator
Iterable Interface is the root interface for the entire collection framework. 
- The collection interface extends the iterable interface. Therefore, inherently, all the interfaces and classes implement this interface
- this interface contains only one abstract method which is the iterator. It returns the

    `Iterator iterator();`
	

    - `boolean hasNext()`: This checks whether an element is present at the next position or not

    - `E next()`: Iterator moves in-between the elements and the next() gives the next element to the iterator and at the same time moves the iterator to the next position.

    - `void remove()`: The remove() method removes an element just before the iterator. This must be called only once after the next() method as multiple calls can result in unspecified behaviour in Java

##  `toArray() Methods `
This method is used to convert a collection to a normal array in Java. This has two versions:

    Object[] toArray(): Returns an array of object.

    T[] toArray(T[]): Returns an object of a given type passed as parameter.
	
### Collection.toArray()

The toArray() method allocates a new in-memory array with a length equal to the size of the collection. Internally, it invokes the Arrays.copyOf on the underlying array backing the collection. Therefore, the returned array has no references to it and is safe to use:
```java
Object[] naturalNumbersArray = naturalNumbers.toArray();
```
However, we cannot merely cast the result into an Integer[]. Doing so will result in a ClassCastException.
```
<T> T[] Collection.toArray(T[] a)
```
Unlike the non-parameterized method, this one accepts a pre-allocated array as an argument. Additionally, the use of Generics in the method's definition mandates having the same type for the input and the returned array. This also solves the previously observed problem of iterating over an Object[].
- This variant works distinctively based on the size of the input array:
	- If the length of the pre-allocated array is less than the collection's size, a new array of the required length and the same type is allocated:
```java
Integer[] naturalNumbersArray = naturalNumbers.toArray(new Integer[0]);
```
   - If the input array is large enough to contain the collection's elements, it's returned with those elements inside:
```java
Integer[] naturalNumbersArray = naturalNumbers.toArray(new Integer[naturalNumbers.size]);
```

@Dipjul Rahman 

---

# lambdas

---

- A lambda expression is like a method: it provides a list of formal parameters and body - an expression or block - expressed in terms of those parameters.

```java
// without input parameter
	//single statement in the body

		() -> expression;

	// multiple statements in the body

		() -> {
				stmt1;
				stmt2;
				...
		}

// with one input parameter
	//single statement in the body
		param -> expression;

		(param) -> expression;

	// multiple statements in the body
		param -> {
				stmt1;
				stmt2;
				...
		}

		(param) -> {
				stmt1;
				stmt2;
				...
		}

// generic format
		//single statement in the body
			(param1, param2, ...) -> expression;

		// multiple statements in the body
			(param1, param2, ...) -> {
						stmt1;
						stmt2;
						...
				}
```

aa 

> 

- Converting regular functions to lambda functions:

```java
public int squareOfNum(int n) {
		return n * n;
}

// Step 1: Remove name, visiblity, return type of the function
(int b) {
		return n * n;
}

// Step 2: Remove types of the parameters
(n) {
		return n * n;
}

// Step 3: Add '->' after the parameters
(n) -> {
		return n * n;
}

// Step 4: if body has only one statement, remove return keyword
// and the curly braces '{}'
(n) -> n * n;

// Step 5: if one parameter, then the '()' around it can be remove
n -> n * n;
```

## Functional interface:

- Functional interfaces provide target types of lambda expressions and method references.
- Each functional interface has a ***single abstract method***, to which the lambda expression's ***parameters and return types*** are matched or adapted.
- Example:

```java
@FunctionalInterface
interface Comparator<T> {
		int compare(T o1, T o2);
}

Camparator<Person> c = (Person p1, Person p2) -> 
											p1.getName().compareTo(p2.getName());
```

- `compare` - functional method`
- `T o1, T o2`  - parameter list
- `(Person p1, Person p2)` - parameter list
- `p1.getName().compareTo(p2.getName())` - implementation
- `(Person p1, Person p2) -> p1.getName().compareTo(p2.getName());` - lambda expression

## Types of Functional Interfaces:

- Predicate - takes `input parameter/s` and return `boolean`
- Supplier - it `doesn't take` any input, only `returns`
- Consumer - it takes `input parameter/s` only, `doesn't return` anything
- Function - it takes `input parameter/s` and `return some output`

## Functional Interfaces:

- `Predicate<T> -> boolean test(T t)`
- `Supplier<T> -> T get()`
- `Consumer<T> -> void accept(T t)`
- `Function<T, V> -> V apply(T t)`
- `BiPredicate<T, U> -> boolean test(T t, U u)`
- `BiConsumer<T, U> -> void accept(T t, U u)`
- `BiFunction<T, U, V> -> V apply(T t, U u)`
- `BinaryOperation<T> -> T test(T t1, T t2)`

---

# Stream API

---

- Stream operations are divided into intermediate and terminal operations, and are combined to form stream pipelines.
- A stream **pipeline** consists of a source followed by zero or more intermediate operations and a terminal operation.
- Intermediate operations return a new stream. They are always **lazy**.
- Terminal operations may traverse the stream to produce a **result** or a **side-effect**.
- Example:

```java
people
	.stream()
	// intermediate
	.map(person -> person.getAddress())
	.filter(address -> address.isVerified())
	.map(Adress::getCity) // method reference
	.map(String::toUpperCase) // method reference
	.distinct()
	.limit(10)
	// terminal
	.collect(Collectors.toList()); 
```

### Types of method references:

- Static methods

    ```java
    (q -> Objects.nonNull(q))

    (Objects::nonNull)
    ```

- Instance methods

    ```java
    (q -> log.println(q)) // Instance method of a particular object

    (log::println)
    ```

    ```java
    (q -> q.toUpperCase()) // Instance method of an arbitrary object

    (String::toUpperCase)
    ```

- Constructors

    ```java
    (q -> new Qoute(q))

    (Qoute::new)
    ```

## Intermediate operations:

1. `map(function)`
    - input: [1, 2, 3, 4, 5]
    - function: 1 → a
    - output: [a, b, c, d, e]
2. `flatMap(function)`
    - input: [1, 2, 3, 4, 5]
    - function: 1 → [a, b]
    - output: [a, b, c, d, e, f, g, h, i, j]
3. `filter(predicate)`
    - input: [1, 2, 3, 4, 5]
    - predicate: x ≠ 2 && x ≠ 5
    - output: [1, 3, 4]
4. `peak(consumer)`
    - input: [1, 2, 3, 4, 5]
    - consumer: side effect
    - output: [1, 2, 3, 4, 5]
5. `limit(int)`
    - input: [1, 2, 3, 4, 5]
    - int: 3
    - output: [1, 2, 3, 4, 5]
6. `skip(int)`
    - input: [1, 2, 3, 4, 5]
    - int: 2
    - output: [3, 4, 5]
7. `distinct()`
    - input: [1, 1, 2, 1, 2]
    - output: [1, 2]
8. `sorted(comparator)`
    - input: [4, 2, 1, 5, 3]
    - output: [1, 2, 3, 4, 5]
- Difference between `map` and `flatMap` ?

    `Stream.flatMap`, as it can be guessed by its name, is the combination of a `map` and a `flat` operation. That means that you first apply a function to your elements, and then flatten it. `Stream.map` only applies a function to the stream without flattening the stream.

    To understand what *flattening* a stream consists in, consider a structure like `[ [1,2,3],[4,5,6],[7,8,9] ]` which has "two levels". Flattening this means transforming it in a "one level" structure : `[ 1,2,3,4,5,6,7,8,9 ]`.

## Terminal operations

1. `findAny(predicate)` 
    - input: [1, 2, 3, 4, 5]
    - predicate: x % 2 == 0
    - result: 2 `not guaranteed`
2. `findFirst(predicate)`
    - input: [1, 2, 3, 4, 5]
    - predicate: x % 2 == 0
    - result: 2 `guaranteed`
3. `allMatch(predicate)`
    - input: [1, 2, 3, 4, 5]
    - predicate: x ≠ 6
    - result: true
4. `noneMatch(predicate)`
    - input: [1, 2, 3, 4, 5]
    - predicate: x % 2 == 0
    - result: false
5. `anyMatch(predicate)`
    - input: [1, 2, 3, 4, 5]
    - predicate: x % 2 == 0
    - result: true
6. `count()`
    - input: [1, 2, 3, 4, 5]
    - result: 5
7. `min(comparator)`
    - input: [1, 2, 3, 4, 5]
    - comparator
    - result: Optional(1)
8. `max(comparator)`
    - input: [1, 2, 3, 4, 5]
    - comparator
    - result: Optional(5)
9. `collect(collector)`
    - input: [1, 2, 3, 4, 5]
    - collector: `Collectors.toList()`
    - result: List(. . .)
10. `forEach(consumer)`
    - input: [1, 2, 3, 4, 5]
    - consumer: side effect
    - void
11. `reduce(binaryOperator)`
    - input: [1, 2, 3, 4, 5]
    - `binaryOperator`: `Integer::sum`
    - result: Optional(15)
