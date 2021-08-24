## Day 3:
### Inheritance with examples:
#### Single Inheritance
In single inheritance, there is only one parent and child class, and the child class inherits all the properties and behavior from the parent class.
```java
class derived-class extends base-class  
{  
   //methods and fields  
}  
```

####  Multilevel Inheritance
In multilevel inheritance, we can inherit from the child class itself. It is useful when we have to inherit all the properties and behavior of the parent class and the grandparent class.
```java
// base class
class Animal
{
    void eat()
    {
       System.out.println("Eating...");
    }
}

// derived Dog class
class Dog extends Animal
{
    
    void bark()
    { 
       System.out.println("Barking...");
    }
    
}

// derived BabyDog class
class BabyDog extends Dog
{
    
    void weep()
    { 
       System.out.println("Weeping...");
    }
    
}
```
####  Hierarchical Inheritance
In hierarchical inheritance, multiple classes can inherit from the same parent class itself. It is useful when multiple classes have to inherit all the properties and behavior from the same parent class

```java
// base class
class Animal
{
    void eat()
    {
       System.out.println("Eating...");
    }
}

// derived Dog class
class Dog extends Animal
{
    
    void bark()
    { 
       System.out.println("Barking...");
    }
    
}

// derived Cat class
class Cat extends Animal
{
    
    void meow()
    { 
       System.out.println("Meowing...");
    }
    
}

// derived Cow class
class Cow extends Animal
{
    
    void moo()
    { 
       System.out.println("Mooing...");
    }
    
}
```

#### Multiple Inheritance
Multiple Inheritance is a feature of an object-oriented concept, where a class can inherit properties of more than one parent class. 
- The problem occurs when there exist methods with the same signature in both the superclasses and subclasses. On calling the method, the compiler cannot determine which class method to be called and even on calling, which class method gets the priority.

#### Why Java doesn't support Multiple Inheritance?
1. <strong>The Diamond Problem</strong>:

          GrandParent

           /     \

          /       \

      Parent1      Parent2

          \       /

           \     /

             Test

2. <strong>Simplicity</strong>:
 Multiple inheritances are not supported by Java using classes, handling the complexity that causes due to multiple inheritances is very complex. It creates problems during various operations such as casting, constructor chaining, etc and there are very few scenarios in which we actually need multiple inheritances, so better to omit it for keeping things simple and straightforward.
 
 ###  Interfaces in Java
 Like a class, an interface can have methods and variables, but the methods declared in an interface are by default abstract (only method signature, without body).  
 - Interfaces specify what a class must do and not how. It is the blueprint of the class.
 - An Interface is about capabilities like a Player may be an interface and any class implementing Player must be able to (or must implement) move(). So it specifies a set of methods that the class has to implement.
 - If a class implements an interface and does not provide method bodies for all functions specified in the interface, the class must be declared abstract.
 - A Java library example is the Comparator Interface. If a class implements this interface, then it can be used to sort a collection.
 - all the methods in the interface are declared with an empty body and are public, and all fields are public, static, and final by default

<strong>Why do we use interface?</strong>
- It is used to achieve total abstraction.
- Since java does not support multiple inheritance in the case of class, but by using interface it can achieve multiple inheritance.
- It is also used to achieve loose coupling.
- Interfaces are used to implement abstraction. So the question arises, Why use interfaces when we have abstract classes?
  - The reason is that the abstract classes may contain non-final variables, whereas variables in interface are final, public, and static. 

```java
interface Vehicle {
    
    // all are the abstract methods.
    void changeGear(int a);
    void speedUp(int a);
    void applyBrakes(int a);
}

class Bicycle implements Vehicle{
    
    int speed;
    int gear;
    
     // to change gear
    @Override
    public void changeGear(int newGear){
        
        gear = newGear;
    }
    
    // to increase speed
    @Override
    public void speedUp(int increment){
        
        speed = speed + increment;
    }
    
    // to decrease speed
    @Override
    public void applyBrakes(int decrement){
        
        speed = speed - decrement;
    }
    
    public void printStates() {
         System.out.println("speed: " + speed
              + " gear: " + gear);
    }
}
```

<strong>Important points about interface</strong>
- We can't create an instance(an interface can't be instantiated) of an interface, but we can make reference of it that refers to the object of its implementing class.
- A class can implement more than one interface.
- An interface can extend another interface or interfaces (more than one interface).
- A class that implements an interface must implement all the methods in the interface.
- All the methods are public and abstract, and all the fields are public, static, and final.
- It is used to achieve multiple inheritance.
- It is used to achieve loose coupling

### Polymorphism 
 #### Compile Time Polymorphism or Method Overloading
Early binding or Compile time polymorphism can be achieved by resolving the methods. The compiler resolves which method should be used based on the signature and number of parameters at compile time only.
- Method overloading increases the readability and maintainability of the Java Program as we don't need to write separate method names performing same operations on different numbers or types of arguments. 

<strong>Method Overloading: Changing number of Parameters</strong>
<strong>Method Overloading: Changing data type of Parameters</strong>
<strong>Why method overloading is not possible by changing the return type of method only?</strong>
- If we only change the return type, then method overloading cannot happen because there will be ambiguity between the methods having the same number and data type of parameters.

<strong>Can we Overload Java `main()` method?</strong>
- Yes, We can write many main methods with different signatures but JVM invokes only the main method which receives String Array as an argument.

#### Run time Polymorphism or Method Overriding
Method overriding is used to provide a specific implementation of a method that is already provided by its superclass.
- Two rules must be followed to override the method:
  - Methods in parent and children class must have the same name.
  - Methods in parent and children class must have the same signature(data type, number of parameters).



<strong>Can we override static method?</strong>
- We can not override the static method because static methods do not belong to objects, it resides in the Class memory area and We can not override class methods as they are shared among all the objects.

<strong>Can we override the main method?</strong>
- We can not override the main method because main is a static method.

### Abstraction with Examples 

In Java, abstraction is achieved by interfaces and abstract classes. We can achieve 100% abstraction using interfaces.

Abstract classes and Abstract methods :
- An abstract class is a class that is declared with abstract keyword.
- An abstract method is a method that is declared without an implementation.
- An abstract class may or may not have all abstract methods. Some of them can be concrete methods
- A method defined abstract must always be redefined in the subclass, thus making overriding compulsory OR either make subclass itself abstract.
- Any class that contains one or more abstract methods must also be declared with abstract keyword.
- There can be no object of an abstract class. That is, an abstract class can not be directly instantiated with the new operator.
- An abstract class can have parametrized constructors and the default constructor is always present in an abstract class.

```java
abstract class Shape 
{
    String color;
    
    // these are abstract methods
    abstract double area();
    public abstract String toString();
    
    // Abstract class can have a constructor
    public Shape(String color) {
        System.out.println("Shape constructor called");
        this.color = color;
    }
    
    // this is a concrete method
    public String getColor() {
        return color;
    }
}
class Circle extends Shape
{
    double radius;
    
    public Circle(String color,double radius) {

        // calling Shape constructor
        super(color);
        System.out.println("Circle constructor called");
        this.radius = radius;
    }

    @Override
    double area() {
        return Math.PI * Math.pow(radius, 2);
    }

    @Override
    public String toString() {
        return "Circle color is " + super.color + 
                       " and area is : " + area();
    }
    
}
class Rectangle extends Shape{

    double length;
    double width;
    
    public Rectangle(String color,double length,double width) {
        // calling Shape constructor
        super(color);
        System.out.println("Rectangle constructor called");
        this.length = length;
        this.width = width;
    }
    
    @Override
    double area() {
        return length*width;
    }

    @Override
    public String toString() {
        return "Rectangle color is " + super.color + 
                           " and area is : " + area();
    }

}
```

### Abstract Class vs Interface in Java 
<strong>Abstraction</strong>: Hiding the internal implementation of the feature and only showing the functionality to the users. i.e. what it works (showing), how it works (hiding). Both abstract class and interface are used for abstraction.

#### Abstract class vs Interface
- Type of methods: Interface can have only abstract methods. Abstract class can have abstract and non-abstract methods. From Java 8, it can have default and static methods also.
- Final Variables: Variables declared in a Java interface are by default final. An abstract class may contain non-final variables.
- Type of variables: Abstract class can have final, non-final, static, and non-static variables. Interface has only static and final variables.
- Implementation: Abstract class can provide the implementation of interface. Interface can't provide the implementation of abstract class.
- Inheritance vs Abstraction: A Java interface can be implemented using keyword the "implements" and an abstract class can be extended using the keyword "extends".
- Multiple implementation: An interface can extend another Java interface only, an abstract class can extend another Java class and implement multiple Java interfaces.
- Accessibility of Data Members: Members of a Java interface are public by default. A Java abstract class can have class members such as private, protected, etc.

