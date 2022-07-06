---
author: "Chinou van Maris"
created: "06/07/2022 20:53"
tags:
 - coding
 - python
 - cheatsheet
---
# Python Cheatsheet :fab_python:
___
This is a comprehensive list of all the basics of Python. Inspired by [pythoncheatsheet.org](https://www.pythoncheatsheet.org/)
### The Zen of Python
Long time Pythoneer Tim Peters succinctly channels the BDFL's guiding principles for Python's design into 20 aphorisms, only 19 of which have been written down.

```python
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one fucking great idea -- let's do more of those!
```

# Python Basics
___
### Math Operators

| **Operators** | **Operation**     | **Example**     |
| ------------- | ----------------- | --------------- |
| **            | Exponent          | `2 ** 3 = 8`    |
| %             | Modulus/Remainder | `22 % 8 = 6`    |
| //            | Integer division  | `22 // 8 = 2`   |
| /             | Division          | `22 / 8 = 2.75` |
| *             | Multiplication    | `3 * 3 = 9`     |
| -             | Subtraction       | `5 - 2 = 3`     |
| +             | Addition          | `2 + 2 = 4`     |
|               |                   |                 |

## Data Types

| **Data Type**          | **Examples**                              |
| ---------------------- | ----------------------------------------- |
| Integers               | `-2, -1, 0, 1, 2, 3, 4, 5`                |
| Floating-point numbers | `-1.25, -1.0, --0.5, 0.0, 0.5, 1.0, 1.25` |
| Strings                | `'a', 'aa', 'aaa', 'Hello!', '11 cats'`   |

## Variables

You can name a variable anything as long as it obeys the following rules:
1. It can only be one word.
2. It can use only letters, numbers, and the underscore `(_)` character.
3. It can't begin with a number.
4. Variable name starting with an underscore `(_)` are considered as "unuseful".

**Example:**
```python
>>> spam = "Hello"
>>> spam
"Hello"
```

```python
>>> _spam = "Hello"
```
*`_spam` should not be used again in the code.*

## Comments

Inline comment:
```python
# This is a comment
```

Multiline comment:
```python
# This is a 
# multiline comment
```

Code with a comment:
```python
a = 1 # initialization
```

Function docstring:

```python
def foo():
	"""
	This is a function docstring
	You can also user:
	''' Function Docstring '''
	"""
```

## The print() Function
Example Code:
```python
>>> print('What is your name?')   # ask for their name
>>> myName = input()
>>> print('It is good to meet you, {}'.format(myName))
What is your name?
Al
It is good to meet you, Al
```

## The len() Function
Evaluates to the integer value of the number of characters in a string:
```python
>>> len('hello')
5
```

Note: test of emptiness of strings, lists, dictionary, etc, should **not** use len, but prefer direct boolean evaluation.

```python
>>> a = [1, 2, 3]
>>> if a:
>>>   print("the list is not empty!")
```

## The str(), int() and float() Functions
Integer to String or Float:
```python
>>> str(29)
'29'
```

```python
>>> print('I am {} years old.'.format(str(29)))
I am 29 years old.
```

```python
>>> str(-3.14)
'-3.14'
```

Float to Integer:
```python
>>> int(7.7)
7
```

```python
>>> int(7.7) + 1
8
```
___
# Flow Control

## Comparison Operators
| **Operator** | **Meaning**              |
| ------------ | ------------------------ |
| ==           | Equal to                 |
| !=           | Not equal to             |
| <            | Less than                |
| >            | Greater than             |
| <=           | Less than or Equal to    |
| >=           | Greater than or Equal to |
These operators evaluate to True or False depending on the values you give them.

Examples:
```python
>>> 42 == 42
True
```

```python
>>> 40 == 42
False
```

```python
>>> 'hello' == 'hello'
True
```

```python
>>> 'hello' == 'Hello'
False
```

```python
>>> 'dog' != 'cat'
True
```

```python
>>> 42 == 42.0
True
```

```python
>>> 42 == '42'
False
```

## Boolean evaluation
Never use `==` or `!=` operator to evaluate boolean operation. Use the `is` or `is not` operators, or use implicit boolean evaluation.

NO (even if they are valid Python):
```python
>>> True == True
True
```

```python
>>> True != False
True
```

YES (even if they are valid Python):
```python
>>> True is True
True
```

```python
>>> True is not False
True
```

These statements are equivalent:

```python
>>> if a is True:
>>>    pass
>>> if a is not False:
>>>    pass
>>> if a:
>>>    pass
```

And these as well:

```python
>>> if a is False:
>>>    pass
>>> if a is not True:
>>>    pass
>>> if not a:
>>>    pass
```

## Boolean Operators
There are three Boolean operators: and, or, and not.

The _and_ Operator’s _Truth_ Table:
| **Expression**    | **Evaluates to** |
| ----------------- | ---------------- |
| `True and True`   | `True`           |
| `True and False`  | `False`          |
| `False and True`  | `False`          |
| `False and False` | `False`          |
The _or_ Operator’s _Truth_ Table:
| **Expression** | **Evaluates to** |
| -------------- | ---------------- |
| `True or True` | `True`           |
| ``               |                  |
