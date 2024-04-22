+++
title = "Understanding *args and **kwargs with unpacking in Python"
author = ["Kaushal Bundel"]
date = 2024-04-21T00:00:00+05:30
publishDate = 2024-04-22T00:00:00+05:30
tags = ["python"]
categories = ["python"]
draft = false
+++

## Introduction {#introduction}

For a very long time, I have been confused about \*args and \*\*kwargs in python. This is a short summary of what these terms mean.

Before I go deep into them, I have to make a clear distinction between argument and parameters. For so long, I have been confused about them and used them interchangeably. In theory:

**Parameter**: These are placeholder values used while a function is defined.
**Arguments**: These are the actual values passed into the function when it is called.


### Understanding the need of \*args or \*kwargs {#understanding-the-need-of-args-or-kwargs}

While defining functions, we need to have a clarity on what parameters we are passing, what is the type of these parameters(though not that strictly in python) and if there is any default values for a parameter. But consider the condition:

1.  What if I am not aware of the parameters when defining a function?
2.  What if I want to create a function that can be generic in nature, so that the number of arguments do not matter?

for eg., In this function, I know what are the parameters are and the sum function is created with this knowledge in mind.

```python
#defining a simple sum function

def sum(a, b):
    return a + b
two_num = sum(2, 3)
print(two_num)
```

If I do not have any idea about the parameters and I have to define the function or If I want to create a generic function, that takes many parameters and perform the same function as above code:

```python
#defining a simple sum function that can take multiple arguments

def sum(*args):
    result = 0
    for arg in args:
        try:
            result += arg
        except TypeError:
            print('The arguments must be int. Continue after changing!')
    return result

# using multiple arguments
print(sum(1, 2, 3, "k"))
print(sum(1, 2, 3, 4, 5))
```

The sum function above has become a generic function, that accepts any number of arguments


### Understanding \*args {#understanding-args}

Simply speaking \*args are nothing but tuples.
Now, tuples are immutable which is a fancy way to say that they can not be changed in place. All the remaining operations that can be applied to python lists can be mostly applied to tuples as well.

```python
#defining a simple sum function
def us_args(*args):
    return f"The argument is {args} and the type is {type(args)}"
print(us_args(1, ("john"), [1, 2, 3]))
```

-   Note: We do not have to use \*args specifically, we can use \*&lt;any_name&gt;, it just needs to start with one star.


### Understanding \*\*kwargs {#understanding-kwargs}

\*\*kwargs are dictionaries. The dictionary consists of key, value pairs. The key is accessed with the dictionary name whereas the value is accessed with .value().

```python
def und_kwargs(**kwargs):
    return f"The kwargs is {kwargs} and the type is {type(kwargs)}"

print(und_kwargs(a = "John", b =1))

```

In the example below the sum function can take many named arguments due to the use of \*\*kwargs

```python
#defining a simple sum function using **kwargs
def sum(a=1, b=2, **kwargs):
    result = a + b
    for kwarg in kwargs.values():
        result += kwarg
    return result
#simple sum with 2 arguments
print(sum(2, 3))

#printing sum with keyword arguments
print(sum(a = 4, b= 6))

#printing multiple arguments
print(sum(a= 1, b = 2, c = 3, d = 4 ))
```

-   Note: Like wise to \*args we can use any name for \*\*kwargs it just needs to start with two stars


### Unpacking an argument using "\*" {#unpacking-an-argument-using}

Unpacking means to simply take the values from collection of items(iterables such as list/tuples)/dictionary/str) and converting them to individual variables.

```python
list1 = [1, 2, 3, 4, 5]
print(list1)
print(*list1)
print(*"John Doe")
```

The first row of results show that the list is returned as a list is passed as an argument while the second and third rows shows the 'unpacked' individual variables.

Demonstration using a more complex example:

```python
def demo_star(movie_name1, movie_name2):
    return f'My favorite movie is {movie_name1}, but I also like {movie_name2}'

movie = ['Shawshank Redemption', 'Naked Gun']

print(demo_star(*movie))


```

In this example, the argument was unpacked with a single \*, and the return statement was updated accordingly.

-   Note here that the number of parameters must be equal to the length of the list. If the length of the iterable is more than or less than the number of parameters than the python interpretor will throw an error.


### Unpacking a argument using "\*\*" {#unpacking-a-argument-using}

"\*\*" unpacks when the parameters are named. So to enable unpacking, arguments in the form of a dictionary are provided.

```python
def demo_dub_star(name, subject, marks):
    return f'{name} scored {marks} in {subject}'

student = {'name': 'John', 'subject':'Maths', 'marks':'90'}

print(demo_dub_star(**student))

```

-   Note that the keys in dictionary should be same as the parameter names else the python interpretor will throw an error.


### Combining unpacking and args together {#combining-unpacking-and-args-together}

The usage of both of these features is complimentary to each other. This can be illustrated with an example.

```python

def sum_any_length(*args):
    result = 0
    for nums in args:
       result += nums
    return result

list_nums = [1, 2, 3, 4]

print(sum_any_length(1, 2))
print(sum_any_length(1, 2, *list_nums))
```

In this code block the we can pass any number of arguments with \*args in the parameter. Since a list is passed, we unpack the list using unpacking operator \* to spread the list and sum it.
