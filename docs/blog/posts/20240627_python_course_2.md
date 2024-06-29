---
date: 2024-06-27
draft: True
authors: [gabrielbdornas]
comments: true
categories:
  - Python
  - Python course
---

# Python course - Class 2

Have you ever wanted to unlock the power of Python?
This versatile language is used by data scientists, web developers, and even hobbyists to automate tasks, analyze information, and build incredible applications.

<!-- more -->

This content is designed to take you from absolute beginner to Python pro, guiding you step-by-step through the fundamentals and helping you put your newfound skills to the test with exciting projects.
Get ready to join the thriving Python community, let's get started!


## Strings

- Single and doble quotes:

    ```python
    course = 'Python for Beginners' # (1)!
    ```

    1. :man_raising_hand: We can use doble quotes to define a `str` as well. Therefor, the `course` variable could be defined as `course = "Python for Beginners".

- Single or doble quotes:

    ```python
    doble_quote_string = "Python's for Beginners" # (1)!
    print(doble_quote_string)
    single_quote_string = 'Python for "Beginners"' # (2)!
    print(single_quote_string)
    ```

    1. :man_raising_hand: Here, as we need to use an apostrophe (`'s`), the `str` must be defined with doble quotes.
    2. :man_raising_hand: Here, as we need to put `"Beginners"` between doble quotes, the `str` must be defined with single quotes.

- Multiple line strings:

    ```python
    email = '''Hi Gabriel,

    Here is our first contact.

    Thank you for been with us.
    Your team
    '''
    print(email) # (1)!
    ```

    1. :man_raising_hand: The `email` variable could be defined using single ou doble quotes.

- Slice strings:

    ```python
    name = 'Gabriel Dornas'
    print(name[0]) # (1)!
    print(name[-1]) # (2)!
    print(name[3:]) # (3)!
    print(name[:3]) # (4)!
    print(name[1:5]) # (5)!
    print(name[:]) # (6)!
    ```

    1. :man_raising_hand: The first character is represented by **index** `0` and so on.
    2. :man_raising_hand: The last character is represented by **index** `-1` and so on.
    3. :man_raising_hand: This slices the string from **index** `3` to the end.
    4. :man_raising_hand: This slices the string, starting from the **index** `0` to, but not including, **index** (`3`). This role is to ensure that `name[:3] + name[3:]` is equal to `name`.
    5. :man_raising_hand: This slices the string, from the **index** `1` to, but not including, **index** (`5`).
    6. :man_raising_hand: This, you can guess, returns the string itself.

??? "Hello World index"

    | String  | H   | e   | l  | l  | o  |    | W  | o  | r  | l  | d  |
    |---------|-----|-----|----|----|----|----|----|----|----|----|----|
    | + index | 0   | 1   | 2  | 3  | 4  | 5  | 6  | 7  | 8  | 9  | 10 |
    | - index | -11 | -10 | -9 | -8 | -7 | -6 | -5 | -4 | -3 | -2 | -1 |

## Formatted Strings

- We don't need string concatenation all the time:

    ```python
    first_name = 'Gabriel'
    last_name = 'Dornas'
    full_name = f'{first_name} {last_name}' # (1)!
    message = f'Hello {full_name}, is everything ok with you?' # (2)!
    print(message)
    ```

    1. :man_raising_hand: The same as using string concatenation or the expression `first_name + last_name`.
    2. :man_raising_hand: Mix text and variables to create new `str`.

## String methods

- Tons of code already available to use[^1]:

    ```python
    course = 'All we need is Python!'

    # lenght
    print(len(course)) # (1)!

    # uppercase
    print(course.upper()) # (2)!

    # lowercase
    print(course.lower()) # (3)!

    # find
    print(course.find('P')) # (4)!

    # replace
    print(course.replace('Python', 'love')) # (5)!

    # in operator
    print('Python' in course) # (6)!
    ```

    1. :man_raising_hand: Could be used, for example, to restrict the number of characters in a form's input filed.
    2. :man_raising_hand: The `.upper()` method doesn't change the original `str`. Try to `print(course)` to check it.
    3. :man_raising_hand: As in the `.upper()` method, the `.lower()` doesn't change the original `str`. Try to `print(course)` to check it.
    4. :man_raising_hand: The `.find()` returns the index of the first occurrence of the searched character, in this example `P`. It is case sensitive, try to pass `p` to `.find()` to see the result.
    5. :man_raising_hand: It's case sensitive just like we saw in the `.find()` method. Try to pass `python` to `.replace()` to see the result.
    6. :man_raising_hand: This is called a boolean expression. This is case sensitive just like we saw in the `.find()` and in the `replace()` methods. Try to pass `python` to it to see the result.

??? question "Could you tell the difference between the `find()` method and the `in` operator?"

    While both `find()` and `in` help search in Python, they serve different purposes. Use `in` for a quick existence check,**returning a boolean value (True/False)**. If you specifically need the position of a substring within a string, then `find()` is the way to go, **returning the index of the first occurrence**.

[^1]: Check [other `str` built-in methods](https://www.w3schools.com/python/python_ref_string.asp) that you can use in Python.
