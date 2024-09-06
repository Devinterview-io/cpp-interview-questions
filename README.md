# Top 100 C++ Interview Questions

<div>
<p align="center">
<a href="https://devinterview.io/questions/web-and-mobile-development/">
<img src="https://firebasestorage.googleapis.com/v0/b/dev-stack-app.appspot.com/o/github-blog-img%2Fweb-and-mobile-development-github-img.jpg?alt=media&token=1b5eeecc-c9fb-49f5-9e03-50cf2e309555" alt="web-and-mobile-development" width="100%">
</a>
</p>

#### You can also find all 100 answers here 👉 [Devinterview.io - C++](https://devinterview.io/questions/web-and-mobile-development/c++-interview-questions)

<br>

## 1. What are the main _features_ of _C++_?

**C++** is renowned for its diverse set of features, many of which it inherited from **C** but also enhanced and expanded upon. These features enable a wide range of programming paradigms, from procedural to object-oriented and generic programming.

### Key Features

#### Efficiency

- **Low-Level Access**: Pointers, direct memory manipulation.
- **Resource Management**: Smart pointers, deterministic destructors with RAII.
- **Inline Functions**: Eliminates function call overhead.
- **Move Semantics**: Transfers resources rather than copying.

#### Flexibility in Types

- **Strongly-Typed**: Encourages type safety.
- **Type Inference**: `auto` keyword deduces types.
- **Concepts** (C++20): Constraints and requirements for templates.

#### Multiple Paradigms

- **Procedural**: Functions and control structures.
- **OOP Support**: Classes, objects, inheritance, polymorphism.
- **Functional Features**: Lambdas, `constexpr`, immutability.
- **Generic Programming**: Templates and concepts.

#### Standard Library

- **Rich in Utilities**: Data structures, algorithms, I/O facilities.
- **Modularity**: Components like `<algorithm>` encourage algorithmic abstraction.
- **Ranges** (C++20): Composable algorithm sequences.

#### Code Reusability

- **Inheritance**: Base classes and derived classes.
- **Composition**: Building classes from other objects.
- **Association**: Member objects and relationships.

#### Polymorphism

- **Compile-Time**: Templates and concepts.
- **Run-Time**: Virtual functions, dynamic_cast.

#### Memory Management

- **Stack vs. Heap**: Automatic storage (`stack`), dynamic memory via pointers.
- **Smart Pointers**: Ownership-aware pointers (`unique_ptr`, `shared_ptr`, `weak_ptr`).
- **RAII**: Resource Acquisition Is Initialization.

#### Modern Features

- **Coroutines** (C++20): Simplified asynchronous programming.
- **Modules** (C++20): Improved code organization and compilation.
- **Constexpr**: Compile-time computation.

### Code Example: Features in Action

```cpp
#include <iostream>
#include <vector>
#include <memory>
#include <concepts>

template <typename T>
concept Numeric = std::is_arithmetic_v<T>;

template <Numeric T>
T addOne(const T& val) {
    return val + 1;
}

struct Animal {
    virtual void speak() const = 0;
    virtual ~Animal() = default;
};

struct Dog : public Animal {
    void speak() const override { std::cout << "Woof!" << std::endl; }
};

int main() {
    std::vector<int> vec { 1, 2, 3 };
    for (const auto& num : vec) {
        std::cout << addOne(num) << std::endl;
    }

    auto dog = std::make_unique<Dog>();
    dog->speak();

    // C++20 feature: constexpr vector
    constexpr std::vector<int> constexpr_vec{1, 2, 3, 4, 5};
    static_assert(constexpr_vec.size() == 5);

    return 0;
}
```
<br>

## 2. Explain the _difference_ between _C_ and _C++_.

- **C**: Developed primarily for system programming at Bell Labs in the 1970s. It laid the foundation for many operating systems and is still widely used.
- **C++**: Emerged in the early 1980s as an extension of C, introducing object-oriented programming (OOP) paradigms. It has since evolved to incorporate features from multiple programming paradigms.

### Key Distinctions

#### Paradigms

- **C**: Primarily _procedural_.
- **C++**: _Multi-paradigm_; supports procedural, OOP, generic, and functional programming.

#### Function Overloading

- **C**: Doesn't support overloading.
- **C++**: Allows _function overloading_, enabling multiple functions with the same name but different parameters.

```cpp
// C++ function overloading example
int add(int a, int b) { return a + b; }
double add(double a, double b) { return a + b; }
```

#### Memory Management

- **C**: Manual memory management using functions like `malloc()` and `free()`.
- **C++**: Offers both manual management and automated options via _RAII_ (Resource Acquisition Is Initialization), _smart pointers_, and the `new` and `delete` operators.

```cpp
// C++ smart pointer example
#include <memory>
std::unique_ptr<int> ptr = std::make_unique<int>(42);
```

#### Code Organization

- **C**: Organizes code into functions and modules.
- **C++**: Extends this with _classes_, _objects_, _inheritance_, and other OOP features.

#### Standard Libraries

- **C**: Uses the C Standard Library.
- **C++**: Incorporates the C++ Standard Library, which includes the C Standard Library and adds features like _containers_, _algorithms_, and _streams_.

#### Header Files

- **C**: Typically uses `.h` extension for header files.
- **C++**: Uses headers without the `.h` extension (e.g., `<iostream>`), though it can still use C-style headers.

#### Type Safety

- **C**: Provides basic type checking.
- **C++**: Offers stronger type checking and features like _templates_ for improved type safety.

```cpp
// C++ template example
template <typename T>
T max(T a, T b) { return (a > b) ? a : b; }
```

#### Object-Oriented Features

- **C**: Does not support OOP concepts natively.
- **C++**: Fully supports OOP with _classes_, _inheritance_, _polymorphism_, and _encapsulation_.

#### Exception Handling

- **C**: Doesn't support exceptions natively.
- **C++**: Provides built-in _exception handling_ mechanisms.

```cpp
// C++ exception handling example
try {
    // code that might throw an exception
} catch (const std::exception& e) {
    std::cerr << "Caught exception: " << e.what() << std::endl;
}
```

#### Boolean Type

- **C**: Traditionally uses integers for boolean values (0 for false, non-zero for true).
- **C++**: Introduces a built-in `bool` type with `true` and `false` keywords.

#### Standardization

- **C**: Latest standard is C17 (ISO/IEC 9899:2018), with C23 in development.
- **C++**: Latest standard is C++20, with C++23 nearing completion.
<br>

## 3. What is _object-oriented programming_ in _C++_?

**Object-Oriented Programming** (OOP) is a programming paradigm that organizes code into reusable and self-contained units called **objects**. Each object groups **data attributes** (characteristics) and **methods** (behaviors) that operate on the data.

### The Four Pillars of OOP

1. **Encapsulation**: Objects hide their internal state and behavior, exposing a controlled public interface.
2. **Inheritance**: Defines an "is-a" relationship, allowing objects of a derived class to access attributes and behaviors of a base class.
3. **Polymorphism**: Enables objects to be treated as instances of their parent class while exhibiting their own behaviors.
4. **Abstraction**: Simplifies complex systems by focusing on high-level actions while hiding implementation details.

### Key OOP Concepts in C++

#### Classes and Objects

A `class` is a blueprint for creating objects:

```cpp
class Car {
private:
    std::string model;
    int year;

public:
    Car(std::string m, int y) : model(m), year(y) {}
    void display() {
        std::cout << year << " " << model << std::endl;
    }
};

int main() {
    Car myCar("Tesla", 2023);
    myCar.display();
    return 0;
}
```

#### Inheritance

C++ supports single and multiple inheritance:

```cpp
class ElectricCar : public Car {
private:
    int batteryCapacity;

public:
    ElectricCar(std::string m, int y, int bc) : Car(m, y), batteryCapacity(bc) {}
};
```

#### Polymorphism

C++ supports both compile-time (function overloading, templates) and runtime polymorphism (virtual functions):

```cpp
class Vehicle {
public:
    virtual void start() = 0;  // Pure virtual function
};

class Car : public Vehicle {
public:
    void start() override {
        std::cout << "Car started" << std::endl;
    }
};
```

#### Encapsulation

C++ uses access specifiers (`public`, `private`, `protected`) to control member visibility:

```cpp
class BankAccount {
private:
    double balance;

public:
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
};
```

#### Abstraction

Abstract classes and interfaces in C++ are created using pure virtual functions:

```cpp
class Shape {
public:
    virtual double area() = 0;  // Pure virtual function
};

class Circle : public Shape {
private:
    double radius;

public:
    Circle(double r) : radius(r) {}
    double area() override {
        return M_PI * radius * radius;
    }
};
```

### Modern C++ OOP Features

- **Smart Pointers**: `std::unique_ptr`, `std::shared_ptr`, and `std::weak_ptr` for better resource management.
- **Move Semantics**: Efficient transfer of resources between objects.
- **Lambda Expressions**: Inline function objects for more flexible OOP designs.
- **Concepts** (C++20): Constraints on template parameters for improved type checking and error messages.
<br>

## 4. What are the _access specifiers_ in _C++_ and what do they do?

Access specifiers are keywords in C++ that control the visibility and accessibility of class members. They enable the **principle of data encapsulation**, ensuring data integrity and promoting a clear separation between a class's interface and its implementation.

### Types of Access Specifiers

C++ provides three main access specifiers:

1. **`public`**: Members are accessible from any part of the program. This category typically includes the class's interface—its public methods and data.

2. **`protected`**: Access is limited to the containing class, its derived classes, and friends. This specifier is useful in inheritance scenarios.

3. **`private`**: Members are accessible only from within the containing class and its friends. This is the default access level for class members and ensures that the class's internal implementation details are hidden from external users.

### Code Example

Here's a comprehensive example demonstrating the use of access specifiers in C++:

```cpp
#include <iostream>

class MyClass {
public:
    void publicMethod() {
        std::cout << "Public method, accessing private data: " << privateData << std::endl;
    }

    struct PublicStruct {
        int data;
    };

    enum class Visibility { Hidden, Visible };

    Visibility toggleVisibility() {
        visibility = (visibility == Visibility::Visible) ? Visibility::Hidden : Visibility::Visible;
        return visibility;
    }

protected:
    int protectedData = 20;

private:
    int privateData = 10;
    Visibility visibility = Visibility::Visible;
};

class DerivedClass : public MyClass {
public:
    void accessProtectedData() {
        std::cout << "Accessing protected data: " << protectedData << std::endl;
        // Cannot access privateData here
    }
};

int main() {
    MyClass obj;
    obj.publicMethod(); // OK
    // obj.privateData; // Error: privateData is not accessible
    // obj.protectedData; // Error: protectedData is not accessible

    DerivedClass derived;
    derived.publicMethod(); // OK
    derived.accessProtectedData(); // OK
    // derived.privateData; // Error: privateData is not accessible

    return 0;
}
```

### Key Points

- **`public`** members can be accessed from anywhere in the program.
- **`protected`** members are accessible within the class, its derived classes, and friends.
- **`private`** members are only accessible within the class and its friends.
- The default access specifier for class members is **`private`**.
- Structs and unions default to **`public`** access, unlike classes.
- Access specifiers can be used multiple times within a class definition to change the access level of subsequent members.

### Modern C++ Considerations

In modern C++ (C++11 and later):

- Use of the `class` keyword for inheritance implies **`private`** inheritance by default.
- Use of the `struct` keyword for inheritance implies **`public`** inheritance by default.
- The `friend` keyword allows a function or another class to access private and protected members of a class.
- C++11 introduced strongly typed enums (`enum class`), which have the same access control as regular classes.
<br>

## 5. Explain the concept of _namespaces_ in _C++_.

**Namespaces** in C++ are a fundamental feature used to organize code into logical groups and prevent naming conflicts. They provide a way to encapsulate related functionality and avoid naming collisions in large projects.

### Key Concepts

#### Namespace Declaration and Usage

Namespaces are declared using the `namespace` keyword:

```cpp
namespace MyNamespace {
    // Declarations and definitions
}
```

To use elements from a namespace, you can either:

1. Use the scope resolution operator `::`:

```cpp
MyNamespace::function();
```

2. Use the `using` directive:

```cpp
using namespace MyNamespace;
function(); // Now directly accessible
```

#### Nested Namespaces

Namespaces can be nested within other namespaces:

```cpp
namespace Outer {
    namespace Inner {
        // Declarations and definitions
    }
}
```

In C++17 and later, you can use nested namespace definitions:

```cpp
namespace Outer::Inner {
    // Declarations and definitions
}
```

#### Unnamed Namespaces

Unnamed (or anonymous) namespaces limit the visibility of their contents to the current translation unit:

```cpp
namespace {
    int hidden_variable = 42;
}
```

#### Namespace Aliases

You can create aliases for long namespace names:

```cpp
namespace very_long_namespace_name {
    void function();
}

namespace vln = very_long_namespace_name;
vln::function(); // Equivalent to very_long_namespace_name::function();
```

### Code Example

Here's a comprehensive example demonstrating various namespace concepts:

```cpp
#include <iostream>

// Standard namespace
namespace std_example {
    void print(const char* message) {
        std::cout << "Standard: " << message << std::endl;
    }
}

// Nested namespace
namespace outer {
    namespace inner {
        void print(const char* message) {
            std::cout << "Nested: " << message << std::endl;
        }
    }
}

// Unnamed namespace
namespace {
    void print(const char* message) {
        std::cout << "Unnamed: " << message << std::endl;
    }
}

int main() {
    std_example::print("Hello from std_example");
    outer::inner::print("Hello from outer::inner");
    print("Hello from unnamed namespace");

    // Using directive
    using namespace std_example;
    print("Using std_example namespace");

    return 0;
}
```
<br>

## 6. What is the _difference_ between '_struct_' and '_class_' in _C++_?

In C++, both `struct` and `class` are used to create **user-defined data types**, but they have key differences in their default member access levels, default inheritance access levels, and intended use-cases.

### Key Distinctions

1. **Member Access Levels**:
   - `struct`: Members are **public** by default.
   - `class`: Members are **private** by default.

2. **Inheritance Access Levels**:
   - `struct`: **Public** inheritance is the default.
   - `class`: **Private** inheritance is the default.

3. **Usage-Centric Distinctions**:
   - `struct`: Suited for small, simple objects with data that is mostly public.
   - `class`: Intended for larger, more complex objects that use encapsulation, data hiding, and have specific member functions.

### Code Example: struct vs. class

```cpp
#include <iostream>
#include <string>

struct PersonStruct {
    std::string name;
    int age;
};

class PersonClass {
private:
    std::string name;
    int age;

public:
    void setName(const std::string& newName) {
        name = newName;
    }

    void setAge(int newAge) {
        if (newAge > 0)
            age = newAge;
    }

    std::string getName() const {
        return name;
    }

    int getAge() const {
        return age;
    }
};

int main() {
    // struct members are public by default
    PersonStruct myStructPerson { "John", 30 };
    std::cout << "Name: " << myStructPerson.name << ", Age: " << myStructPerson.age << std::endl;

    // class members are private by default
    PersonClass myClassPerson;
    myClassPerson.setName("Jane");
    myClassPerson.setAge(25);
    std::cout << "Name: " << myClassPerson.getName() << ", Age: " << myClassPerson.getAge() << std::endl;

    return 0;
}
```

### Additional Considerations

- In modern C++, the distinction between `struct` and `class` is mainly a matter of default access specifiers.
- The choice between `struct` and `class` often depends on the design intent and coding style guidelines of a project.
- Some developers use `struct` for **Plain Old Data** (POD) types and `class` for more complex objects with behaviors.
- Both `struct` and `class` can have member functions, constructors, and destructors.
- The `struct` keyword is retained in C++ for backward compatibility with C and to provide a quick way to create simple data structures.
<br>

## 7. What is a _constructor_ and what are its _types_ in _C++_?

A **constructor** in C++ is a special member function responsible for initializing instances of a class. Constructors are called automatically when an object is created.

### Types of Constructors

#### 1. Default Constructor

If a class doesn't have any constructors specified, the compiler automatically generates a default constructor. Its role is to initialize the object to a default state.

```cpp
class MyClass {
public:
    MyClass() = default;  // Explicitly defaulted constructor
};
```

#### 2. Parameterized Constructor

Designed to accept arguments for custom object initialization.

```cpp
class Person {
public:
    Person(const std::string& name, int age) : name_(name), age_(age) {}
private:
    std::string name_;
    int age_;
};
```

#### 3. Copy Constructor

Used for creating an object as a copy of an existing object. The parameter is typically a `const` reference to the same class.

```cpp
class MyClass {
public:
    MyClass(const MyClass& other) : data_(other.data_) {}
private:
    int data_;
};
```

#### 4. Move Constructor

Optimized for moving data from temporary objects or rvalue references. Introduced in C++11.

```cpp
class MyClass {
public:
    MyClass(MyClass&& other) noexcept : data_(std::move(other.data_)) {}
private:
    std::vector<int> data_;
};
```

#### 5. Delegating Constructor (C++11)

Allows a constructor to call another constructor of the same class.

```cpp
class Rectangle {
public:
    Rectangle(int l, int w) : length(l), width(w) {}
    Rectangle() : Rectangle(0, 0) {}  // Delegating constructor
private:
    int length, width;
};
```

#### 6. Inherited Constructor (C++11)

Allows a derived class to inherit constructors from its base class.

```cpp
class Base {
public:
    Base(int x) : x_(x) {}
private:
    int x_;
};

class Derived : public Base {
public:
    using Base::Base;  // Inherit constructors from Base
};
```

### Key Points

- Constructors are declared in the **`public`** section of the class.
- Multiple constructors can coexist in a class (**constructor overloading**).
- Use **member initializer lists** for efficient initialization, especially for `const` members and base classes.
- Consider using `= default` for explicitly defaulted constructors and `= delete` for deleted constructors (C++11).
- Implement the **Rule of Five** (or Rule of Zero) for classes managing resources: define or delete copy constructor, move constructor, copy assignment, move assignment, and destructor.
- Use **`std::move`** in move constructors to transfer ownership of resources efficiently.
<br>

## 8. Explain the concept of _destructors_ in _C++_.

In C++, a **destructor** is a special member function that is automatically called when an object goes out of scope or is explicitly deleted using the `delete` keyword. Its primary purpose is to ensure **proper cleanup** of the object's allocated resources.

### Key Features

- **Automatic Invocation**: Destructors are called implicitly when an object leaves its scope or is explicitly deleted.

- **Syntax**: Destructors are identified by the `~` symbol followed by the class name (e.g., `~MyClass()`).

- **No Return Type or Arguments**: Destructors don't return a value and typically don't take any arguments.

- **Order of Destruction**: Objects are destroyed in the reverse order of their creation.

- **Virtual Destructors**: Essential for polymorphic behavior in inheritance hierarchies.

### Code Example

```cpp
class Resource {
public:
    Resource() { std::cout << "Resource acquired\n"; }
    ~Resource() { std::cout << "Resource released\n"; }
};

class MyClass {
private:
    Resource* resource;
public:
    MyClass() : resource(new Resource()) {}
    ~MyClass() { delete resource; }
};
```

### Use Cases

1. **Memory Management**: Releasing dynamically allocated memory.

   ```cpp
   class DynamicArray {
   private:
       int* arr;
       size_t size;
   public:
       DynamicArray(size_t s) : size(s), arr(new int[s]) {}
       ~DynamicArray() { delete[] arr; }
   };
   ```

2. **File Handling**: Closing open files.

   ```cpp
   class FileHandler {
   private:
       std::ofstream file;
   public:
       FileHandler(const std::string& filename) : file(filename) {}
       ~FileHandler() { if (file.is_open()) file.close(); }
   };
   ```

3. **Resource Management**: Closing database connections, network sockets, etc.

### Best Practices

- **RAII (Resource Acquisition Is Initialization)**: Use destructors to implement RAII, ensuring resources are properly managed.

- **Virtual Destructors**: Always declare destructors as `virtual` in base classes intended for inheritance.

   ```cpp
   class Base {
   public:
       virtual ~Base() = default;
   };
   ```

- **Noexcept Specifier**: Modern C++ recommends marking destructors as `noexcept`.

   ```cpp
   class Modern {
   public:
       ~Modern() noexcept {
           // Cleanup code
       }
   };
   ```

### C++11 and Beyond

- **= default**: You can explicitly request a default destructor.

   ```cpp
   class DefaultDtor {
   public:
       ~DefaultDtor() = default;
   };
   ```

- **Smart Pointers**: Modern C++ encourages using smart pointers (`std::unique_ptr`, `std::shared_ptr`) which manage their own destruction, reducing the need for explicit destructors in many cases.
<br>

## 9. What is _function overloading_ in _C++_?

**Function overloading** in C++ is a feature that allows multiple functions to have the same name but different parameter lists. The compiler distinguishes between these functions based on the **number**, **types**, and **order** of parameters.

### Key Concepts

#### Parameter Lists

- Functions are differentiated based on:
  - Types of parameters
  - Order of parameters
  - Total number of parameters

- An empty parameter list is valid (nullary function)

#### Restrictions

- Return type alone is not sufficient to differentiate functions
- Overloading works for both global and member functions

### Code Example

Here's a C++ code snippet demonstrating function overloading:

```cpp
#include <iostream>
#include <string>

void print(int num) {
    std::cout << "Integer: " << num << std::endl;
}

void print(double num) {
    std::cout << "Double: " << num << std::endl;
}

void print(const std::string& str) {
    std::cout << "String: " << str << std::endl;
}

int main() {
    print(5);
    print(3.14);
    print(std::string("Overloading"));
    return 0;
}
```

### Best Practices

- **Consistent Naming**: Use function names that reflect their purpose
- **Clarity Over Complexity**: Use overloading judiciously to maintain readability
- **Combine with Default Arguments**: Consider using default arguments to reduce the number of overloaded functions

#### Modern C++ Considerations

- With C++11 and later, consider using **variadic templates** for more flexible function overloading
- Use `std::string` instead of `const char*` for string parameters in modern C++ code
- Utilize `constexpr` for compile-time evaluations when applicable
<br>

## 10. What is _operator overloading_ in _C++_?

**Operator overloading** in C++ allows developers to define custom behaviors for operators when used with user-defined types such as classes and structures. This feature enables the creation of more intuitive and expressive code by extending the functionality of standard operators to work with custom types.

### Key Concepts

- **Custom Behavior**: Operators can be redefined to perform specific actions for user-defined types.
- **Syntax Enhancement**: Allows for more natural and readable code when working with custom types.
- **Type-Specific Operations**: Enables the implementation of operations that are meaningful for particular classes or structures.

### Syntax for Operator Overloading

Operators can be overloaded using either member functions or non-member functions (often declared as `friend` functions).

#### Member Function Syntax

```cpp
class MyClass {
public:
    MyClass operator+(const MyClass& other) const {
        // Implementation
    }
};
```

#### Non-member Function Syntax

```cpp
class MyClass {
    // Class definition
};

MyClass operator+(const MyClass& lhs, const MyClass& rhs) {
    // Implementation
}
```

### Commonly Overloaded Operators

- Arithmetic operators (`+`, `-`, `*`, `/`, etc.)
- Comparison operators (`==`, `!=`, `<`, `>`, etc.)
- Assignment operator (`=`)
- Stream insertion and extraction operators (`<<`, `>>`)
- Increment and decrement operators (`++`, `--`)
- Subscript operator (`[]`)

### Best Practices

1. **Maintain Intuitive Behavior**: Overloaded operators should behave consistently with their built-in counterparts.
2. **Preserve Semantics**: The meaning of the operator should remain clear and logical.
3. **Consider Efficiency**: Implement overloaded operators efficiently, especially for frequently used operations.
4. **Use Sparingly**: Overload operators only when it significantly improves code readability and maintainability.
5. **Document Thoroughly**: Clearly document the behavior of overloaded operators, especially if it deviates from standard expectations.

### Code Example: Overloading the Addition Operator

```cpp
class Complex {
private:
    double real, imag;

public:
    Complex(double r = 0, double i = 0) : real(r), imag(i) {}

    Complex operator+(const Complex& other) const {
        return Complex(real + other.real, imag + other.imag);
    }
};

int main() {
    Complex a(1, 2), b(3, 4);
    Complex c = a + b;  // Uses overloaded operator+
    return 0;
}
```

### Limitations and Considerations

- **Cannot Create New Operators**: Only existing operators can be overloaded.
- **Precedence and Arity**: The precedence and number of operands of an operator cannot be changed.
- **Cannot Overload for Built-in Types**: Operators for fundamental types (like `int`, `float`) cannot be overloaded.
- **Some Operators Cannot Be Overloaded**: Operators like `.`, `::`, `?:`, and `sizeof` cannot be overloaded.
<br>

## 11. What is _dynamic memory allocation_ in _C++_?

**Dynamic memory allocation** in C++ allows for memory management during program execution. Unlike automatic and static storage durations, dynamic allocation lets you explicitly control an object's lifetime, size, and location in the program's memory.

### Key Concepts

#### Heap
Dynamic memory is allocated from the **heap**, a large pool of memory that exists throughout the program's runtime. Unlike the stack, which has a fixed and more limited size, the heap can grow and shrink as needed.

#### `new` and `delete` Operators
The operators `new` and `delete` are used for dynamic memory management:
- `new` allocates memory for a single object or an array of objects
- `delete` releases this memory when it's no longer needed, ensuring that the object's destructor is called

#### Smart Pointers
Introduced in C++11, smart pointers provide a safer and more convenient way to manage dynamic memory:
- `std::unique_ptr`: Ensures a single owner for the allocated object
- `std::shared_ptr`: Allows for multiple owners, using a control block to track the object's lifetime
- `std::weak_ptr`: Non-owning "weak" reference to an object managed by `std::shared_ptr`

### Code Example: Using `new` and `delete`

```cpp
#include <iostream>

class DynamicMemoryExample {
public:
    DynamicMemoryExample() { std::cout << "Constructor called!" << std::endl; }
    ~DynamicMemoryExample() { std::cout << "Destructor called!" << std::endl; }
};

int main() {
    int* intPtr = new int(42);  // Allocate memory for an integer on the heap
    std::cout << *intPtr << std::endl;
    delete intPtr;  // Release the memory

    DynamicMemoryExample* array = new DynamicMemoryExample[3];  // Allocate an array of objects
    delete[] array;  // Release the array

    return 0;
}
```

### Code Example: Using Smart Pointers

```cpp
#include <iostream>
#include <memory>

class DynamicMemoryExample {
public:
    DynamicMemoryExample() { std::cout << "Constructor called!" << std::endl; }
    ~DynamicMemoryExample() { std::cout << "Destructor called!" << std::endl; }
};

int main() {
    auto uptr = std::make_unique<int>(42);  // Create a unique pointer to an integer
    std::cout << *uptr << std::endl;

    auto sptr = std::make_shared<DynamicMemoryExample>();  // Create a shared pointer to an object

    auto array = std::make_unique<DynamicMemoryExample[]>(3);  // Create a unique pointer to an array

    return 0;  // Smart pointers automatically release memory when they go out of scope
}
```

### Memory Leaks and Best Practices

- Always pair `new` with `delete` and `new[]` with `delete[]`
- Prefer smart pointers over raw pointers to prevent memory leaks
- Use `std::make_unique` and `std::make_shared` for exception safety and efficiency
- Consider using container classes (e.g., `std::vector`) for dynamic arrays instead of manual allocation
<br>

## 12. Explain the _difference_ between '_new_' and '_malloc()_'.

In C++, both `new` and `malloc()` are used for **dynamic memory allocation**, but they have different origins and characteristics.

### Key Distinctions

1. **Origin**:
   - `new` is part of the C++ language.
   - `malloc()` stems from C.
   
   For modern C++ code, it's generally preferred to use `new`, `new[]` for arrays, and smart pointers like `std::unique_ptr` or `std::shared_ptr` to manage dynamic memory.

2. **Return Type**:
   - `new` returns a pointer of the requested type. If memory allocation fails, it throws a `std::bad_alloc` exception (unless a custom handler is set).
   - `malloc()` returns a `void*` pointer. If allocation fails, it returns `nullptr`.

3. **Object Construction and Destruction**:
   - `new` allocates memory and calls the object's constructor.
   - `malloc()` only allocates raw memory; it doesn't invoke constructors.
   - `delete` calls the object's destructor and then deallocates the memory.
   - `free()` only deallocates the memory without calling any destructors.

4. **Size Specification**:
   - `new` automatically deduces the size based on the type.
   - `malloc()` requires explicit size specification in bytes.

5. **Type Safety**:
   - `new` is type-safe and returns a pointer of the correct type.
   - `malloc()` returns a `void*` that needs to be explicitly cast to the desired type.

### Code Example

```cpp
#include <iostream>
#include <cstdlib>
#include <new>

class Widget {
public:
    Widget(int val) : value(val) { std::cout << "Widget constructed\n"; }
    ~Widget() { std::cout << "Widget destructed\n"; }
private:
    int value;
};

int main() {
    // Using new
    Widget* w1 = new Widget(5);
    int* arr = new int[10];

    // Using malloc
    Widget* w2 = static_cast<Widget*>(std::malloc(sizeof(Widget)));
    
    // Proper construction with placement new
    if (w2) {
        new (w2) Widget(10);
    }

    // Cleanup
    delete w1;  // Calls destructor and deallocates
    delete[] arr;
    
    if (w2) {
        w2->~Widget();  // Manually call destructor
        std::free(w2);  // Deallocate memory
    }

    return 0;
}
```

### Modern C++ Considerations

In modern C++, it's recommended to use smart pointers and container classes instead of raw pointers and manual memory management:

```cpp
#include <memory>
#include <vector>

std::unique_ptr<Widget> w = std::make_unique<Widget>(5);
std::vector<int> vec(10);  // Dynamic array managed by vector
```
<br>

## 13. What is a _memory leak_ and how can it be prevented?

A **memory leak** occurs when a program allocates memory but fails to release it when it's no longer needed. This leads to a gradual reduction in available memory, potentially causing performance issues or program crashes.

### Common Causes of Memory Leaks

- **Missing Deallocation**: Failing to `delete` for every `new` or `free` for every `malloc`.
- **Complex Data Structures**: Forgetting to deallocate memory in structures like linked lists or trees.
- **Circular References**: In garbage-collected languages, circular references between objects can prevent memory reclamation.

### Techniques to Prevent Memory Leaks

#### Manual Memory Management

- **RAII (Resource Acquisition Is Initialization)**: Allocate resources in the constructor and release them in the destructor.
- **Smart Pointers**: Use `std::unique_ptr`, `std::shared_ptr`, or `std::weak_ptr` from the `<memory>` header in C++.

#### Automatic Memory Management

- **Garbage Collection**: Languages with automatic garbage collection reduce the need for manual memory management.

### Best Practices

- **Use Stack Allocation**: Prefer stack-allocated objects when their lifetime aligns with the scope.
- **Prefer Smart Pointers**: Automate memory management to reduce leak likelihood.
- **Clear Ownership**: Establish which part of the code is responsible for deallocation.

### Code Example: Memory Management Techniques

```cpp
#include <iostream>
#include <memory>

class MyResource {
public:
    MyResource() { std::cout << "Resource acquired!\n"; }
    ~MyResource() { std::cout << "Resource released!\n"; }
};

void manualManagement() {
    MyResource* resource = new MyResource();
    // Uncommenting the next line would ensure manual resource release
    // delete resource;
}

void raii() {
    MyResource resource;  // Automatically released when out of scope
}

void smartPointers() {
    auto resource = std::make_unique<MyResource>();
    // Automatically released when unique_ptr goes out of scope
}

int main() {
    std::cout << "RAII:\n";
    raii();

    std::cout << "\nUnique Pointers:\n";
    smartPointers();

    std::cout << "\nManual Memory Management:\n";
    manualManagement();

    return 0;
}
```
<br>

## 14. What is a _dangling pointer_?

A **dangling pointer** is a pointer that references a memory location that has been **deallocated** or is no longer valid. This situation typically occurs when the memory to which the pointer was pointing has been `free`d or `delete`d, or when the object it was referencing has gone out of scope.

### Causes of Dangling Pointers

1. **Premature Deallocation**: Memory is freed or deleted while pointers to it still exist.
2. **Returning Local References**: Returning a reference or pointer to a local variable that goes out of scope.
3. **Use-After-Free**: Accessing memory through a pointer after it has been deallocated.

### Avoiding Dangling Pointers

1. **Smart Pointers**: Utilize `std::unique_ptr`, `std::shared_ptr`, or `std::weak_ptr` from the C++11 standard library to manage memory automatically.
2. **Nullify After Deallocation**: Set pointers to `nullptr` after using `delete`.
3. **RAII (Resource Acquisition Is Initialization)**: Use objects with well-defined lifetimes to manage resources.
4. **Careful Scope Management**: Be mindful of object lifetimes, especially when using raw pointers.

### Code Example: Dangling Pointers

```cpp
#include <iostream>
#include <memory>

void danglingPointerExample() {
    int* rawPtr = new int(5);
    delete rawPtr;
    // rawPtr is now dangling
    // *rawPtr; // Undefined behavior

    // Better approach using smart pointers
    std::unique_ptr<int> smartPtr = std::make_unique<int>(5);
    // No need to manually delete, memory is automatically managed
}

int* returnDanglingPointer() {
    int localVar = 10;
    return &localVar; // Dangling pointer: localVar goes out of scope
}

int main() {
    danglingPointerExample();

    int* danglingPtr = returnDanglingPointer();
    // *danglingPtr; // Undefined behavior

    return 0;
}
```

### Modern C++ Best Practices

1. **Use Smart Pointers**: Prefer `std::unique_ptr` for exclusive ownership and `std::shared_ptr` for shared ownership.
2. **Avoid Raw Pointers**: When possible, use references or smart pointers instead of raw pointers.
3. **Consider `std::optional`**: For functions that might not return a value, use `std::optional` (C++17) instead of nullable pointers.
4. **Use Static Analysis Tools**: Employ tools like Clang Static Analyzer or Cppcheck to detect potential dangling pointer issues.
<br>

## 15. Explain the concept of _smart pointers_ in _C++_.

**Smart pointers** in C++ are objects designed for managing **dynamic memory** in a more automated and safe way than traditional raw pointers.

They offer several advantages:

- **Automated Memory Management**: Simplify memory cleanup using well-defined strategies like reference counting or ownership.
- **Improved Safety**: Minimize risks of memory leaks, dangling pointers, and double deletions.
- **Scoped Ownership**: Establish a clear ownership hierarchy, making it easier to determine which part of the code is responsible for managing the memory.

### Types of Smart Pointers

C++ provides three primary types of smart pointers, all of which are defined in the `<memory>` header:

1. **`std::unique_ptr`**
2. **`std::shared_ptr`**
3. **`std::weak_ptr`**

#### Unique Pointers (`std::unique_ptr`)

- Used for **exclusive ownership** of a dynamically allocated object.
- The object is automatically destroyed when the unique pointer goes out of scope.
- Efficient and lightweight.
- Not copyable, but can be moved.

```cpp
#include <memory>
#include <iostream>

int main() {
    std::unique_ptr<int> uptr = std::make_unique<int>(5);
    // std::unique_ptr<int> uptr2 = uptr; // Error: unique_ptr is not copyable
    std::cout << *uptr << std::endl;
    // Memory is automatically released when uptr goes out of scope
    return 0;
}
```

#### Shared Pointers (`std::shared_ptr`)

- Enable **multiple pointers** to own the same object.
- The object is destroyed when the last shared pointer owning it is destroyed.
- Thread-safe reference counting, but this adds some overhead.
- Can lead to **circular references** if not used carefully.

```cpp
#include <memory>
#include <iostream>

struct Node {
    std::shared_ptr<Node> next;
};

int main() {
    std::shared_ptr<int> sptr = std::make_shared<int>(10);
    {
        std::shared_ptr<int> anotherSptr = sptr;
        std::cout << *anotherSptr << std::endl;
    }
    // The referenced int is still alive

    std::shared_ptr<Node> node1 = std::make_shared<Node>();
    std::shared_ptr<Node> node2 = std::make_shared<Node>();
    node1->next = node2;
    node2->next = node1;  // Creates a circular reference

    // Node objects are still in memory due to the circular reference
    return 0;
}
```

#### Weak Pointers (`std::weak_ptr`)

- Designed to **observe** an object owned by a shared pointer without extending its lifetime.
- Resolves to a shared pointer or an expired state, allowing you to check if the object still exists.
- Helps break circular references in `std::shared_ptr`.

```cpp
#include <memory>
#include <iostream>

int main() {
    std::shared_ptr<int> sPtr = std::make_shared<int>(42);
    std::weak_ptr<int> wPtr = sPtr;

    if (auto locked = wPtr.lock()) {
        std::cout << "Value: " << *locked << std::endl;
    } else {
        std::cout << "The object is no longer available." << std::endl;
    }

    sPtr.reset();  // Release the resource

    if (auto locked = wPtr.lock()) {
        std::cout << "Value: " << *locked << std::endl;
    } else {
        std::cout << "The object is no longer available." << std::endl;
    }

    return 0;
}
```

### Best Practices

- Use `std::make_unique` and `std::make_shared` for creating smart pointers (since C++14).
- Prefer `std::unique_ptr` when single ownership is sufficient.
- Use `std::shared_ptr` when multiple ownership is required.
- Employ `std::weak_ptr` to break circular references and for temporary observation of shared objects.
- Avoid mixing raw pointers and smart pointers for the same resource.
<br>



#### Explore all 100 answers here 👉 [Devinterview.io - C++](https://devinterview.io/questions/web-and-mobile-development/c++-interview-questions)

<br>

<a href="https://devinterview.io/questions/web-and-mobile-development/">
<img src="https://firebasestorage.googleapis.com/v0/b/dev-stack-app.appspot.com/o/github-blog-img%2Fweb-and-mobile-development-github-img.jpg?alt=media&token=1b5eeecc-c9fb-49f5-9e03-50cf2e309555" alt="web-and-mobile-development" width="100%">
</a>
</p>

