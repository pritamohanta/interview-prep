
# Object-Oriented Programming (OOP) Questions and Answers

## 1. What is the difference between a class and an object?

In object-oriented programming, a class is a blueprint or template for creating objects, while an object is an instance of a class. A class defines a set of attributes and methods that are common to all objects of that class. Class is a logical entity that describes the properties and behavior of a group of objects. On the other hand, an object is a physical entity that represents a specific instance of a class. It has its own set of values for the attributes defined in the class and can perform the methods defined in the class. In simpler terms, a class is like a blueprint, while an object is like a building created from that blueprint.

---

## 2. What is the difference between a static and non-static method?

In C++, a static method is a member function of a class that can be called without an instance of the class. It belongs to the class itself, not to any instance of the class. A static method can access only static data members and other static methods of the class. It cannot access non-static data members or non-static methods of the class. Additionally, a static method can be called using the class name followed by the scope resolution operator (`::`) and the name of the method.

On the other hand, a non-static method is a member function of a class that can be called only on an instance of the class. It can access both static and non-static data members and methods of the class. Non-static methods are called using an instance of the class followed by the dot operator (`.`) and the name of the method.

---

## 3. What is the purpose of an interface in OOP?

In object-oriented programming, an interface is a collection of abstract methods that define a set of behaviors that a class can implement. It is a contract between the class and the outside world that specifies what the class can do. An interface defines a set of methods that a class must implement, but it does not provide any implementation of those methods. Instead, the class that implements the interface provides the implementation of those methods.

The purpose of an interface is to provide a way to achieve abstraction in programming. It allows you to define a set of methods that a class must implement without specifying how those methods are implemented. This makes it possible to write code that can work with any class that implements the interface, without knowing the details of how the class works. Interfaces also provide a way to achieve polymorphism in programming, which allows you to write code that can work with objects of different classes as long as they implement the same interface.

---

## 4. Explain the 4 pillars of OOP.

The four pillars of Object-Oriented Programming (OOP) are Abstraction, Encapsulation, Inheritance, and Polymorphism.

* **Abstraction:** Abstraction is the process of hiding complex implementation details and showing only the necessary information to the user. It allows the user to focus on what the object does instead of how it does it. Abstraction is achieved through abstract classes and interfaces.
* **Encapsulation:** Encapsulation is the process of wrapping data and methods into a single unit, called a class. It provides data security by preventing unauthorized access to the data. Encapsulation also helps in code maintenance and reusability.
* **Inheritance:** Inheritance is the process of creating a new class from an existing class. The new class inherits the properties and methods of the existing class. Inheritance allows the creation of a hierarchy of classes, where the child classes inherit the properties and methods of the parent class.
* **Polymorphism:** Polymorphism is the ability of an object to take on many forms. It allows objects of different classes to be treated as if they were objects of the same class. Polymorphism is achieved through method overloading and method overriding.

These four pillars of OOP provide a framework for creating modular, reusable, and maintainable code.

---

## 5. What is the difference between a public and private constructor?

A public constructor is accessible from anywhere, while a private constructor is only accessible within the same class. A public constructor can be used to create objects of a class from anywhere in the program, while a private constructor is typically used to restrict object creation to within the same class. Private constructors are often used in the Singleton design pattern, where only one instance of a class is allowed to exist.

```cpp
#include <iostream>
#include <bits/stdc++.h>
using namespace std;

class MyClass {
public:
    MyClass() {
        cout << "Public constructor called" << endl;
    }
private:
    MyClass(int x) {
        cout << "Private constructor called with argument " << x << endl;
    }
};

int main() {
    MyClass obj1; // Public constructor called
    //MyClass obj2(10); // This line will give a compile-time error because the constructor is private
    return 0;
}

```

---

## 6. What is the difference between an abstract class and an interface?

An abstract class is a class that cannot be instantiated and is typically used as a base class for other classes to inherit from. An abstract class can contain both abstract and non-abstract methods, and can also have instance variables. An abstract class contains at least one pure virtual function. You declare a pure virtual function by using a pure specifier (`= 0`) in the declaration of a virtual member function in the class declaration.

An interface, on the other hand, is a collection of abstract methods that can be implemented by any class. In C++, an interface is typically implemented using an abstract class with only pure virtual functions.

*Note: Abstract method is a method that has no implementation and is declared using the abstract keyword.*

```cpp
// Abstract class example
class Animal {
public:
    string name;
    int age;
       Animal(string name, int age) {
        this->name = name;
        this->age = age;
    }
       void eat() {
        cout << "The animal is eating" << endl;
    }
       virtual void makeSound() = 0; // Pure virtual function
};

// Interface example
class Vehicle {
public:
    virtual void start() = 0;
    virtual void stop() = 0;
    virtual void accelerate() = 0;
    virtual void brake() = 0;
};

class Car : public Vehicle {
public:
    void start() {
        cout << "The car is starting" << endl;
    }
       void stop() {
        cout << "The car is stopping" << endl;
    }
       void accelerate() {
        cout << "The car is accelerating" << endl;
    }
       void brake() {
        cout << "The car is braking" << endl;
    }
};

int main() {
    //Animal animal("Lion", 5); // This line will give a compile-time error because Animal is an abstract class and cannot be instantiated
    Car car;
    car.start();
    car.accelerate();
    car.brake();
    car.stop();
    return 0;
}

```

---

## 7. What is the difference between a shallow copy and a deep copy?

In programming, when we copy an object, we can either create a shallow copy or a deep copy. The main difference between the two is how they handle references to other objects.

A **shallow copy** creates a new object that is a copy of the original object, but the new object only contains references to the same memory locations as the original object. In other words, the new object points to the same memory locations as the original object, so any changes made to the original object will also be reflected in the new object. Shallow copy is a quick and efficient way to copy objects, but it can lead to unexpected behavior if the original object is modified.

A **deep copy**, on the other hand, creates a new object that is a copy of the original object, and all of its fields and references are also copied. In other words, a deep copy creates a new object with its own memory locations, so any changes made to the original object will not be reflected in the new object. Deep copy is a safer way to copy objects, but it can be slower and more memory-intensive than shallow copy.

```cpp
// Shallow copy
Person* person2 = person1;
person2->setAddress(new Address("456 Oak St", "Othertown"));
cout << person1->address->street << endl; // Output: 456 Oak St

// Deep copy
Person* person3 = new Person(person1->name, new    Address(person1->address->street, person1->address->city));
person3->setAddress(new Address("789 Pine St", "Somewhere"));
cout << person1->address->street << endl; // Output: 456 Oak St

```

---

## 8. What is the role of the "this" keyword in OOP?

In object-oriented programming (OOP), the `this` keyword refers to the current object instance. It is a reference to the object that is currently being operated on, and it is used to the members of the object.

The `this` keyword is often used in OOP to disambiguate between instance variables and local variables or parameters that have the same name. When a local variable or parameter has the same name as an instance variable, the `this` keyword can be used to refer to the instance variable.

---

## 9. What is a virtual function, and how is it implemented in OOP?

A virtual function is a member function of a class that can be overridden in a derived class. When a virtual function is called on an object, the actual function that is called depends on the type of the object at runtime, rather than the type of the pointer or reference used to access the object. This is known as "dynamic dispatch" or "late binding" or “dynamic binding”. It allows polymorphism, where a single interface (base class) can have multiple implementations (derived classes), and the correct implementation is chosen at runtime based on the actual type of the object.

To declare a virtual function in C++, we use the `virtual` keyword in the function declaration in the base class. When a derived class overrides a virtual function, it also uses the `virtual` keyword in the function declaration, but it is not required.

```cpp
#include <iostream>
#include <bits/stdc++.h>

class Shape {
public:
    virtual void draw() {   // without virtual, output: Drawing a shape
        std::cout << "Drawing a shape" << std::endl;
    }
};

class Circle : public Shape {
public:
    void draw() {
        std::cout << "Drawing a circle" << std::endl;
    }
};

int main() {
    Shape* shape = new Circle();
    shape->draw();         // output: Drawing a circle
    // int a; while(cin >> a) {};
    return 0;
}

```

---

## 10. What is the difference between overloading and overriding a method?

In C++, method overloading and method overriding both refer to creating different methods that share the same name. The main difference between them is that method overloading is creating multiple methods in the same class with the same name but different parameters, while method overriding is creating a new implementation of an existing method in a subclass.

When you call an overloaded method, C++ determines which method to call based on the number and types of arguments passed to it, at the compile time. When you call an overridden method using an object of the subclass type, C++ uses the method's implementation in the subclass rather than the one in the superclass (Note: based on the type of the object).

---

## 11. What is an Abstract class?

An abstract class is a class that cannot be instantiated and is used as a base class for other classes. It is declared using the "virtual" keyword and at least one pure virtual function, which is a function without a definition. The purpose of an abstract class is to provide an appropriate base class from which other classes can inherit. Abstract classes cannot be used to instantiate objects. Attempting to instantiate an object of an abstract class causes a compilation error. The subclasses of an abstract class must implement the pure virtual function(s) to become concrete classes.

```cpp
#include <iostream>
#include <bits/stdc++.h>
using namespace std;

// Abstract class
class Shape {
   public:
      // Pure virtual function
            virtual int getArea() = 0;
};

// Derived class
class Rectangle: public Shape {
   private:
      int length;
      int width;
   public:
      Rectangle(int l = 0, int w = 0) {
         length = l;
         width = w;
      }
      int getArea() {
         return (length * width);
      }
};

int main() {
   Rectangle rect(5, 10);
   cout << "Area of rectangle: " << rect.getArea() << endl;
   return 0;
}

```

---

## 12. Explain different types of constructors.

In C++, there are three types of constructors: default constructor, parameterized constructor, and copy constructor.

* **Default Constructor:** A default constructor is a constructor that takes no arguments. It is called when an object is created without any arguments. If a class does not have any constructor defined, the compiler automatically generates a default constructor.
* **Parameterized Constructor:** A parameterized constructor is a constructor that takes one or more arguments. It is used to initialize the object with the given values.
* **Copy Constructor:** A copy constructor is a constructor that creates a new object by copying the values of an existing object. It is used to create a new object that is a copy of an existing object.

```cpp
class MyClass {
   public:
      int x, y;
      MyClass() {
         cout << "Default constructor called" << endl;
      }
      MyClass(int a, int b) {
         x = a;
         y = b;
         cout << "Parameterized constructor called" << endl;
      }
           MyClass(const MyClass &obj) {
         x = obj.x;
         y = obj.y;
         cout << "Copy constructor called" << endl;
      }
};

```

---

## 13. What is Coupling in OOP and why is it helpful?

In object-oriented programming (OOP), coupling refers to the degree of interdependence between two classes. It measures how closely related two classes are to each other. A high degree of coupling means that the classes are closely related and depend on each other, while a low degree of coupling means that the classes are independent of each other.

Coupling is helpful because it allows for better organization and maintainability of code. When classes are loosely coupled, changes made to one class do not affect the other classes. This makes it easier to modify and maintain the code without affecting the entire system. On the other hand, when classes are tightly coupled, changes made to one class can have a ripple effect on the other classes, making it difficult to modify and maintain the code.

There are different types of coupling in OOP, including:

* **Content coupling:** When one class modifies the internal workings of another class.
* **Common coupling:** When two or more classes share a global data object.
* **Control coupling:** When one class controls the flow of another class.
* **Stamp coupling:** When one class uses a large number of methods from another class.
* **Data coupling:** When two classes communicate by passing data between them.

In general, it is recommended to strive for low coupling between classes in order to improve the maintainability and flexibility of the code.

---

## 14. What is a destructor in OOP?

In object-oriented programming (OOP), a destructor is a special member function that is called when an object is destroyed or goes out of scope. It is used to release any resources that were allocated by the object during its lifetime, such as memory, files, or network connections.

The destructor has the same name as the class, preceded by a tilde (`~`) symbol. It does not take any arguments and has no return type.

It is important to note that if a class does not have a destructor defined, the compiler will automatically generate a default destructor that does nothing. However, if a class allocates any resources during its lifetime, it is recommended to define a destructor to release those resources when the object is destroyed.

```cpp
class MyClass {
   public:
      MyClass() {
         cout << "Constructor called" << endl;
      }
      ~MyClass() {
         cout << "Destructor called" << endl;
      }
};

int main() {
   MyClass obj;
   return 0;
}

```

---

## 15. What is a static keyword in cpp?

In C++, a static variable or function is a variable or function that is shared by all instances of a class. It is not associated with any particular object of the class, but rather with the class itself.

A **static variable** is declared using the "static" keyword and is initialized only once, when the program starts. It retains its value throughout the lifetime of the program and can be accessed by any instance of the class. Here's an example:

```cpp
class MyClass {
   public:
      static int count;
      MyClass() {
         count++;
      }
};

int MyClass::count = 0;

int main() {
   MyClass obj1;
   MyClass obj2;
   cout << "Count: " << MyClass::count << endl;  // output: count: 2
   return 0;
}

```

A **static function** is declared using the "static" keyword and can be called without an object of the class. It is not associated with any particular object of the class, but rather with the class itself. Here's an example:

```cpp
class MyClass {
   public:
      static void print() {
         cout << "Hello, world!" << endl;
      }
};

int main() {
   MyClass::print();   // Hello, world!
   return 0;
}

```

---

## 16. What is the difference between encapsulation and data abstraction?

Encapsulation and data abstraction are two fundamental concepts in object-oriented programming, often used together to design and implement classes and objects. While they are related, they serve different purposes:

### 1. Encapsulation

Encapsulation is defined as the wrapping up of data under a single unit. It is the mechanism that binds together code and the data it manipulates. Another way to think about encapsulation is that it is a protective shield that prevents the data from being accessed by the code outside this shield. Technically in encapsulation, the variables or data of a class is hidden from any other class and can be accessed only through any member function of its own class in which they are declared. As in encapsulation, the data in a class is hidden from other classes, so it is also known as data-hiding. Encapsulation can be achieved by Declaring all the variables in the class as private and writing public methods in the class to set and get the values of variables.

```cpp
#include <bits/stdc++.h>
#include <iostream>
#include <string>
using namespace std;

class Person {
private:
    string name;
    int age;
    string address;

public:
    // Public member functions to access and modify the private data members
    void setName(const string& newName) {
        name = newName;
    }
    void setAge(int newAge) {
        if (newAge >= 0) {
            age = newAge;
        }
    }
    void setAddress(const string& newAddress) {
        address = newAddress;
    }
    string getName() const {
        return name;
    }
    int getAge() const {
        return age;
    }
    string getAddress() const {
        return address;
    }
};

int main() {
    Person person1;
    person1.setName("John Doe");
    person1.setAge(30);
    person1.setAddress("123 Main St");
    
    // Accessing the private data members through public member functions
    cout << "Name: " << person1.getName() << endl;
    cout << "Age: " << person1.getAge() << endl;
    cout << "Address: " << person1.getAddress() << endl;
    return 0;
}

```

In this example, we have a `Person` class that represents a person with three private data members: `name`, `age`, and `address`. The private data members are not directly accessible from outside the class, as they are declared as private.

Encapsulation is achieved by providing public member functions (`setName`, `setAge`, `setAddress`, `getName`, `getAge`, and `getAddress`) to interact with the private data members. These public member functions act as an interface to access and modify the private data in a controlled manner.

The `setName`, `setAge`, and `setAddress` member functions are used to set the values of the private data members, and they provide validation to ensure that valid data is stored (e.g., non-negative age). The `getName`, `getAge`, and `getAddress` member functions are used to retrieve the values of the private data members.

### 2. Data Abstraction

Data Abstraction is the property by virtue of which only the essential details are displayed to the user. The trivial or the non-essential units are not displayed to the user. Ex: A car is viewed as a car rather than its individual components. Data Abstraction may also be defined as the process of identifying only the required characteristics of an object ignoring the irrelevant details. The properties and behaviors of an object differentiate it from other objects of similar type and also help in classifying/grouping the objects.

```cpp
#include <bits/stdc++.h>
#include <iostream>

class Shape {
public:
    // Virtual function for calculating the area
    virtual double calculateArea() {
        return 0.0;
    }
};

class Circle : public Shape {
private:
    double radius;
public:
    Circle(double r) : radius(r) {}
    // Implementation of the calculateArea function for Circle
    double calculateArea() {
        return 3.14159 * radius * radius;
    }
};

class Square : public Shape {
private:
    double side;
public:
    Square(double s) : side(s) {}
    // Implementation of the calculateArea function for Square
    double calculateArea() {
        return side * side;
    }
};

int main() {
    // Creating objects and calculating the areas
    Circle myCircle(5.0);
    Square mySquare(4.0);
    
    // Using the Shape pointer to access the calculateArea function
    Shape* shape1 = &myCircle;
    Shape* shape2 = &mySquare;
    
    // Calculating and displaying the areas without const and override keywords
    std::cout << "Circle Area: " << shape1->calculateArea() << std::endl;
    std::cout << "Square Area: " << shape2->calculateArea() << std::endl;
    return 0;
}

```

In this example, we have an abstract class `Shape`, which defines a pure virtual function `calculateArea()`. A pure virtual function has no implementation in the base class and requires derived classes to provide an implementation. This allows us to achieve data abstraction by hiding the details of how each shape calculates its area.

The `Circle` and `Square` classes inherit from the `Shape` class and implement the `calculateArea()` function accordingly. The user interacts with the shapes through the common `Shape` abstract base class, not knowing the specific implementation details of how the area is calculated for each shape.