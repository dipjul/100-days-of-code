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


   
