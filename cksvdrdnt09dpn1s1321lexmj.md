## Working with Lists & Dictionaries in Python

Hi, Guys Today we will learn about List and Dictionaries in python.

Python is an interpreted high-level general-purpose programming language. Its design philosophy emphasizes code readability with its use of significant indentation. Its language constructs as well as its object-oriented approach aim to help programmers write clear, logical code for small and large-scale projects.

## Lists

List is an mutable data type in python, it is kind of array but supports not only homogenous list of datatypes but mixture too.

In List index of first element starts from 0, list is used to store multiple variable in one variable.

### Creating a list



```
ls = [ "Saurabh", " hashnode", "Python", " datatype"]
print(ls)

``` 
##### Output


```
['Saurabh', ' hashnode', 'Python', ' datatype']

``` 

### Accessing the list element


```
print(ls[2])

``` 
##### Output


```
'Python'

``` 

We can also use negative indexing:

```
print(ls[-1])
``` 

##### Output

```
'datatype'
``` 

### Creation of another list


```
ls=[1,2,3,4,5]
print(ls)

``` 
##### Output

```
[1, 2, 3, 4, 5]
``` 



### Print Specific index


```
print(ls[0]) #?-> 1
print(ls[2])
``` 
##### Output

```
1
3
``` 

### negative index

```
print(ls[-1]) 

``` 
##### Output

```
5
``` 

### Len function

```
print(len(ls))

``` 
##### Output

```
5
``` 

### List insert function

```
ls.insert(1,"python")
print(ls)
ls.insert(3,"kotlin")
print(ls)
``` 
##### Output

```
[1, 'python', 2, 3, 4, 5]
[1, 'python', 2, 'kotlin', 3, 4, 5] #after adding kotlin
``` 

# Append

```
ls.append("gorilla")
print(ls)
``` 

##### Output

```
[1, 'python', 2, 'kotlin', 3, 4, 5, 'gorilla']
``` 




