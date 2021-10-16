## Inheritance in Python - OOPS

## Inheritance in Python - OOPS

Summary: in this tutorial, you’ll learn about Python inheritance and how to use the inheritance to reuse code from an existing class.

Lets start with Person Class:

```python
class Person:
    def __init__(self, first_name, last_name, age):
        self.first_name = first_name
        self.last_name = last_name
        self.age = age

    def introduce(self):
        return f"Hi. I'm {self.first_name}. I'm {self.age} years old."
```

Suppose that you need to create a new class that represents an Student, called `Student` class.

Since an employee has a first name, last name, age, and behaviors like a person, you may want to copy the code from the `Person` class to the `Student` class.

But if you do so, you’ll have duplicate code. In other words, you’ll have the same piece of code in two classes. And it’ll take you double efforts to maintain the classes.

Instead of copying code from the `Person` class to the `Student` class, you can create a relationship between the student and person. An student is a person.

In object-oriented programming, you use inheritance to model the **is a** relationship.

The **benefits** of inheritance are: 

1. It represents real-world relationships well.
2. It provides **reusability** of a code. We don’t have to write the same code again and again. Also, it allows us to add more features to a class without modifying it.
3. It is transitive in nature, which means that if class B inherits from another class A, then all the subclasses of B would automatically inherit from class A.

### Inherit

The following shows the syntax for defining a class that inherits from another class:

```
class child_class(parent_class):
    ...
```

In this syntax, you place the parent class within the parentheses following the name of the child class.

The following example illustrates how to define the `Employee` class that inherits from the `Person` class:

```
class Student(Person):
	pass
```

Since the `Student` class is empty, you place the `pass` statement in its body to make the syntax valid.

So lets take example by code.

This is how we normally can assign attribute to class object withought defining variable in class definantion.

```
class class2:
    pass
abc=class2()
abc.name="Saurabh Jadhav"
print(abc.name)
```

Learn more about classes and objects in [Python Series](https://saurabhjadhavblogs.com/series/python)

Now lets do same with Inheritance:

```
class Person():
    def __init__(self,name,age,gender):
        self.name=name
        self.age=age
        self.gender=gender        
class Student(Person):
    pass 
```

We defined class Person and and inherited that class in Student class.

```
id1=Student("wonder woman",122,"female")
```

We created object id1 and assign constructor values for Person class arguments.

```
id1.course="swordmanship"
id1.rollno=2
id1.year=3
```

We added attributes and assign values to them.

```
print("Name:",id1.name,"Age:",id1.age,
"course:",id1.course,"year of study",
id1.year)
```

Output:

```
Name: wonder woman Age:122 course:swordmanship yearofstudy3 
```

Full program:

```python
#inheritance withought child class constructor
class Person():
    def __init__(self,name,age,gender):
        self.name=name
        self.age=age
        self.gender=gender        
class Student(Person):
    pass  
id1=Student("wonder woman",122,"female")
id1.course="swordmanship"
id1.rollno=2
id1.year=3
print("Name:",id1.name,"Age:",id1.age,
"course:",id1.course,"year of study",
id1.year)
```



### Add constructor in child class

Lets define Parent Class:

```
class Person():
    def __init__(self,name,age,gender):
        self.name=name
        self.age=age
        self.gender=gender 
```

Now we need child class student with roll no etc.

```
class Student(Person):
    def __init__(self,rollno,course,year,
    name,age,gender):
        super().__init__(name,age,gender)
        self.rollno=rollno
        self.course=course
        self.year=year  
```

Notice the super() line here.

Why we added this?

When We add `__init__` in child class it overrrides the parent class's `__init__` .

So first we added all parent class constructor arguments and child class arguments in child class constructore like this:

```
  def __init__(self,rollno,course,year,
    name,age,gender):
```

Now we call super() method with init and pass arguments for parent class constructore like this:

```
super().__init__(name,age,gender)
```

thats it now we have both classes base and child class with constructors.

Full code:

```
#inheritance with child class constructor
class Person():
    def __init__(self,name,age,gender):
        self.name=name
        self.age=age
        self.gender=gender        
class Student(Person):
    def __init__(self,rollno,course,year,
    name,age,gender):
        super().__init__(name,age,gender)
        self.rollno=rollno
        self.course=course
        self.year=year  
id1=Student(1,"Boxing",4,"superman",17,
"male")
print("Name:",id1.name,"Age:",id1.age,
"course:",id1.course)
```

Output:

```
Name: superman Age: 17 course: Boxing
```

### Use of Methods in Inheritance

Lets create parent class again:

```
class Person():
    def __init__(self,name,age,gender):
        self.name=name
        self.age=age
        self.gender=gender 
```

Now create child class and use a method to print data.

```
class Student(Person):
    def intoduce(self):
        print("My name is ",self.name)
        print("My age is ",self.age,
        "and my gender is ",
        self.gender)
```

Now we can just create a child and use method like this:

```
id1=Student("wonder woman",2,"female")
id1.intoduce()
```

Full  code:

```
#inheritance and methods
class Person():
    def __init__(self,name,age,gender):
        self.name=name
        self.age=age
        self.gender=gender        
class Student(Person):
    def intoduce(self):
        print("My name is ",self.name)
        print("My age is ",self.age,
        "and my gender is ",
        self.gender)

id1=Student("wonder woman",2,"female")
id1.intoduce()

```

Output:

```
My name is  wonder woman
My age is  2 and my gender is  female
```

### Multilevel inheritance

We will create this heirarchy:

```
class Person():
	pass
class Student(Person):
	pass
class Child(Student):
	pass
```

The code is almost same as we did above we will add new class and method here.

```
class Child(Student):
    def intoduce(self):
        print("My name is ",self.name)
        print("My age is: ",self.age,"and my gender is: ",self.gender)
    def introduceSchooling(self):
        print("I m in ",self.year,"year of ",self.course,"course",
        "where my roll no is",self.rollno)
```

In class child we added two methods.

We Student in child, and first method get data stored from `Person Class` and second method get data stored from `Student Class`

Lets See whole code:

```
#inheritance and methods
class Person():
    def __init__(self,name,age,gender):
        self.name=name
        self.age=age
        self.gender=gender   

class Student(Person):
    def __init__(self,rollno,course,year,
    name,age,gender):
        super().__init__(name,age,gender)
        self.rollno=rollno
        self.course=course
        self.year=year               
class Child(Student):
    def intoduce(self):
        print("My name is ",self.name)
        print("My age is: ",self.age,"and my gender is: ",self.gender)
    def introduceSchooling(self):
        print("I m in ",self.year,"year of ",self.course,"course",
        "where my roll no is",self.rollno)

id1=Child(1,"laxmichitfund(21 din me double)",2,"wonder woman",2,"female")
id1.intoduce()
id1.introduceSchooling()
```

Output:

```
My name is  wonder woman
My age is:  2 and my gender is:  female
I m in  2 year of  laxmichitfund(21 dinme double) course where my roll no is 1
```

So that was about it.