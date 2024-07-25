---
date: 2024-07-15
draft: False
authors: [gabrielbdornas]
comments: true
categories:
  - Python
  - Python course
---

# Python 18 Horas - W3schools #1

Join us on an immersive journey through the universe of Python programming! In the Python 18Hours Meetings, guided by the comprehensive materials from [W3Schools](https://www.w3schools.com/python/default.asp), we will uncover the secrets of this powerful and versatile language, exploring its fundamentals and functionalities step by step.

<!-- more -->

![type:video](https://www.youtube.com/embed/duci2JOnFbw)

## What was covered

* **Introduction to Python:**

    * Popularity and diverse applications (web, data analysis, automation, etc.).
    * Ease of learning and intuitive syntax.
    * Large and active community for support.

* **Installation and basic usage:**

    * It is recommended to use a virtual environment to isolate projects.

    ```python
    # create python virtual environment
    python -m venv venv

    # activate virtual environment on linux/mac
    source venv/bin/activate

    # activate virtual environment on windows
    source venv/Scripts/activate
    ```

    * Running scripts through the interpreter and `.py` files.

* **Syntax and indentation:**

    * The importance of indentation for code organization and readability.

    ```python
    if 5 > 2:
      print('Five is greater than 2!')
    ```

    * Indentation errors and how to identify them in the editor and interpreter.
    * Best practices for code formatting with tabs (4 spaces).

* **Variables:**

    * Concept and creation through value assignment.

    ```python
    name = "John Doe" # str
    age = 30 # int
    value = 4.56 # float
    city = "Belo Horizonte" # str
    correct = True # bool
    ```

    * Storing data for later use in the code.
    * Differences between variables and literal values.
    * Absence of formal variable type declaration in Python.

* **Comments:**

    * Using hashtags (#) for comments and code documentation.

    ```python
    # this is a comment
    if 5 > 2: # this is also a comment
      print('Five is greater than 2!')

    def sum(a, b):
      """
      This is a comment to indicate that
      this function sums two numbers, a and b
      """
      return a + b

    print(sum(2, 2))

    # multi-line comment
    # print(sum(2, 3))
    # print(sum(2, 4))
    # print(sum(2, 5))
    ```

    * Disabling parts of the code for testing and debugging.
    * Shortcuts to comment and uncomment lines and blocks in the text editor.

## Extra Tips

* Configure the text editor to comment lines and blocks of code easily.
* Configure the text editor to automatically save the worked file (auto-save).
* Use the virtual environment for each project to isolate libraries and avoid conflicts.
* This summary was prepared based on the meeting transcript and may contain adaptations for better clarity and conciseness. I recommend watching the recording for a deeper understanding of the topics covered.

## Exercises

??? question "Define variables for a new hospital management program"

    - A new patient named João was admitted to the hospital. He is 20 years old and is a new patient at this hospital. Define variables to store this patient's name, age, and whether he is a new patient at the institution. Display all this collected information in the system.

    ??? "Before looking at the answer, try to do it yourself."

        ```python
        name = 'João'
        age = 20
        new_patient = True
        print(name, age, new_patient) # (1)!
        ```

        1. :man_raising_hand: You can pass more than one value to the `print()` function.

## Referências

- [W3schools Python HOME](https://www.w3schools.com/python/default.asp).
- [W3schools Python Intro](https://www.w3schools.com/python/python_intro.asp).
- [W3schools Python Get Started](https://www.w3schools.com/python/python_getstarted.asp).
- [W3schools Python Syntax](https://www.w3schools.com/python/python_syntax.asp).
- [W3schools Python Comments](https://www.w3schools.com/python/python_comments.asp).
- [Python documentation - Whetting Your Appetite](https://docs.python.org/3/tutorial/appetite.html).
- [Python documentation - Using the Python Interpreter](https://docs.python.org/3/tutorial/interpreter.html).
- [Python documentation - An Informal Introduction to Python](https://docs.python.org/3/tutorial/introduction.html).
