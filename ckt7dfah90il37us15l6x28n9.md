## Class and Objects - Object Oriented Programming in Python

## Class and Objects - Object Oriented Programming in Python

### Introduction

Classes provide a means of bundling data and functionality together. Creating a new class creates a new *type* of object, allowing new *instances* of that type to be made. Each class instance can have attributes attached to it for maintaining its state. Class instances can also have methods (defined by its class) for modifying its state.

Compared with other programming languages, Python’s class mechanism adds classes with a minimum of new syntax and semantics. It is a mixture of the class mechanisms found in C++ and Modula-3. 

Python classes provide all the standard features of Object Oriented Programming: 

- The class inheritance mechanism allows multiple base classes,
- A derived class can override any methods of its base class or classes
- A method can call the method of a base class with the same name. 
- Objects can contain arbitrary amounts and kinds of data. 
- As is true for modules, classes partake of the dynamic nature of Python: they are created at runtime, and can be modified further after creation.

### Defining Class & Objects

#### Class Definition Syntax

The simplest form of class definition looks like this:

```
class ClassName:
    <statement-1>
    .
    .
    .
    <statement-N>
```

When a class definition is entered, a new namespace is created, and used as the local scope — thus, all assignments to local variables go into this new namespace. In particular, function definitions bind the name of the new function here.

Define Class Code:

```
class Dog:
    pass
```

Dog is the name of Class here.

###  Class Objects

An Object is an instance of a Class. A class is like a blueprint while an instance is a copy of the class with *actual values*.

*Attribute references* use the standard syntax used for all attribute references in Python: `obj.name`. Valid attribute names are all the names that were in the class’s namespace when the class object was created. 

So, if the class definition looked like this:

```
class MyClass:
    """A simple example class"""
    i = 12345

    def f(self):
        return 'hello world'
```

Class *instantiation* uses function notation. Just pretend that the class object is a parameterless function that returns a new instance of the class. For example (assuming the above class):

```
x = MyClass()
```

The instantiation operation (“calling” a class object) creates an empty object. Many classes like to create objects with instances customized to a specific initial state. Therefore a class may define a special method named [`__init__()`](https://docs.python.org/3/reference/datamodel.html#object.__init__), like this:

```
def __init__(self):
    self.data = []
```

When a class defines an [`__init__()`](https://docs.python.org/3/reference/datamodel.html#object.__init__) method, class instantiation automatically invokes [`__init__()`](https://docs.python.org/3/reference/datamodel.html#object.__init__) for the newly-created class instance. So in this example, a new, initialized instance can be obtained by:

Example of having arguments in [`__init__()`]

```
>>> class Complex:
...     def __init__(self, realpart, imagpart):
...         self.r = realpart
...         self.i = imagpart
...
>>> x = Complex(3.0, -4.5)
>>> x.r, x.i
(3.0, -4.5) # Output
```

A program to show example of class creation and object creation and passing arguments:

```
class ImClass(): 
    def __init__(self,object_name,object_id):
        self.name=object_name
        self.id=object_id

abc=ImClass("Iron man",2)     	
xyz=ImClass("Spidey",4)	
```

To access a variable we can do like this:

```
print(abc.name)
print(abc.id)
print(xyz.name)
print(xyz.id)
```

Output:

```
Iron man
2
Spidey
4
```

Here in this blog we understands about class and objects and init() which can be called as constructor like another languages.

In next Blog we will understand more about variables and functions in classes and their scope.  