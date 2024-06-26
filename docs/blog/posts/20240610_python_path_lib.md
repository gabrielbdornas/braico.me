---
date: 2024-06-10
draft: false
authors: [gabrielbdornas]
comments: true
categories:
  - Python
  - Python’s standard library
---

# Python pathlib

Working with files and interacting with the file system are common tasks for Python developers.
That’s where pathlib comes in.
Let's understand how it works with the help of the [Python's pathlib Module: Taming the File System](https://realpython.com/python-pathlib/) post.

<!-- more -->

- The pathlib module is part of Python’s standard library.

- The pathlib’s Path class works the same way on different operating systems.

- One motivation behind pathlib is to represent the file system with dedicated objects instead of strings[^1].

- Traditionally, Python has represented file paths using regular strings. However, paths are more than plain strings.

- As an initial example of pathlib usage, the following code block moves files into a subfolder:

    ```Python
    from pathlib import Path # (1)!

    for file_path in Path.cwd().glob("*.txt"):
        new_path = Path("archive") / file_path.name # (2)!
        file_path.replace(new_path)
    ```

    1. :man_raising_hand: Because you’ll mainly be working with the Path class of pathlib, importing it as `from pathlib import Path` saves you a few keystrokes in your code. This way, you can work with Path directly, rather than importing pathlib as a module and referring to `pathlib.Path`.

    2. :man_raising_hand: The archive's folder must exists to ensure `.replace()` method works.

## Using Path Methods

<div class="annotate" markdown>

- Once you’ve imported Path, you can make use of existing methods to get the **current working directory** (`cwd`) (1), or your user’s **home directory**.

- To get your current working directory, you can use `.cwd()`:

</div>

1. :man_raising_hand: The **current working directory** is the directory in the file system that the current process is operating in. Using the home directory as a starting point, you can specify paths that’ll **work on different machines, independent of any specific usernames**.

=== "Linux"

    ```python
    >>> from pathlib import Path
    >>> Path.cwd() # (1)!
    PosixPath('/home/gabrielbdornas/Desktop/codei')
    ```

    1. :man_raising_hand: With `Path.cwd() `and `Path.home()`, you can conveniently get a starting point for your Python scripts. In cases where you need to spell paths out or reference a subdirectory structure, you can instantiate Path with a string.

=== "macOS"

    ```python
    >>> from pathlib import Path
    >>> Path.cwd() # (1)!
    PosixPath('/Users/gabrielbdornas/Desktop/codei')
    ```

    1. :man_raising_hand: With `Path.cwd() `and `Path.home()`, you can conveniently get a starting point for your Python scripts. In cases where you need to spell paths out or reference a subdirectory structure, you can instantiate Path with a string.

=== "Windows"

    ```python
    >>> from pathlib import Path
    >>> Path.cwd() # (1)!
    WindowsPath('C:/Users/gabrielbdornas/Desktop/codei')
    ```

    1. :man_raising_hand: With `Path.cwd() `and `Path.home()`, you can conveniently get a starting point for your Python scripts. In cases where you need to spell paths out or reference a subdirectory structure, you can instantiate Path with a string.

- To get your home directory, you can use `.home()`:

```python
>>> from pathlib import Path
>>> Path.home() # (1)!
PosixPath('/home/gabrielbdornas/')
```

1. :man_raising_hand: Using the home directory as a starting point, you can specify paths that’ll work independent of any specific usernames.

## Passing in a String

- Instead of starting in your user’s home directory or your current working directory, you can point to a directory or file directly by passing its string representation into Path:

=== "Linux"

    ```python
    >>> from pathlib import Path
    >>> Path("/home/gabrielbdornas/Desktop/codei/file.txt")
    PosixPath('/home/gabrielbdornas/Desktop/codei/file.txt')
    ```

=== "Windows"

    ```python
    >>> from pathlib import Path
    >>> Path(r"C:\Users\gabrielbdornas\codei\file.txt")
    WindowsPath('C:/Users/gabrielbdornas/Desktop/codei/file.txt') # (1)!
    ```

    1. :man_raising_hand: On Windows, the **path separator** is a backslash (\). However, in many contexts, the backslash is also used as an escape character to represent non-printable characters. To avoid problems, use raw string literals to represent Windows paths like `r"C:\Users"`.

??? Note "The `__file__` attribute"

    An idiomatic way of working with the current module’s location as the path is using `__file__`:


    ```python
    # hello.py

    from pathlib import Path

    print(f"You can find me here: {Path(__file__).parent}!") # (1)!
    ```

    1. :man_raising_hand: The `__file__` attribute contains the path to the file that Python is currently importing or executing. You can pass in `__file__` to Path when you need to work with the path to the module itself. For example, maybe you want to get the parent directory with `.parent`.

## Joining Paths

- A third way to construct a path is to join the parts of the path using the special forward slash operator (`/`):

```python
from pathlib import Path

for file_path in Path.cwd().glob("*.txt"):
    new_path = Path("archive") / file_path.name # (1)!
    file_path.rename(new_path)
```

1. :man_raising_hand: The forward slash operator can join several paths or a mix of paths and strings as long as you include one Path object. **You use a forward slash regardless of your platform’s actual path separator**.

??? Note "The `.joinpath()` method"

    - If you don’t like the special slash notation, then you can do the same operation with the `.joinpath()` method:

    ```python
    >>> from pathlib import Path
    >>> Path.home().joinpath("python", "scripts", "test.py")
    PosixPath('/home/gabrielbdornas/python/scripts/test.py')
    ```

## File System Operations With Paths

- A file or directory path consists of different parts. When you use pathlib, these parts are conveniently available as properties. Basic examples include:

    - `.name`: The filename without any directory
    - `.stem`: The filename without the file extension
    - `.suffix`: The file extension
    - `.anchor`: The part of the path before the directories
    - `.parent`: The directory containing the file, or the parent directory if the path is a directory

    ```python
    >>> from pathlib import Path
    >>> path = Path(__file__)
    >>> path
    PosixPath("/home/gabrielbdornas/codei/test.md")

    >>> path.name
    'test.md'

    >>> path.stem
    'test'

    >>> path.suffix
    '.md'

    >>> path.anchor
    '/'

    >>> path.parent # (1)!
    PosixPath("/home/gabrielbdornas/codei")

    >>> path.parent.parent
    PosixPath('/home/gabrielbdornas')
    ```

    1. :man_raising_hand: Note that `.parent` returns a new Path object, whereas the other properties return strings. This means, for instance, that you can chain `.parent` in the last example or even combine it with the slash operator to create completely new paths.

## Reading and Writing Files

- Consider that you want to print all the items on a shopping list that you wrote down in a Markdown file. The content of shopping_list.md looks like this:

```markdown
<!-- shopping_list.md -->

# Shopping List

## Fruit

* Banana
* Apple
* Peach

## Candy

* Chocolate
* Nougat Bits
```

- With pathlib, you can use `open()` directly on Path objects.

- A first draft of your script that finds all the items in `shopping_list.md` and prints them may look like this:

    ```python
    # read_shopping_list.py

    from pathlib import Path

    path = Path.cwd() / "shopping_list.md"
    with path.open(mode="r", encoding="utf-8") as md_file: # (1)!
        content = md_file.read()
        groceries = [line for line in content.splitlines() if line.startswith("*")]
    print("\n".join(groceries))
    ```

    1. :man_raising_hand: In fact, `Path.open()` is calling the built-in `open()` function behind the scenes. That’s why you can use parameters like mode and encoding with `Path.open()`.


- On top of that, pathlib offers some convenient methods to read and write files:
    - `.read_text()` opens the path in text mode and returns the contents as a string.
    - `.read_bytes()` opens the path in binary mode and returns the contents as a byte string.
    - `.write_text()` opens the path and writes string data to it[^2][^3].
    - `.write_bytes()` opens the path in binary mode and writes data to it[^2][^3].

- Therefore, you can update `read_shopping_list.py` using `.read_text()`:

    ```python
    # read_shopping_list.py

    from pathlib import Path

    path = Path.cwd() / "shopping_list.md" # (1)!
    content = path.read_text(encoding="utf-8")
    groceries = [line for line in content.splitlines() if line.startswith("*")]
    print("\n".join(groceries))
    ```

    1. :man_raising_hand: You can also specify paths directly as in `Path("shopping_list.md")`, **in which case they’re interpreted relative to the current working directory**.

- If you want to create a plain shopping list that only contains the groceries, then you can use `.write_text()` in a similar fashion:

    ```python
    # write_plain_shoppinglist.py

    from pathlib import Path

    content = Path("shopping_list.md").read_text(encoding="utf-8")
    groceries = [line for line in content.splitlines() if line.startswith("*")]

    Path("plain_list.md").write_text("\n".join(groceries), encoding="utf-8")
    ```

## Renaming Files

- When you want to rename files, you can use `.with_stem()`, `.with_suffix()`, or `.with_name()`. They return the original path but with the filename, the file extension, or both replaced. You can use all of them in combination with `.replace()`, example:

    ```python
    >>> from pathlib import Path
    >>> txt_path = Path('/home/gabrielbdornas/codei/hello.txt')
    >>> txt_path
    PosixPath('/home/gabrielbdornas/codei/hello.txt')

    >>> md_path = txt_path.with_suffix('.md') # (1)!
    PosixPath('/home/gabrielbdornas/codei/hello.md')

    >>> txt_path.replace(md_path) # (2)!
    ```

    1. :man_raising_hand: Using `.with_suffix()` returns a new path.

    2. :man_raising_hand: To actually rename the file, you use `.replace()`. This moves `txt_path` to `md_path` and renames it when saving.

- If you want to change the complete filename, including the extension, then you can use `.with_name()`:

    ```python
    >>> from pathlib import Path
    >>> txt_path = Path('/home/gabrielbdornas/codei/hello.txt')
    >>> txt_path
    PosixPath('/home/gabrielbdornas/codei/hello.txt')

    >>> md_path = txt_path.with_name('goodbye.md')
    PosixPath('/home/gabrielbdornas/codei/goodbye.md')

    >>> txt_path.replace(md_path) # (1)!
    ```

    1. :man_raising_hand: It renames `hello.txt` to `goodbye.md`.


## Copying Files

- Surprisingly, Path doesn’t have a method to copy files. But with the knowledge that you’ve gained about pathlib so far, you can create the same functionality with a few lines of code:

    ```python
    >>> from pathlib import Path
    >>> source = Path('shopping_list.md')
    >>> destination = source.with_stem('shopping_list_02') # (1)!
    >>> destination.write_bytes(source.read_bytes()) # (2)!
    ```

    1. :man_raising_hand: You’re using `.with_stem()` to create the new filename without changing the extension.
    2. :man_raising_hand: The actual copying takes place here, where you use `.read_bytes()` to read the content of source and then write this content to destination using `.write_bytes()`.

## Moving and Deleting Files

- Through pathlib, you also have access to basic file system–level operations like moving, updating, and even deleting files. For the most part, these methods don’t give a warning or wait for confirmation before getting rid of information or files. So, be careful when using these methods[^3].

- To move a file, you can use `.replace()`[^2]. To avoid possibly overwriting the destination path, you can test whether the destination exists before replacing:

    ```python
    from pathlib import Path
    source = Path('hello.py')
    destination = Path('goodbye.py')

    if not destination.exists():
      source.replace(destination)
    ```

- However, this does leave the door open for a possible [race condition](https://en.wikipedia.org/wiki/Race_condition). Another process may add a file at the destination path between the execution of the if statement and the `.replace()` method. If that’s a concern, then a safer way is to open the destination path for exclusive creation then explicitly copy the source data and delete the source file afterward:

    ```python
    from pathlib import Path

    source = Path('hello.py')
    destination = Path('goodbye.py')

    try:
      with destination.open(mode='xb') as file:
        file.write(source.read_bytes())
    except FileExistsError:
        print(f'File {destination} existis already') # (1)!
    else:
        source.unlink() # (2)!
    ```

    1. :man_raising_hand: If destination already exists, it catches a `FileExistsError` and prints a warning message.

    2. :man_raising_hand: To perform a move, you need to delete source with `.unlink()` after the copy is done. Using `else` ensures that the source file isn’t deleted if the copying fails.

## Creating Empty Files

- To create an empty file with pathlib, you can use `.touch()`. This method is intended to update a file’s modification time, but you can use its side effect to create a new file:

    ```python
    >>> from pathlib import Path
    >>> filename = Path('hello.py')
    >>> filename.exists()
    False

    >>> filename.touch()
    >>> filename.exists() # (1)!
    True

    >>> filename.touch() # (2)!
    ```

    1. :man_raising_hand: You use `.exists()` both to verify that the file didn’t exist before and then to check that it was successfully created.

    2. :man_raising_hand: If you use `.touch()` again, then it updates the file’s modification time. If you don’t want to modify files accidentally, then you can use the `exist_ok` parameter and set it to False as in `filename.touch(exist_ok=False)`.

## Python pathlib Examples

### Counting Files

- With pathlib, you can conveniently use the `.iterdir()` method, which iterates over all the files in the given directory:

    ```python
    >>> from pathlib import Path
    >>> from collections import Counter
    >>> counter(path.suffix for path in Path.cwd().iterdir()) # (1)!
    Counter({'.md': 2, '.txt': 4, '.pdf': 2, '.py': 1})
    ```

    1. :man_raising_hand: You can create more flexible file listings with the methods `.glob()` and `.rglob()`. For example, `Path.cwd().glob("*.txt")` returns all the files with a `.txt` suffix in the current directory. If you want to recursively find all the files in both the directory and its subdirectories, then you can use `.rglob()`.

### Displaying a Directory Tree

- In this example, you define a function named `tree()`, which will print a visual tree representing the file hierarchy, rooted at a given directory. This is useful when, for example, you want to peek into the subdirectories of a project.

```python
# display_dir_tree.py

def tree(directory):
    print(f"+ {directory}")
    for path in sorted(directory.rglob("*")):
        depth = len(path.relative_to(directory).parts) # (1)!
        spacer = "    " * depth
        print(f"{spacer}+ {path.name}")
```

1. :man_raising_hand: Note that you need to know how far away from the root directory a file is located. To do this, you first use `.relative_to()` to represent a path relative to the root directory. Then, you use the `.parts` property to count the number of directories in the representation.

- When run, this function creates a visual tree like the following:

```python
>>> from pathlib import Path
>>> from display_dir_tree import tree
>>> tree(Path.cwd())
+ /home/gabrielbdornas/codei
    + directory_1
        + file_a.md
    + directory_2
        + file_a.md
        + file_b.pdf
        + file_c.py
    + file_1.txt
    + file_2.txt
```

### Finding the Most Recently Modified File

- The `.iterdir()`, `.glob()`, and `.rglob()` methods are great fits for generator expressions and list comprehensions.To find the most recently modified file in a directory, you can use the `.stat()` method to get information about the underlying files. For instance, `.stat().st_mtime` gives the time of last modification of a file:

```python
>>> from pathlib import Path
>>> from datetime import datetime
>>> directory = Path.cwd()
>>> time, file_path = max((f.stat().st_mtime, f) for f in directory.iterdir())
>>> print (datetime.fromtimestamp(time), file_path)
2024-06-18 11:23:56.977817 /home/gabrielbdornas/codei/test001.txt
```

### Creating a Unique Filename

- In the last example, you’ll construct a unique numbered filename based on a template string. This can be handy when you don’t want to overwrite an existing file if it already exists:

```python
# unique_path.py

def unique_path(directory, name_pattern): # (1)!
  counter = 0
  while True:
    counter += 1
    path = directory / name_pattern.format(counter)
    if not path.exists():
      return path
```

1. :man_raising_hand: In `unique_path()`, you specify a pattern for the filename, with room for a counter. Then, you check the existence of the file path created by joining a directory and the filename, including a value for the counter. If it already exists, then you increase the counter and try again.

- Now you can use the script above to get unique filenames:

```python
>>> from pathlib import Path
>>> from unique_path import unique_path
>>> template = "test{:03d}.txt"
>>> unique_path(Path.cwd(), template)
PosixPath("/home/gabrielbdornas/codei/test003.txt") # (1)!
```

1. :man_raising_hand: If the directory already contains the files `test001.txt` and `test002.txt`, then the above code will set path to `test003.txt`.

## Conclusion

- Python’s pathlib module provides a modern and Pythonic way of working with file paths, making code more readable and maintainable. With pathlib, you can represent file paths with dedicated Path objects instead of plain strings[^1].

- The pathlib module makes dealing with file paths convenient by providing helpful methods and properties. Peculiarities of the different systems are hidden by the Path object, which makes your code more consistent across operating systems.

[^1]: In general, you should try to use Path objects as much as possible in your code to take advantage of their benefits, but converting them to strings can be necessary in certain contexts. **Some libraries and APIs still expect you to pass file paths as strings, so you may need to convert a Path object to a string before passing it to certain functions**. You'll see that, on Windows, although you enter paths with backslashes, pathlib represents them with the forward slash (/) as the path separator. This representation is named POSIX style. POSIX stands for [Portable Operating System Interface](https://en.wikipedia.org/wiki/POSIX), which is a standard for maintaining the compability between operating systems.

[^2]: When using these methods, Python overwrites any existing files on the same path without giving you any notice. **That means you could erase all your hard work with a single keystroke**! As always, when you write files with Python, you should be cautious of what your code is doing. The same is true when you’re renaming files.
[^3]: A good way to protect yoursef of this kind of troble is using version control system while writing your codes.
