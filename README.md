# Pythonic Essentials
A practical introduction to Python and coding principles
# Table of contents
- [Minimal syntactic requirements](#Minimal-syntactic-requirements)
- [Functions](#functions)
- [Variables](#variables)
- [Modules and Imports](#Modules-and-imports)
- [Control flow: loops and conditionals](#Control-flow:-loops-and-conditionals)
- [Python Dictionaries and Relational Data](#Python-Dictionaries-and-Relational-Data)
- [Objects and Object Oriented Programming](#Objects-and-Object-Oriented-Programming)
- [SQlite databases](#SQlite-databases)
---
# Minimal syntactic requirements

Python executes statements one at a time, and even a single number or word counts as a valid statement. 

And like many other programming languages, Python organizes instructions into grouped sections called code blocks to determine which lines are executed together. 

## Code blocks

A **code block** is a group of lines that belong together and are executed as a single unit. Code blocks appear in functions, loops, conditionals, and other structures. **Indentation**—adding spaces or tabs at the beginning of each line—is how Python knows which lines are part of the same block. The amount of spaces or tabs must be **consistent within a block**, and these indents assist in **nesting** blocks inside other blocks.

The **top-most lines in a Python file** that are not indented are **not considered part of a code block**; they are executed directly by the Python interpreter. Only lines with indentation belong to a block.

For example:

```python
print("This runs at the top level, not part of any block.")

age = 18
if age >= 18:
    print("You are an adult.")   # indented lines form a block
    print("You can vote.")       # same block
print("This line is back at the top level.")  # not part of the block
```

You can **nest blocks inside other blocks** by adding additional levels of indentation:

```python
age = 20
has_id = True

if age >= 18:
    if has_id:                 # nested block inside outer block
        print("You can enter the club.")
    else:
        print("You need an ID.")
```

Here, the inner `if` and `else` are nested inside the outer `if` block. Python uses indentation to recognize this structure. You can use either **spaces or tabs**, but the key is to be consistent within a block. Most style guides recommend using **4 spaces per indentation level**.

## Comments

Comments in Python are optional notes in your code that help explain what the code does. They start with the `#` symbol and are completely ignored when the program runs, meaning they have no effect on the program’s behavior.

- **Single-line comments** are the most common type and appear on their own line or at the end of a code line:

```python
# This is a single-line comment explaining the next line
x = 5  # This sets x to 5
```

- **Multi-line comments** are used when you want to write longer explanations that span several lines. Python does not have a special multi-line comment symbol, but you can achieve the same effect using triple quotes (`'''` or `"""`). These are actually treated as multi-line string literals, but if they are not assigned to a variable, Python ignores them, effectively making them comments:

```python
"""
This is a multi-line comment.
It can span several lines.
Useful for explaining more complex logic
or temporarily disabling blocks of code.
"""
y = 10
```

Using comments effectively makes your code easier to read, maintain, and understand, especially for yourself or other people who might work on your code later.

## Functions

**Functions** are reusable pieces of code that perform a task; defining a function requires the keyword `def` followed by the function name and a colon. The **body of the function**, which is the code it runs, must exist even if it does nothing, and you can use the placeholder keyword `pass` for this purpose:

```python
def my_function():
    pass  # placeholder body, does nothing
```

Functions can also perform actions and return results. You can give them inputs (called arguments), have them do calculations or processing, and produce outputs that can be used elsewhere in your code. This makes your code reusable and easier to read. For example:

```python
def add_numbers(a, b):
    return a + b

result = add_numbers(3, 5)
print(result)  # prints 8
```

Repeating actions or making decisions, such as loops or conditionals, also require indentation to group the lines that should be executed together. If a block is intentionally left empty, you can use the placeholder keyword `pass` to satisfy Python’s syntax:

```python
for i in range(5):
    pass  # this loop does nothing
```

## Variables

In general computing, a **variable** is a named storage location that holds a value, such as a number, text, or other data. Variables allow programs to store, retrieve, and manipulate information dynamically, rather than working with fixed values. You can think of a variable as a labeled box where you can put data and access it whenever needed.

In Python, variables are **created automatically when you assign a value**, and the type of the variable is determined based on the value you store. Python has several basic variable types:

- **Integer (`int`)** – whole numbers
- **Floating-point (`float`)** – numbers with decimals
- **String (`str`)** – text
- **Boolean (`bool`)** – True or False values
- **List (`list`)** – ordered collection of items
- **Dictionary (`dict`)** – key-value pairs for structured data

Example:

```python
age = 25                  # int
height = 5.9              # float
name = "Alice"            # str
is_student = True         # bool
colors = ["red", "green"] # list
person = {"name": "Bob", "age": 30} # dict
```

Variables in Python do not need to be declared in advance—simply assigning a value creates the variable, and Python automatically determines its type. Any value or operation, such as adding numbers or combining words, can be used as an expression, either by itself or as part of another statement.

Python distinguishes between **local** and **global** variables.

- **Local variables** are created inside a function or a code block and exist only while that function is running. They cannot be accessed outside the function.
    

```python
def greet():
    message = "Hello!"  # local variable
    print(message)

greet()
# print(message)  # This would cause an error because message is local to the function
```

- **Global variables** are defined outside any function or block and can be accessed anywhere in the program, including inside functions. If you want to modify a global variable inside a function, you must declare it with the `global` keyword.
    

```python
counter = 0  # global variable

def increment():
    global counter  # allows modification of the global variable
    counter += 1

increment()
increment()
print(counter)  # prints 2
```

Using local and global variables appropriately helps manage data scope, avoids accidental overwriting, and keeps your code organized.

## Modules and imports

Finally, **modules and imports** are optional tools that allow Python to use extra functionality from libraries when needed. A **module** is simply a Python file that contains code, such as functions, variables, or classes, which can be reused in other programs. Python itself comes with many built-in modules, and you can also create your own modules to organize your code into separate files for clarity and reuse.

You can use the `import` keyword to access a module’s functions or variables. For example, importing the `math` module gives access to useful mathematical functions and constants:

```python
import math

radius = 5
area = math.pi * radius ** 2  # Using math.pi from the math module
root = math.sqrt(16)          # Using math.sqrt() function
print(area, root)
```

You can also create your own Python files as **custom libraries** and import them into other programs. For instance, if you have a file called `my_utils.py` with a simple function:

```python
# my_utils.py
def greet(name):
    return f"Hello, {name}!"
```

To import it in another Python file, **Python expects `my_utils.py` to be in the same directory as the file doing the import** or in a folder listed in Python’s module search path (`sys.path`):

```python
import my_utils  # Python looks for my_utils.py in the current directory

message = my_utils.greet("Alice")
print(message)
```

This approach helps keep code organized, avoids repetition, and makes it easier to manage larger projects. By breaking code into modules and optionally building your own libraries, you can reuse and share functionality across multiple programs.

# Control flow: loops and conditionals 

**Control flow** in Python determines the order in which the program’s instructions are executed. By default, Python executes code line by line from top to bottom, but sometimes you want your program to **make decisions** or **repeat actions**. This is where **conditionals** and **loops** come in.

- **Conditionals** let your program choose between different paths depending on whether a condition is true or false. The main conditional statement in Python is `if`. You can also use `elif` (short for “else if”) and `else` for additional options. Indentation is used to show which lines belong to the conditional block:

```python
age = 20

if age >= 18:
    print("You are an adult.")
elif age >= 13:
    print("You are a teenager.")
else:
    print("You are a child.")
```

In this example, Python checks the conditions in order and executes only the block of code that matches the first true condition.

- **Loops** let your program repeat a block of code multiple times. The most common loops in Python are `for` and `while`. Like conditionals, loops use indentation to define which lines are part of the loop block.

```python
# for loop example
for i in range(5):  # repeats 5 times
    print("Iteration", i)

# while loop example
count = 0
while count < 3:
    print("Counting", count)
    count += 1  # increment count to eventually stop the loop
```

- In a **for loop**, Python automatically iterates over a sequence, such as numbers or items in a list.
- In a **while loop**, Python keeps repeating the block as long as a condition remains true.

Using loops and conditionals together allows you to **control the flow of your program**, making it dynamic, interactive, and able to respond to different situations.

# Python Dictionaries and Relational Data

In Python, one of the most powerful ways to organize and access data is through **dictionaries**, which are sometimes called **hash maps** or **associative arrays** in other programming languages. A dictionary is a collection of **key-value pairs**, where each key is unique and maps to a specific value. This is similar to how data is often represented in **YAML** or other configuration files, which use nested structures to organize information.

Dictionaries are very useful for **configuration files** because you can store all of your program settings in a structured way, and then access or update them easily in your code. For example:

```python
config = {
    "app_name": "MyApp",
    "version": 1.0,
    "features": {
        "login": True,
        "chat": False
    }
}

print(config["features"]["login"])  # Accessing nested data
```

If a user chooses to store configuration in **native Python code** (for example, writing the config directly as a `.py` file), there are **security risks**. Executing or importing a config file as code can run **arbitrary commands**, which could be dangerous if the file is modified by an attacker or comes from an untrusted source.

A **safer alternative** is to use a **data-only format** such as JSON, which can be read into Python dictionaries without executing code:

```python
# config.json
{
    "app_name": "MyApp",
    "version": 1.0,
    "features": {
        "login": true,
        "chat": false
    }
}
```

```python
# Python code to safely load JSON config
import json

with open("config.json", "r") as file:
    config = json.load(file)

print(config["features"]["login"])  # Accessing nested data safely
```

Dictionaries are also helpful for representing **relational data**, which is data that describes relationships between different pieces of information. In computing, relational data often involves **rows and columns**, like a spreadsheet: each row represents an item or record, and each column represents a property of that item. For instance, a list of users could be stored as a list of dictionaries, each containing the user’s name, age, and email:

```python
users = [
    {"name": "Alice", "age": 25, "email": "alice@example.com"},
    {"name": "Bob", "age": 30, "email": "bob@example.com"}
]
```

This concept overlaps with **SQL databases** and other tabular data systems. In SQL, each table has rows and columns, much like the list-of-dictionaries structure in Python. The key difference is that SQL provides additional tools for **querying, filtering, and joining data across multiple tables**, but the underlying idea is the same: data is structured, accessible by keys or columns, and can describe relationships.

By understanding Python dictionaries and how they relate to structured, relational data, beginners gain a unified mental model that applies both to configuration files and to more advanced database concepts, making it easier to scale programs from simple scripts to complex data-driven applications, while staying mindful of security best practices when choosing how to store and load configuration.

# Objects and Object Oriented Programming

In Python, **objects** are a fundamental way to organize and work with data. An object is essentially a collection of **data** (attributes) and **functions** (methods) that operate on that data. This approach is part of **Object-Oriented Programming (OOP)**, which helps structure programs by bundling related functionality together. Python has built-in support for objects and OOP, unlike some functional programming languages where similar concepts exist but are expressed indirectly through closures, data structures, and higher-order functions.

Let’s look at our JSON Read example:

```python
import json

with open("config.json", "r") as file:
    config = json.load(file)

print(config["features"]["login"])  # Accessing nested data safely
```

Here, `config` is a **Python dictionary**, which itself is an **object**. The dictionary object contains keys (like `"features"`) and values, and provides methods for accessing and manipulating that data. When you write:

```python
print(config["features"]["login"])
```

you are using **object access notation** to retrieve nested data. In OOP terms:

- `config` is the object
- `"features"` is a key that retrieves another object (another dictionary) stored inside `config`
- `"login"` is a key of the nested dictionary
- The `[]` notation is the dictionary’s built-in **method for accessing values**, which is one way Python objects expose functionality

This demonstrates how objects allow you to **encapsulate data** and interact with it in a structured way. Even though dictionaries are simple, they behave like objects with **attributes and methods**.

Python’s OOP goes further: you can define your own classes, which are **templates for creating custom objects** with their own attributes and methods. For example:

```python
class FeatureConfig:
    def __init__(self, login_enabled, chat_enabled):
        self.login = login_enabled
        self.chat = chat_enabled

config_obj = FeatureConfig(login_enabled=True, chat_enabled=False)
print(config_obj.login)  # Accessing an attribute
```

Here:

- `FeatureConfig` is a **class** (a blueprint for objects)
- `config_obj` is an **instance** of that class
- `login` is an **attribute** storing data
- The `print(config_obj.login)` line shows how you access data on a custom object

Even in functional languages, programmers often emulate object-like structures using **records, closures, or maps**, but Python provides OOP as a **built-in feature**, making it straightforward to define and reuse objects, bundle behavior, and represent complex data in a structured, hierarchical way.

# SQlite databases

The following shows the basic workflow for **CRUD** in Python:

- **C**reate → insert rows and data
- **R**ead → query and fetch rows
- **U**pdate → modify existing rows
- **D**elete → remove rows

**1. Create (Insert Data)**

```python
import sqlite3

conn = sqlite3.connect("example.db")
cursor = conn.cursor()

# Create table
cursor.execute("""
CREATE TABLE IF NOT EXISTS users (
    id INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER
)
""")

# Insert data
cursor.execute("INSERT INTO users (name, age) VALUES (?, ?)", ("Alice", 25))
cursor.execute("INSERT INTO users (name, age) VALUES (?, ?)", ("Bob", 30))
conn.commit()
```

---

**2. Read (Query Data)**

```python
# Retrieve all users
cursor.execute("SELECT * FROM users")
users = cursor.fetchall()
for user in users:
    print(user)

# Retrieve specific users
cursor.execute("SELECT * FROM users WHERE age > ?", (26,))
print(cursor.fetchall())
```

---

**3. Update (Modify Data)**

```python
# Update Alice's age
cursor.execute("UPDATE users SET age = ? WHERE name = ?", (26, "Alice"))
conn.commit()
```

---

**4. Delete (Remove Data)**

```python
# Delete Bob from the table
cursor.execute("DELETE FROM users WHERE name = ?", ("Bob",))
conn.commit()
```

---

**5. Close Connection**

```python
conn.close()
```
