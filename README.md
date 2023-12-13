- [x]  class

#data(represented by fields)

#Behaviour(represented by methods/ functions)

```csharp
class Person
===============
Name: string
Age: byte
Height: float
Weight: byte
----------------
Walk()
Talk()
Eat()
Sleep()
```

- [x]  object

### Encapsulation

- [x]  public
- [x]  private
- [x]  protected
- [x]  internal

Access is limited to only the current Assembly, that is any class or type declared as internal is accessible anywhere inside the same namespace. It is the ***default access modifier in C#***.

```csharp
// C# Program to show use of
// internal access modifier
// Inside the file Program.cs
using System;

namespace internalAccessModifier {

// Declare class Complex as internal
internal class Complex {

	int real;
	int img;

	public void setData(int r, int i)
	{
		real = r;
		img = i;
	}

	public void displayData()
	{
		Console.WriteLine("Real = {0}", real);
		Console.WriteLine("Imaginary = {0}", img);
	}
}

// Driver Class
class Program {

	// Main Method
	static void Main(string[] args)
	{
		// Instantiate the class Complex
		// in separate class but within 
		// the same assembly
		Complex c = new Complex();

		// Accessible in class Program
		c.setData(2, 1);
		c.displayData();
	}
}
}
/*
Real = 2
Imaginary = 1
*/
```

### Inheritance

- [x]  base and derived classes

In C#, inheritance is a process in which one object acquires all the properties and behaviors of its parent object automatically. In such way, you can reuse, extend or modify the attributes and behaviors which is defined in other class.

In C#, the class which inherits the members of another class is called **derived class** and the class whose members are inherited is called **base** class. The derived class is the specialized class for the base class.

### Advantage of C# Inheritance

**Code reusability:** Now you can reuse the members of your parent class. So, there is no need to define the member again. So less code is required in the class.

```csharp
using System;  
   public class Animal  
    {  
       public void eat() { Console.WriteLine("Eating..."); }  
   }  
   public class Dog: Animal  
   {  
       public void bark() { Console.WriteLine("Barking..."); }  
   }  
   public class BabyDog : Dog  
   {  
       public void weep() { Console.WriteLine("Weeping..."); }  
   }  
   class TestInheritance2{  
       public static void Main(string[] args)  
        {  
            BabyDog d1 = new BabyDog();  
            d1.eat();  
            d1.bark();  
            d1.weep();  
        }  
    }
```

---

### Polymorphism

- [x]  compile time vs run time polyomorphism

The term "Polymorphism" is the combination of "poly" + "morphs" which means many forms. It is a greek word. In object-oriented programming, we use 3 main concepts: inheritance, encapsulation and polymorphism.

There are two types of polymorphism in C#: compile time polymorphism and runtime polymorphism.

Compile time polymorphism is achieved by method overloading and operator overloading in C#. 

It is also known as static binding or early binding. 

Runtime polymorphism in achieved by method overriding which is also known as dynamic binding or late binding.

Static binding or early binding = Compile time

Dynamic binding or late binding = Runtime

### **C# Method Overriding**

If derived class defines same method as defined in its base class, it is known as method overriding in C#. It is used to achieve runtime polymorphism. It enables you to provide specific implementation of the method which is already provided by its base class.

To perform method overriding in C#, you need to use **virtual** keyword with base class method and **override** keyword with derived class method.

```csharp
using System;  
public class Animal{  
    public virtual void eat(){  
        Console.WriteLine("Eating...");  
    }  
}  
public class Dog: Animal  
{  
    public override void eat()  
    {  
        Console.WriteLine("Eating bread...");  
    }  
}  
public class TestOverriding  
{  
    public static void Main()  
    {  
        Dog d = new Dog();  
        d.eat();  
    }  
}
```

### C# Base

In C#, base keyword is used to access fields, constructors and methods of base class.

You can use base keyword within instance method, constructor or instance property accessor only. You can't use it inside the static method.

```csharp
using System;  
public class Animal{  
    public string color = "white";  
}  
public class Dog: Animal  
{  
    string color = "black";  
    public void showColor()  
    {  
        Console.WriteLine(base.color);  
        Console.WriteLine(color);  
    }  
      
}  
public class TestBase  
{  
    public static void Main()  
    {  
        Dog d = new Dog();  
        d.showColor();  
    }  
}
//OUTPUT: white 
//  black
```

### Calling base class method

By the help of base keyword, we can call the base class method also. It is useful if base and derived classes defines same method. In other words, if method is overridden. If derived class doesn't define same method, there is **no need to use** base keyword. Base class method can be directly called by the derived class method.

```csharp
using System;  
public class Animal{  
    public virtual void eat(){  
        Console.WriteLine("eating...");  
    }  
}  
public class Dog: Animal  
{  
    public override void eat()  
    {  
        base.eat();  
        Console.WriteLine("eating bread...");  
    }  
      
}  
public class TestBase  
{  
    public static void Main()  
    {  
        Dog d = new Dog();  
        d.eat();  
    }  
}
// OUTPUT
// eating...
// eating bread...
```

Whenever you inherit the base class, base class constructor is internally invoked.

### Abstraction

- [x]  abstract class and methods

Data abstraction is the process of **hiding** certain details and showing only essential information to the user. Abstraction can be achieved with either **abstract classes or interfaces.**

The abstract keyword is used for classes and methods.

Abstract class: is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class).

```csharp
using System;  
public abstract class Shape  
{  
    public abstract void draw();  
}  
public class Rectangle : Shape  
{  
    public override void draw()  
    {  
        Console.WriteLine("drawing rectangle...");  
    }  
}  
public class Circle : Shape  
{  
    public override void draw()  
    {  
        Console.WriteLine("drawing circle...");  
    }  
}  
public class TestAbstract  
{  
    public static void Main()  
    {  
        Shape s;  
        s = new Rectangle();  
        s.draw();  
        s = new Circle();  
        s.draw();  
    }  
}
// OUTPUT::
// drawing ractangle...
// drawing circle...
```

Abstract method: can only be used in an abstract class, and it does not have a body. The body is provided by the derived class (inherited from).

```csharp
public abstract void draw();
```

- [x]  interfaces

Interface in C# is a blueprint of a class. It is like abstract class because **all the methods which are declared inside the interface are abstract methods**. It cannot have method body and cannot be instantiated.

It is used *to achieve multiple inheritance* which can't be achieved by class. It is used *to achieve fully abstraction* because it cannot have method body.

Its implementation must be provided by class or struct. The class or struct which implements the interface, must provide the implementation of all the methods declared inside the interface.

```csharp
using System;  
public interface Drawable  
{  
    void draw();  
}  
public class Rectangle : Drawable  
{  
    public void draw()  
    {  
        Console.WriteLine("drawing rectangle...");  
    }  
}  
public class Circle : Drawable  
{  
    public void draw()  
    {  
        Console.WriteLine("drawing circle...");  
    }  
}  
public class TestInterface  
{  
    public static void Main()  
    {  
        Drawable d;  
        d = new Rectangle();  
        d.draw();  
        d = new Circle();  
        d.draw();  
    }  
}
```

### **Note: Interface methods are public and abstract by default. You cannot explicitly use public and abstract keywords for an interface method.**

```csharp
using System;  
public interface Drawable  
{  
    public abstract void draw();//Compile Time Error  
}
```

### C# Namespaces

Namespaces in C# are used to organize too many classes so that it can be easy to handle the application.

In a simple C# program, we use System.Console where System is the namespace and Console is the class. To access the class of a namespace, we need to use namespacename.classname. We can use **using** keyword so that we don't have to use complete name all the time.

In C#, global namespace is the root namespace. The global::System will always refer to the namespace "System" of .Net Framework.

```csharp
using System;  
namespace First {  
public class Hello  
{  
    public void sayHello() { Console.WriteLine("Hello First Namespace"); }  
}  
}  
namespace Second  
{  
    public class Hello  
    {  
        public void sayHello() { Console.WriteLine("Hello Second Namespace"); }  
    }  
}  
public class TestNamespace  
{  
    public static void Main()  
    {  
        First.Hello h1 = new First.Hello();  
        Second.Hello h2 = new Second.Hello();  
        h1.sayHello();  
        h2.sayHello();  
  
    }  
}  
/*
Output:

Hello First Namespace
Hello Second Namespace
*/
```

### C# namespace example: by using keyword

If we are using "using" keyword then we don't have to use complete name for accessing a namespace program.

```csharp
using System;  
using First;  
using Second;  
namespace First {  
public class Hello  
{  
    public void sayHello() { Console.WriteLine("Hello Namespace"); }  
}  
}  
namespace Second  
{  
    public class Welcome  
    {  
        public void sayWelcome() { Console.WriteLine("Welcome Namespace"); }  
    }  
}  
public class TestNamespace  
{  
    public static void Main()  
    {  
        Hello h1 = new Hello();  
        Welcome w1 = new Welcome();  
        h1.sayHello();  
        w1.sayWelcome();  
    }  
}  
/*
Output:

Hello Namespace
Welcome Namespace
*/
```

### Types of classes in C#

- [x]  regular
- [x]  static
    
    ### **C# static**
    
    In C#, static is a keyword or modifier that **belongs** to the type not instance. So instance is not required to access the static members. In C#, static can be field, method, constructor, class, properties, operator and event.
    
    ### Advantage of C# static keyword
    
    **Memory efficient:** Now we don't need to create instance for accessing the static members, so it saves memory. Moreover, it belongs to the type, so it will not get memory each time when instance is created.
    
    # C# static class
    
    The C# static class is like the normal class but it cannot be instantiated. It can have only static members. The advantage of static class is that it provides you guarantee that instance of static class cannot be created.
    
    ```csharp
    using System;  
       public static class MyMath  
        {  
            public static float PI=3.14f;   
            public static int cube(int n){return n*n*n;}  
        }  
       class TestMyMath{  
           public static void Main(string[] args)  
            {  
                Console.WriteLine("Value of PI is: "+MyMath.PI);  
                Console.WriteLine("Cube of 3 is: " + MyMath.cube(3));  
            }  
        }
    ```
    
- [x]  abstract
- [x]  sealed Partial

C# sealed keyword applies restrictions on the class and method. If you create a sealed class, it cannot be derived. If you create a sealed method, it cannot be overridden.

### **Property**

### Usave of C# Properties

1. C# Properties can be read-only or write-only.
2. We can have logic while setting values in the C# Properties.
3. We make fields of the class private, so that fields can't be accessed from outside the class directly. Now we are forced to use C# properties for setting or getting values.

```csharp
class User
    {
        private string name = "Emran Khan";
        public string Name
        {
            get{return name.ToUpper();}
            set{ if (value[0] == 'e')name = value;}
        }
    }
```

---

### Delegates & Lambda Expression

- [x]  Delegates

In C#, delegate is a *reference to the method*. It works like *function pointer* in C and C++. But it is objected-oriented, secured and type-safe than function pointer.

For static method, delegate encapsulates method only. But for instance method, it encapsulates method and instance both.

The best use of delegate is to use as event.

Internally a delegate declaration defines a class which is the derived class of **System.Delegate**.

```csharp
using System;  
delegate int Calculator(int n);//declaring delegate  
      
public class DelegateExample  
{  
    static int number = 100;  
    public static int add(int n)  
    {  
        number = number + n;  
        return number;  
    }  
    public static int mul(int n)  
    {  
        number = number * n;  
        return number;  
    }  
    public static int getNumber()  
    {  
        return number;  
    }  
    public static void Main(string[] args)  
    {  
        Calculator c1 = new Calculator(add);//instantiating delegate  
        Calculator c2 = new Calculator(mul);  
        c1(20);//calling method using delegate  
        Console.WriteLine("After c1 delegate, Number is: " + getNumber());  
        c2(3);  
        Console.WriteLine("After c2 delegate, Number is: " + getNumber());  
  
    }  
}
```

- [x]  Anonymous Method
- [x]  Lambda Expression

Anonymous function is a type of function that does not has name. In other words, we can say that a function without name is known as anonymous function.

In C#, there are two types of anonymous functions:

- Lambda Expressions
- Anonymous Methods
- 

### C# Lambda Expressions

Lambda expression is an anonymous function which we can use to create delegates. We can use lambda expression to create local functions that can be passed as an argument. It is also helpful to write LINQ queries.

**C# Lambda Expression Syntax**

1. (input-parameters) => expression

### Example

```csharp
using System;  
namespace LambdaExpressions  
{  
    class Program  
    {  
        delegate int Square(int num);  
        static void Main(string[] args)  
        {  
            Square GetSquare = x => x * x;  
            int j = GetSquare(5);    
            Console.WriteLine("Square: "+j);  
        }  
    }  
}
```

### C# Anonymous Methods

Anonymous method provides the same functionality as lambda expression, except that it allows us to omit parameter list. Let see an example.

Example

```csharp
using System;

namespace AnonymousMethods

{

class Program

{

public delegate void AnonymousFun();

static void Main(string[] args)

{

AnonymousFun fun = delegate () {

Console.WriteLine("This is anonymous function");

};

fun();

}

}

}

// Another example
public delegate int Del(int a, int b);
       public static void Main(string[] args)
       {
           Del d;
           d = delegate (int x, int y)
           {
               return x + y;
           };
           Console.WriteLine(d(234,423));

       }
```

Tasks

- [ ]  Create a console application using OOP features
- [x]  C# generics

Not specified to a particular data type

add <T> TO: Classes, methods, fields, etc.

allows for code reusability for different data types

```csharp
using System;  
namespace CSharpProgram  
{  
    class GenericClass<T>  
    {  
        public GenericClass(T msg)  
        {  
            Console.WriteLine(msg);  
        }  
    }  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            GenericClass<string> gen   = new GenericClass<string> ("This is generic class");  
            GenericClass<int>    genI  = new GenericClass<int>(101);  
            GenericClass<char>   getCh = new GenericClass<char>('I');  
        }  
    }  
}  
/*
Output:

This is generic class
101
I
*/

// ANother Example:

public static void Main(string[] args)
  {
      int a = 234;
      float f = 23.4234f;
      string st = "this is thekl";
      show(st);
      show(f);

      show(9273497293.2234847928734);
  }
  static void show<T>(T n)
  {
      Console.WriteLine(n);
  }
```

- [x]  IList, IEnumerable, IQueryable, List (Difference between them)
- [x]  Linq
