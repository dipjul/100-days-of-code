## Day 2:
### Strings
- Strings are defined as an array of characters. 
- The difference between a character array and a string is that the string is terminated with a special character ‘\0’.
```java
String str = "Geeks";
```
![image](https://user-images.githubusercontent.com/20329508/130382134-3238077c-c77f-4880-85e8-b112417c3028.png)

### Memory allotment of String
- Whenever a String Object is created, two objects are created- 
  - one in the Heap Area and 
  - one in the String constant pool, 
- and the String object reference always points to the heap area object.

![image](https://user-images.githubusercontent.com/20329508/130382372-c98df5d5-8221-4898-9431-eded24033c2c.png)

### Interfaces and Classes in String:
#### CharBuffer:
- This class implements the CharSequence interface. 
- This class is used to allow character buffers to be used in place of CharSequences. 
- An example of such usage is the regular-expression package java.util.regex.

#### String: 
- String is a sequence of characters. 
- In java, objects of String are immutable, which means that they are a constant and cannot be changed once created.
```java
String s = “GeeksforGeeks”; // String literal

String s = new String (“GeeksforGeeks”); // Using new keyword
```

#### StringBuffer:
- StringBuffer is a peer class of String that provides much of the functionality of strings. 
- String represents fixed-length, immutable character sequences while StringBuffer represents growable and writable character sequences.
```java
StringBuffer s = new StringBuffer("GeeksforGeeks");
```

#### StringBuilder:
- The StringBuilder in Java represents a mutable sequence of characters. 
- Since the String Class in Java creates an immutable sequence of characters, the StringBuilder class provides an alternate to String Class as it creates a mutable sequence of characters. 
```java
StringBuilder str = new StringBuilder();

str.append("GFG");
```

#### StringTokenizer:
- StringTokenizer class in Java is used to break a string into tokens
- A StringTokenizer object internally maintains a current position within the string to be tokenized. 
- Some operations advance this current position past the characters processed.
- A token is returned by taking a substring of the string that was used to create the StringTokenizer object

![image](https://user-images.githubusercontent.com/20329508/130382974-de8b2c41-2165-441b-9022-df05692e200d.png)

#### StringJoiner:
-  StringJoiner is a class in java.util package which is used to construct a sequence of characters(strings) separated by a delimiter and optionally starting with a supplied prefix and ending with a supplied suffix. 
-  Though this can also be done with the help of the StringBuilder class, StringJoiner provides an easy way to do so without writing much code.
```java
public StringJoiner(CharSequence delimiter)
```

### Compare two strings:
#### User defined function
```java
public class GFG {
  
    // This method compares two strings
    // lexicographically without using
    // library functions
    public static int stringCompare(String str1, String str2)
    {
  
        int l1 = str1.length();
        int l2 = str2.length();
        int lmin = Math.min(l1, l2);
  
        for (int i = 0; i < lmin; i++) {
            int str1_ch = (int)str1.charAt(i);
            int str2_ch = (int)str2.charAt(i);
  
            if (str1_ch != str2_ch) {
                return str1_ch - str2_ch;
            }
        }
  
        // Edge case for strings like
        // String 1="Geeks" and String 2="Geeksforgeeks"
        if (l1 != l2) {
            return l1 - l2;
        }
  
        // If none of the above conditions is true,
        // it implies both the strings are equal
        else {
            return 0;
        }
    }
```

#### String.equals(): 
- string `equals()` method compares the two given strings based on the data/content of the string. 
- If all the contents of both the strings are the same then it returns true. If all characters do not match, then it returns false.
```java
str1.equals(str2);
```
#### String.equalsIgnoreCase() : 
- The `String.equalsIgnoreCase()` method compares two strings irrespective of the case (lower or upper) of the string. 
- This method returns true if the argument is not null and the contents of both the Strings are same, ignoring case, else it returns false.
```java
str2.equalsIgnoreCase(str1);
```

#### Objects.equals() : 
- `Object.equals(Object a, Object b)` method returns true if the arguments are equal to each other and false otherwise. 
- Consequently, if both arguments are null, true is returned and if exactly one argument is null, false is returned. 
- Otherwise, equality is determined by using the `equals()` method of the first argument.

#### String.compareTo() :
```java
int str1.compareTo(String str2)
```
- It compares and returns the following values as follows:
  - if (string1 > string2), it returns a positive value.
  - if both the strings are equal lexicographically
    - i.e.(string1 == string2), it returns 0.
  - if (string1 < string2), it returns a negative value.

#### Why not to use == for comparison of Strings?
- `==` checks whether both objects point to the same memory location whereas `.equals()` evaluates the comparison of values in the objects.

###  Immutable Strings in Java 
- while the String object is immutable, its reference variable is not
```java
String s1 = "java";
s1.concat("rules");
```
What's happening:
- The first line is pretty straightforward: create a new String "java" and refer s1 to it. Next, the VM creates another new String "java rules", but nothing refers to it. So, the second String is instantly lost. We can't reach it.
- The reference variable s1 still refers to the original String "java". Almost every method, applied to a String object in order to modify it, creates new String object. So, where do these String objects go? Well, these exist in memory, and one of the key goals of any programming language is to make efficient use of memory.
- As applications grow, it's very common for String literals to occupy large area of memory, which can even cause redundancy. So, in order to make Java more efficient, the JVM sets aside a special area of memory called the "String constant pool". When the compiler sees a String literal, it looks for the String in the pool. If a match is found, the reference to the new literal is directed to the existing String and no new String object is created. The existing String simply has one more reference.
- In the String constant pool, a String object is likely to have one or more references. If several references point to the same String without even knowing it, it would be bad if one of the references modify that String value. That's why String objects are immutable.
- Well, now you could say, what if someone overrides the functionality of String class? That's the reason that the String class is marked final so that nobody can override the behavior of its methods.

### Introduction to OOPS
Classes and Objects are basic concepts of Object Oriented Programming which revolve around real-life entities.

#### Object: It is a basic unit of Object Oriented Programming and represents the real-life entities

An object consists of:-
- <strong>State</strong> : It is represented by the attributes of an object. It also reflects the properties of an object.
- <strong>Behavior</strong> : It is represented by the methods of an object. It also reflects the response of an object with other objects.
- <strong>Identity</strong> : It gives a unique name to an object and enables one object to interact with other objects.

#### Inheritance
The capability of a class to derive properties and characteristics from another class is called Inheritance
- <strong>Sub Class</strong>: The class that inherits properties from another class is called Sub class or Derived Class.
- <strong>Super Class</strong>: The class whose properties are inherited by sub class is called Base Class or Super class.
- <strong>Reusability</strong>: Inheritance supports the concept of “reusability”, i.e. when we want to create a new class and there is already a class that includes some of the code that we want, we can derive our new class from the existing class. By doing this, we are reusing the fields and methods of the existing class.

#### Polymorphism
means having many forms. 
- Like a man at the same time can be a father, a husband, and an employee. So the same person posses different behavior in different situations. This is called polymorphism. 

#### Abstraction
Data Abstraction is the property by virtue of which only the essential details are displayed to the user. 
- The trivial or the non-essentials units are not displayed to the user. 
- Ex: A car is viewed as a car rather than its individual components
- Advantages of Abstraction
  - It reduces the complexity of viewing things.
  - Avoids code duplication and increases reusability.
  - Helps to increase the security of an application or program as only the important details are provided to the user.

#### Encapsulation
Encapsulation is defined as the wrapping up of data under a single unit. 
- It is the mechanism that binds together the code and the data it manipulates.
- Advantages of Encapsulation:
  - <strong>Data Hiding</strong>: The user will have no idea about the inner implementation of the class. It will not be visible to the user how the class is storing values in the variables. He only knows that we are passing the values to a setter method and that the variables are getting initialized with that value.
  - <strong>Increased Flexibility</strong>: We can make the variables of the class as read-only or write-only, depending on our requirements. If we wish to make the variables as read-only then we have to omit the setter methods such as setName(), setAge() etc. or if we wish to make the variables as write-only then we have to omit the get methods such as getName(), getAge(), etc.
  - <strong>Reusability</strong>: Encapsulation also improves the re-usability and makes the code easy to change with new requirements.
  - <strong>Testing code is easy</strong>: Encapsulated code is easy to test for unit testing.


