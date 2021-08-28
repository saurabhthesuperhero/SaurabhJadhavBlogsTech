## Working with Lists & Dictionaries in Python

Hi, Guys Today we will learn about List and Dictionaries in python.

Python is an interpreted high-level general-purpose programming language. Its design philosophy emphasizes code readability with its use of significant indentation. Its language constructs as well as its object-oriented approach aim to help programmers write clear, logical code for small and large-scale projects.

# Lists

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

### Creating another list

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

### Use Negative index

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
[1, 'python', 2, 'kotlin', 3, 4, 5] ##after adding kotlin
```

### Append function

```
ls.append("gorilla")
print(ls)
```

##### Output

```
[1, 'python', 2, 'kotlin', 3, 4, 5, 'gorilla']
```

### Pop operation

```
ls.pop()
print(ls)
```

##### Output

```
[1, 'python', 2, 'kotlin', 3, 4, 5]
```

### Pop specific

```
ls.pop(2)
print(ls)
```

##### Output

```
[1, 'python', 'kotlin', 3, 4, 5]
```

### Remove

```
ls.remove(3)
print(ls)
```

##### Output

```
[1, 'python', 'kotlin',4, 5]
```

### Clear 

```
ls.clear()
print(ls)
```

##### Output

```
[]
```

### Adding lists into one list

```
lt=["hello","dance","sheeran"] #creating a new list lt
print(lt)
print(ls)
ls=[1,2,3,4] #creating new list ls
newls=[ls,lt] # adding list as item to list
print(newls)
```

##### Output

```
['hello', 'dance', 'sheeran'] #lt
[1,2,3,4]  #ls
[[1, 2, 3, 4], ['hello', 'dance', 'sheeran']] #newls
```

-------------------



# Dictionary

**Dictionary** in Python is an unordered collection of data values, used to store data values like a map, which, unlike other Data Types that hold only a single value as an element, Dictionary holds **key:value** pair. Key-value is provided in the dictionary to make it more optimized. 

### Creating a dictionary

The key value are separated by colon ":" and two key-value pair  are spearted by ","

```
dt={"name":"taylor","song":"blank space"}

## Print dictionary
print(dt)
```

##### Output

```
{'name': 'taylor', 'song': 'blank space'}
```

### Access single element

access -> square bracket and pass key name

```
print(dt["name"])
print(dt["song"])
```

##### Output

```
taylor
blank space
```

### Adding values

```
dt.update({"Age":23})
print(dt)
```

##### Output

```
{'name': 'taylor', 'song': 'blank space', 'Age': 23}
```

### Pop

```
dt.pop("song")
print(dt)
```

##### Output

```
{'name': 'taylor', 'Age': 23}
```

###  Pop last item

```
dt.popitem()
print(dt)
```

##### Output

```
{'name': 'taylor'}
```

### Clear

```
dt.clear()
print(dt)
```

##### Output

```
{}
```

### Overwrite value with key

```
dt={"name":"taylor","song":"blank space"}

dt.update({"name":"Ed sheeran"})
print(dt)
```

##### Output

```
{'name': 'Ed sheeran', 'song': 'blank space'}
```

### Keys and Values printing

```
#Print keys

print(dt.keys())
```

##### Output

```
dict_keys(['name', 'song'])
```

### Print values

```
print(dt.values())
```

##### Output

```
dict_values(['Ed sheeran', 'blank space'])
```



## Thank You!!!

Pythoneers , lets meet in next Pyblog.