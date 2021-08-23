# 100-days-of-code
## Day 1 - Day 7 : Choose a Programming Language and Learn The Fundamentals of it
### Day 1
- Choose a programming language:
  - I'm choosing Java
<hr>

## Notes:
### Features of Java:
  - Simple
  - Secure
  - Portable
  - Object-Oriented
  - Robust
  - Architectural Neutral
  - Distributed
  - Dynamic
### Java Program Compilation:
  - It converts java file into a highly optimized class file(bytecode)  
### Java Program Execution:
  - Classloader: It loads the lass file for JVM execution
  - Bytecode Verifier: It verifies the bytecode and restrict the objects from illegal access to other parts of the system
  - Interpreter: It read the bytecode instructions and execute them line by line.
### Java program execution flow:
 
  ![image](https://user-images.githubusercontent.com/20329508/130343770-f6dc7b92-a408-4b97-a03d-7ebbf3c23dff.png)
  
### JVM, JRE & JDK
  ![image](https://user-images.githubusercontent.com/20329508/130343803-d019614c-1961-461f-a471-71edfc4993f9.png)

 #### Java Virtual Machine (JVM):
  - abstract virtual macine which does not exist physically
  - a kind of specification that provides a secure runtime environment to execute the bytecode
  - invokes main()
  - is a part of JRE(Java Runtime environment)
 #### Java Runtime Environment(JRE):
  - provides minimum requirements for executing a Java application
  - consists of:
    - JVM
    - core classes
    - supporting files
 #### Java Development Kit (JDK):
   - provides the environment to develop and execute
   - contains:
     - a private JVM,
     - interpreter/loader(java)
     - compiler (javac)
     - an archiver (jar)
     - a document generator (Javadoc), etc    
   
### Basic Console Input/Output:
   #### Buffered Reader Class:
   - input is buffered for efficient reading
 ```java
      import java.io.BufferedReader;
      
      BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
      String name = reader.readLine();
      int number = Integer.parseInt(reader.readLine());
  ```
   #### Scanner Class
   - Reading methods are not synchronized 
   ```java
        import java.uti.Scanner;
        
        Scanner in = new Scanner(System.in);
        String s = in.nextLine();
        int num = in.nxtInt();
   ```
  #### Console Class
  - Reading password without echoing the entered characcters
  - Reading methods are synchronized
  - Does not work in non-interactive wnvironment
```java
       String name = System.console().readLine();
```
 ### Java Identifiers:
  #### Rules:
  - The only allowed characters for identifiers are all alphanumeric characters([A-Z],[a-z],[0-9]), '$'(dollar sign), and '_' (underscore)
  - Identifiers should not start with digits(\[0-9])
  - Java identifiers are case-sensitive
  - There is no limit on the length of the identifier but it is advisable to use an optimum length of 4 - 15 letters only
  - Reserved Words can't be used as an identifier
  
 ### Java Variables:
 - is a name given to a memory location.
 - Declare a variable:
  - Data Type: Type of data that can be stored in this variable.
  - Variable Name: Name given to the variable.
  - Value: It is the initial value stored in the variable

### Types of Variables:
  #### Local Variables:
  - defined within a block or method or constructor
  - variables are created when the block is entered or the function is called and destroyed after exiting from the block or when the call returns from the function
  - The scope of these variables exists only within the block in which the variable is declared
  - Initilisation of local variable is mandatory
  #### Instance Variables:
  - are non-static variables and are declared in a class outside any method, constructor or block
  - these variables are created when an object of the class is created and destroyed when the object is destroyed
  - Unlike local variables, we may use access specifiers for instance variables. If we do not specify any access specifier then the default access specifier will be used
  - Initilisation of Instance Variable is not mandatory
  #### Static Variables:
  - are also known as Class variables
  - are declared similarly as instance variables, the difference is that static variables are declared using the static keyword within a class outside any method, constructor, or block
  - we can only have one copy of a static variable per class irrespective of how many objects we create
  - are created at the start of the program execution and are destroyed automatically when the execution ends
  - Initilisation of Static Variable is not mandatory
  - If we access the static variable like Instance variable (through object), compiler will show the warning message and it wont hault the program. Compiler will replace the object name to class name automatically

### Data Types:
#### Primitive data

![image](https://user-images.githubusercontent.com/20329508/130344786-f68a743b-53ad-4894-a08d-57e9f0415644.png)


#### Object data


### Operators in Java:
![image](https://user-images.githubusercontent.com/20329508/130344850-10794437-88d1-4c0a-912b-c0520e6f13f6.png)


### Decision Control Statements:
#### Selection
- if
- if - else
- if - else if - else
- nesting of above ones
- switch
#### Jump
- break
- continue
- return
#### Loops
- while `while(condition){}`
- do-while `do{}while(condition);`
- for `for(initialize; condition; increment/decrement}`
- new for each : `for(T ele: Collection obj){}`
### Methods
![image](https://user-images.githubusercontent.com/20329508/130345140-a77967cc-0c7d-4858-942a-bc9638a7b7ab.png)


   
### Arrays
#### 1-D Array
```java
int[] intArray; // declaring array
intArray = new int[20]; // allocating memory to array

int[] intArray = new int[20]; // combining both statements in one

int[] intArray = new int[]{ 1,2,3,4,5,6,7,8,9,10 }; // Declaring array literal

intArray[0] = 5; // first element is set as 5

```

![image](https://user-images.githubusercontent.com/20329508/130357846-0274a774-2174-4f96-8ad8-cd4f85b57366.png)

#### Array Objects
```java
class Student {
  int rollNo;
  String name;
  
  Student(int rollNo, String name) {
    this.rollNo = rollNo;
    this.name = name;
  }
}
Student[] arr = new Student[7]; //student is a user-defined class

```

#### What happens if we try to access element outside the array size?
Compiler throws ArrayIndexOutOfBoundsException to indicate that array has been accessed with an illegal index. The index is negative, greater than, or equal to size of array.

#### Multi-D Array
```java
int[][] intArray = new int[10][20]; //a 2D array or matrix
int[][][] intArray = new int[10][20][10]; //a 3D array
```

![image](https://user-images.githubusercontent.com/20329508/130357972-f860f30f-0d0b-42a6-9798-93758b1f23c6.png)


- Passing Arrays to Methods
- Returning Arrays from Methods

#### Cloning of arrays
- When you clone a single dimensional array, such as Object[], a "deep copy" is performed with the new array containing copies of the original array's elements as opposed to references.
```java
int intArray[][] = {1, 2, 3};
int cloneArray[][] = intArray.clone()
```

![image](https://user-images.githubusercontent.com/20329508/130358023-6b4ab649-07b2-42bc-a5fe-e24df45227fd.png)

- A clone of a multidimensional array (like Object[][]) is a "shallow copy" however, which is to say that it creates only a single new array with each element array as a reference to an original element array but subarrays are shared.
```java
int intArray[][] = {{1, 2, 3}, {4, 5}};
int cloneArray[][] = intArray.clone()
```
![image](https://user-images.githubusercontent.com/20329508/130358144-cfc09920-1637-42be-8cf3-caffc89b8881.png)

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

