---
date: 2024-06-26
draft: True
authors: [gabrielbdornas]
comments: true
categories:
  - Python
  - Python course
---

# Python course - Class 1

Have you ever wanted to unlock the power of Python?
This versatile language is used by data scientists, web developers, and even hobbyists to automate tasks, analyze information, and build incredible applications.

<!-- more -->

This content is designed to take you from absolute beginner to Python pro, guiding you step-by-step through the fundamentals and helping you put your newfound skills to the test with exciting projects.
Get ready to join the thriving Python community, let's get started!


## Installations

- If you are using Linux or Mac, it may be installed. Open your terminal and run `python --version`.
- If you are on Windows, download it from the [Python downloads page](https://www.python.org/downloads/).
- Download a text editor as [VS code](https://code.visualstudio.com/download) or [sublime text](https://www.sublimetext.com/3)
- If you are on Window, download [git for windows](https://git-scm.com/download/win) as we'll need a terminal to run our programs.

## Your first Python program

- Here is your first Python program:

    ```python
    print("Gabriel Braico Dornas") # (1)!
    ```

    1. :man_raising_hand: Run it using the [Python interpreter](https://docs.python.org/3/tutorial/interpreter.html) and/or `app.py` file.

- The program is executed line by line.

    ```python
    print('o----') # (1)!
    print(' ||||')
    ```

    1. :man_raising_hand: Here, `o----` is a string (`str`) or a series of characters.


- String multiplication:

    ```python
    print('#' * 10) # (1)!
    ```

    1. :man_raising_hand: The `'#' * 10` is an expression, or a piece of code, that produces a value. Python first evaluates the `'#' * 10` code, and then it prints its result (`##########`).

??? question "What other shapes could we draw using string multiplication?"

    - Left-sided pyramid [^1]:

    ```python
    print('*')
    print('*' * 2)
    print('*' * 3)
    print('*' * 4)
    print('*' * 5)
    print('*' * 6)
    print('*' * 7)
    print('*' * 8)
    print('*' * 9)
    ```

    - Upside-down pyramid [^1]:

    ```python
    print('*' * 9)
    print('*' * 8)
    print('*' * 7)
    print('*' * 6)
    print('*' * 5)
    print('*' * 4)
    print('*' * 3)
    print('*' * 2)
    print('*')
    ```

    ```python
    # Your turn!!! (1)
    ```

    1. :man_raising_hand: Comments in Python are created with the `#` character. Everything after the `#` character won't be executed by the Python interpreter.

## Variables

- Variables temporarily stores data in a computer's memory:

    ```python
    price = 10  # (1)!
    print(price) # (2)!
    ```

    1. :man_raising_hand: Identifier (variable's name) + equal sign + variable's value.
    2. :man_raising_hand: Do not add quotations here.

- Update the variable's value:

    - Numbers variables:

        ```python
        price = 10 # (1)!
        price = 20
        print(price)
        rating = 4.6 # (2)!
        rating = 7.9
        print(rating) # (3)!
        ```

        1. :man_raising_hand: Here, `10` is an integer (`int`) or a whole number without a decimal point.
        2. :man_raising_hand: Here, `4.6`  is a float (`float`) or a number with a decimal point.
        3. :man_raising_hand: Remember that the program is executed line by line.

    - String and boolean variables:

        ```python
        name = 'Gabriel Braico Dornas'
        name = 'Gabriel'
        print(name)
        is_approved = True # (1)!
        is_approved = False
        print(is_approved)
        ```

        1. :man_raising_hand: Here, `is_approved` is a boolean or, as we say yes (`True`) and no (`False`). **Note that python is a case-sensitive language**.

    - Mix them:

        ```python
        my_variable = 2 # (1)!
        my_variable = 2.5 # (2)!
        my_variable = 'Gabriel Braico Dornas' # (3)!
        my_variable = False # (4)!
        print(my_variable) # (5)!
        ```

        1. :man_raising_hand: If `print(my_variable)` is added after here, it'll print the value `2`.
        2. :man_raising_hand: If `print(my_variable)` is added after here, it'll print the value `2.5`.
        3. :man_raising_hand: If `print(my_variable)` is added after here, it'll print the value `Gabriel Braico Dornas`.
        4. :man_raising_hand: As `print(my_variable)` was added after here, it'll print the value `False`.
        5. :man_raising_hand: Remember that the program is executed line by line.

??? question "Define variables to our new hospital program"

    - We checked in a patient named John Smith. He's 20 years old and is a new patient. Define a variable to store the patient name, age and whether it is a new patient or not.

    ??? "Give it a try before see my solution."

        ```python
        name = 'John Smith'
        age = 20
        is_new_patient = True
        print(name, age, is_new_patient) # (1)!
        ```

        1. :man_raising_hand: You can pass more them one value to be printed with the `print()` function.

## Receiving input

- Ask the user's name:

    ```python
    input('What is your name? ') # (1)!
    ```

    1. :man_raising_hand: Both the `print()` and the `input()` are functions built into Python. Think of functions as the buttons on the remote control of your TV. The control's buttons are just like functions/operations that you can use over and over again. Function's parenthesis indicates that we are **calling** that function, or pressing a button on a remote control.

- Printing a nice message to our user:

    ```python
    name = input('What is your name? ') # (1)!
    print('Hi ' + name) # (2)!
    ```

    1. :man_raising_hand: Pay attention to the space after the question mark.
    2. :man_raising_hand: Another example of an expression, or a piece of code that produces a value.

??? question "What is your user's favorite color?"

    - As two questions to your user: His/her name and his/her favorite color. Then print a message like "Gabriel likes green!".

    ??? "Give it a try before see my solution."

        ```python
        name = input('What is your name? ')
        color = input('What is your favorite color? ')
        print(name + ' likes ' + color) # (1)!
        ```

        1. :man_raising_hand: As you can see, `print(name, 'likes', color)` will work as well. Type `help(print)` in [Python interpreter](https://docs.python.org/3/tutorial/interpreter.html) to understand why we don't need to use spaces in the "likes" `string` with this approach.

## Type conversion

- Calculate the user's age:

    ```python
    birth_year = input('Birth year: ')
    age = 2024 - birth_year
    print(age) # (1)!
    ```

    1. :man_raising_hand: Be never afraid to error messages. They tend to be really useful. Just read it. Then, try to figure it out what's going on.

- Refactoring the code to fix the error:

    ```python
    birth_year = input('Birth year: ') # (1)!
    print(type(birth_year)) # (2)!
    birth_year = int(birth_year) # (3)!
    print(type(birth_year)) # (4)!
    age = 2024 - birth_year # (5)!
    print(age)
    ```

    1. :man_raising_hand: The `input()` functions always returns a `str`, even if the user types a number.

    2. :man_raising_hand: The `type()` function confirms that the type of the variable `birth_year` is `str`, which means that the expression `2024 - birth_year` was evaluated as `2024 - '1985'` in the last example.

    3. :man_raising_hand: The `int()` function converts the variable from `str` to `int`. The `float()`, `bool()` and `str()` functions are examples of other conversion type functions. Try them out!

    4. :man_raising_hand: The `type()` function confirms that the type of the variable `birth_year`, now, is `int`.

    5. :man_raising_hand: The expression `2024 - birth_year`, now, will be evaluated as `2024 - 1985`.

??? question "What is your user's weight in kilograms?"

    - Ask the user their weight in pounds, convert it to kilograms and print on the terminal.

    ??? "Give it a try before see my solution."

        ```python
        weight_lbs = int(input('What your weight in pounds? ')) # (1)!
        weight_kg = weight_lbs * 0.45  # (2)!
        print(weight_kg) # (3)!
        ```

        1. :man_raising_hand: As you can see, `int(input())` will work as well. First, the Python interpreter will evaluate the expression inside the `input()`, then convert it to `int` using the `int()` function.

        2. :man_raising_hand: The `0.45` number is an example of the `float` data type, or a number with a decimal point.

        2. :man_raising_hand: What if we use the `print('Your weight in kilograms is ' + weight_kg)` expression?

[^1]: Idea from the [Creating Patterns in Python Medium post](https://mardiyyah.medium.com/creating-patterns-in-python-learnpythonthroughprojects-series-7-3e78db1b3a04).
