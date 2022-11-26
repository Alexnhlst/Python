<h1>A Gentle Introduction to Python</h1>

> "Give a man a fish and you feed him for a day. Teach a man to fish and you feed him for a lifetime." - Chinese proverb

Computer programming, or coding, is telling a computer to do something using a language it understands. Coding is not just putting together some instructions that work. Good code is short, fast, elegant, easy to read and understand, simple, easy to modify and extend, easy to scale and refactor, and easy to test.

- [A proper introduction](#a-proper-introduction)
- [Enter the Python](#enter-the-python)
  - [Portability](#portability)
  - [Coherence](#coherence)
  - [Developer productivity](#developer-productivity)
  - [An extensive library](#an-extensive-library)
  - [Software quality](#software-quality)
  - [Software integration](#software-integration)
  - [What are the drawbacks?](#what-are-the-drawbacks)
- [Setting up the environment](#setting-up-the-environment)
  - [Python 2 versus Python 3](#python-2-versus-python-3)
  - [Installing Python](#installing-python)
  - [About virtual environments](#about-virtual-environments)
    - [Your first virtual environment](#your-first-virtual-environment)
  - [Installing third-party libraries](#installing-third-party-libraries)
  - [Your friend, the console](#your-friend-the-console)
- [How to run a Python program](#how-to-run-a-python-program)
  - [Running Python scripts](#running-python-scripts)
  - [Running the Python interactive shell](#running-the-python-interactive-shell)
  - [Running Python as a service](#running-python-as-a-service)
  - [Running Python as a GUI application](#running-python-as-a-gui-application)
- [How is Python code organized?](#how-is-python-code-organized)
  - [How do we use modules and packages?](#how-do-we-use-modules-and-packages)
- [Python's execution model](#pythons-execution-model)
  - [Names and namespaces](#names-and-namespaces)
  - [Scopes](#scopes)
- [Objects and classes](#objects-and-classes)
- [Guidelines for writing good code](#guidelines-for-writing-good-code)
  - [Python culture](#python-culture)

## A proper introduction

When we write code, we are instructing a computer about the things it has to do. Where does the action happen? In many places: the computer memory, hard drives, network cables, the CPU, and so on. If you write a piece of software that allows people to buy clothes online, you will have to represent real people, real clothes, real brands, sizes, and so on and so forth, within the boundaries of a program. In order to do so, you will need to create and handle objects in the program being written. The two main features any object has are **properties** and **methods**. Typically, in a computer program, you'll represent people as customers or employees. The properties that you store against them are things like a name, a Social Security number, an age, whether they have a driving license, an email, gender, and so on. In a computer program, you store all the data needed in order to use an object for the purpose that needs to be served. Properties are characteristics of an object. Methods are things that an object can do. As a person, I have methods such as speak, walk, sleep, wake up, eat, dream, write, read, and so on. All the things that I can do could be seen as methods of the objects that represent me. Coding, in fact, is simply about managing those objects that live in the subset of the world that we're reproducing in our software. You can create, use, reuse, and delete objects as you please. According to the Data Model chapter on the [official Python documentation](https://docs.python.org/3/reference/datamodel.html):

> "Objects are Python's abstraction for data. All data in a Python program is represented by objects or by relations between objects."

Every object in Python has an **ID** (or identity), a **type**, and a **value**. Once created, the ID of an object is never changed. It's a unique identifier for it, and it's used behind the scenes by Python to retrieve the object when we want to use it. The type also never changes. The type states what operations are supported by the object and the possible values that can be assigned to it. The value can be changed or not: if it can, the object is said to be **mutable**; otherwise, it is said to be **immutable**. When you give an object a name, then you can use the name to retrieve the object and use it. In a more generic sense, objects, such as numbers, strings (text), and collections, are associated with a name.

---

## Enter the Python

Python is the marvelous creation of Guido Van Rossum, a Dutch computer scientist and mathematician who decided to gift the world with a project he was playing around with over Christmas 1989. The language appeared to the public somewhere around 1991, and since then has evolved to be one of the leading programming languages used worldwide today.

### Portability

Python runs everywhere, and porting a program from Linux to Windows or Mac is usually just a matter of fixing paths and settings. Python is designed for portability and it takes care of specific operating system (OS) quirks behind interfaces that shield you from the pain of having to write code tailored to a specific platform.

### Coherence

Python is extremely logical and coherent. You can see it was designed by a brilliant computer scientist. Most of the time you can just guess how a method is called if you don't know it.

### Developer productivity

A Python program is typically one-fifth to one-third the size of equivalent Java or C++ code. This means the job gets done faster. Another important aspect is that Python runs without the need for lengthy and time-consuming compilation and linkage steps, so there is no need to wait to see the results of your work.

### An extensive library

Python has an incredibly extensive standard library (it is said to come with batteries included). If that wasn't enough, the Python international community maintains a body of third-party libraries, tailored to specific needs, which you can access freely at the **Python Package Index (PyPI)**.

### Software quality

Python is heavily focused on readability, coherence, and quality. The language's uniformity allows for high readability, and this is crucial nowadays, as coding is more of a collective effort than a solo endeavor. Another important aspect of Python is its intrinsic multiparadigm nature. You can use it as a scripting language, but you can also exploit object-oriented, imperative, and functional programming styles—it is extremely versatile.

### Software integration

Another important aspect is that Python can be extended and integrated with many other languages.

### What are the drawbacks?

Probably, the only drawback that one could find in Python, which is not due to personal preferences, is its execution speed. Typically, Python is slower than its compiled siblings. The standard implementation of Python produces, when you run an application, a compiled version of the source code called byte code (with the extension .pyc), which is then run by the Python interpreter. The advantage of this approach is portability, which we pay for with increased runtimes due to the fact that Python is not compiled down to the machine level, as other languages are. Despite this, Python speed is rarely a problem today, hence its wide use regardless of this aspect. What happens is that, in real life, hardware cost is no longer a problem, and usually it's easy enough to gain speed by parallelizing tasks. Moreover, many programs spend a great proportion of the time waiting for I/O operations to complete; therefore, the raw execution speed is often a secondary factor to the overall performance. In situations where speed really is crucial, one can switch to faster Python implementations, such as [PyPy](https://www.pypy.org/), which provides, on average, just over a four-fold speedup by implementing advanced compilation techniques. It is also possible to write performance-critical parts of your code in faster languages, such as C or C++, and integrate that with your Python code. Libraries such as **pandas** and **NumPy** (which are commonly used for doing data science in Python) use such techniques.

---

## Setting up the environment

### Python 2 versus Python 3

In the real world, Python 2 is now only running legacy software. Python 3 has been out since 2008, and the lengthy transition phase from Version 2 has mostly come to an end. Python 2 was widely used in the industry, and it took a long time and sometimes a huge effort to make the transition. Some Python 2 software will never be updated to Python 3, simply because the cost and effort involved is not considered worth it. Some companies, therefore, prefer to keep their old legacy systems running just as they are, rather than updating them just for the sake of it. During the transition phase, many libraries were rewritten to be compatible with both versions, mostly harnessing the power of the six library (the name comes from the multiplication 2 x 3, due to the porting from Version 2 to 3), which helps you to introspect and adapt the behavior according to the version used. Now that Python 2 has reached its **end of life (EOL)**, some libraries have started to reverse that trend and are dropping support for Python 2.

### Installing Python

First of all, let's talk about your OS. Python is fully integrated and, most likely, already installed in almost every Linux distribution. If you have a Mac, it's likely that Python is already there as well (although possibly only Python 2.7); if you're using Windows, however, you probably need to install it. Getting Python and the libraries you need up and running requires a bit of handiwork. Linux and macOS seem to be the most user-friendly for Python programmers; Windows, on the other hand, may require a bit more effort. The place you want to start is the official [Python website](https://www.python.org). This website hosts the official Python documentation and many other resources that you will find very useful. Now that Python is installed on your system, the objective is to be able to open a console and run the **Python interactive shell** by typing `python`.

> Type `exit()` to quit the shell.

### About virtual environments

You install Python on your system and you start working on a website for Client X. You create a project folder and start coding. Along the way, you also install some libraries; for example, the Django framework. Let's say the Django version you install for Project X is 2.2. Now, your website is so good that you get another client, Y. She wants you to build another website, so you start Project Y and, along the way, you need to install Django again. The only issue is that now the Django version is 3.0 and you cannot install it on your system because this would replace the version you installed for Project X. You don't want to risk introducing incompatibility issues, so you have two choices: either you stick with the version you have currently on your machine, or you upgrade it and make sure the first project is still fully working correctly with the new version. Virtual environments are isolated Python environments, each of which is a folder that contains all the necessary executables to use the packages that a Python project would need (think of packages as libraries for the time being). When it comes to creating a virtual environment on your system, there are a few different methods to carry this out. As of Python 3.5, the suggested way to create a virtual environment is to use the [`venv`](https://docs.python.org/3/library/venv.html) module. Another common way of creating virtual environments is to use the [`virtualenv`](https://virtualenv.pypa.io/en/latest/) third-party Python package.

#### Your first virtual environment

It is very easy to create a virtual environment, but according to how your system is configured and which Python version you want the virtual environment to run, you need to run the command properly. Another thing you will need to do, when you want to work with it, is to activate it. Activating virtual environments basically produces some path juggling behind the scenes so that when you call the Python interpreter from that shell, you're actually calling the active virtual environment one, instead of the system one.

1. Open a terminal and change into the folder (directory) we use as root for our projects (our folder is `srv`). We are going to create a new folder called `my-project` and change into it.
2. Create a virtual environment called `lpp3ed`.
3. After creating the virtual environment, we will activate it. The methods are slightly different between Linux, macOS, and Windows.
4. Then, we will make sure that we are running the desired Python version (3.9.X) by running the Python interactive shell.
5. Deactivate the virtual environment.

We are going to start with an example on Windows

```powershell
 Alex@UNIT01 ~\srv  mkdir my-project # step 1

    Directory: C:\Users\Alex\srv

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          11/26/2022 12:47 PM                my-project

 Alex@UNIT01 ~\srv  cd .\my-project\
 Alex@UNIT01 ~\....\my-project  get-command -all python # check system python

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Application     python.exe                                         3.10.8150… C:\Python310\python.exe
Application     python.exe                                         0.0.0.0    C:\Users\Alex\AppData\Local\Microsoft\Wi…

 Alex@UNIT01 ~\....\my-project  python -m venv lpp3ed # step 2
 Alex@UNIT01 ~\....\my-project  .\lpp3ed\Scripts\activate # step 3
(lpp3ed)  Alex@UNIT01 ~\....\my-project  get-command -all python # check python again, now virtual env python is listed first

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Application     python.exe                                         3.10.8150… C:\Users\Alex\srv\my-project\lpp3ed\Scri…
Application     python.exe                                         3.10.8150… C:\Python310\python.exe
Application     python.exe                                         0.0.0.0    C:\Users\Alex\AppData\Local\Microsoft\Wi…

(lpp3ed)  Alex@UNIT01 ~\....\my-project  python # step 4
Python 3.10.8 (tags/v3.10.8:aaaf517, Oct 11 2022, 16:50:30) [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> exit()
(lpp3ed)  Alex@UNIT01 ~\....\my-project  deactivate # step 5
 Alex@UNIT01 ~\....\my-project 
```

On a Linux machine, the steps are the same, but the commands are structured slightly differently.

```sh
Python/srv on  01-python-intro [!?]
❯ mkdir my-project # step 1

Python/srv on  01-python-intro [!?]
❯ cd my-project/

Python/srv/my-project on  01-python-intro [!?]
❯ which python3.9 # check system python
/usr/bin/python3.9 # <-- system python3.9

Python/srv/my-project on  01-python-intro [!?]
❯ python3.9 -m venv lpp3ed # step 2

Python/srv/my-project on  01-python-intro [!?]
❯ source ./lpp3ed/bin/activate.fish # step 3

Python/srv/my-project on  01-python-intro [!?] via 🐍 v3.9.2 (lpp3ed)
❯ which python
/home/alex/Development/Python/srv/my-project/lpp3ed/bin/python

Python/srv/my-project on  01-python-intro [!?] via 🐍 v3.9.2 (lpp3ed)
❯ python # step 4
Python 3.9.2 (default, Feb 28 2021, 17:03:44)
[GCC 10.2.1 20210110] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> exit()

Python/srv/my-project on  01-python-intro [!?] via 🐍 v3.9.2 (lpp3ed) took 4s
❯ deactivate # step 5

Python/srv/my-project on  01-python-intro [!?]
```

Something to notice here is that in order to activate the virtual environment, we need to run the `lpp3ed/bin/activate` script, which needs to be sourced. When a script is sourced, it means that it is executed in the current shell, and therefore its effects last after the execution.

### Installing third-party libraries

In order to install third-party libraries, we need to use the Python Package Installer, known as **pip**. Chances are that it is already available to you within your virtual environment, but if not, you can learn all about it on its [documentation page](https://pip.pypa.io). The following example shows how to create a virtual environment and install a couple of third-party libraries taken from a requirements file.

```sh
Python/srv on  01-python-intro [!?]
❯ mkdir my-project

Python/srv on  01-python-intro [!?]
❯ cd my-project/

Python/srv/my-project on  01-python-intro [!?]
❯ python3.9 -m venv lpp3ed

Python/srv/my-project on  01-python-intro [!?]
❯ source ./lpp3ed/bin/activate.fish

Python/srv/my-project on  01-python-intro [!?] via 🐍 v3.9.2 (lpp3ed)
❯ cat requirements.txt
Django==3.1.7
requests==2.25.1⏎
# the following instruction shows how to use pip to install
# requirements from a file

Python/srv/my-project on  01-python-intro [!?] via 🐍 v3.9.2 (lpp3ed)
❯ pip install -r requirements.txt
Collecting Django==3.1.7
  Downloading Django-3.1.7-py3-none-any.whl (7.8 MB)
     |████████████████████████████████| 7.8 MB 1.4 MB/s
Collecting requests==2.25.1
  Downloading requests-2.25.1-py2.py3-none-any.whl (61 kB)
     |████████████████████████████████| 61 kB 777 kB/s
Collecting sqlparse>=0.2.2
  Downloading sqlparse-0.4.3-py3-none-any.whl (42 kB)
     |████████████████████████████████| 42 kB 1.0 MB/s
Collecting asgiref<4,>=3.2.10
  Downloading asgiref-3.5.2-py3-none-any.whl (22 kB)
Collecting pytz
  Downloading pytz-2022.6-py2.py3-none-any.whl (498 kB)
     |████████████████████████████████| 498 kB 1.5 MB/s
Collecting urllib3<1.27,>=1.21.1
  Downloading urllib3-1.26.13-py2.py3-none-any.whl (140 kB)
     |████████████████████████████████| 140 kB 658 kB/s
Collecting chardet<5,>=3.0.2
  Downloading chardet-4.0.0-py2.py3-none-any.whl (178 kB)
     |████████████████████████████████| 178 kB 602 kB/s
Collecting idna<3,>=2.5
  Downloading idna-2.10-py2.py3-none-any.whl (58 kB)
     |████████████████████████████████| 58 kB 1.5 MB/s
Collecting certifi>=2017.4.17
  Downloading certifi-2022.9.24-py3-none-any.whl (161 kB)
     |████████████████████████████████| 161 kB 722 kB/s
Installing collected packages: urllib3, sqlparse, pytz, idna, chardet, certifi, asgiref, requests, Django
Successfully installed Django-3.1.7 asgiref-3.5.2 certifi-2022.9.24 chardet-4.0.0 idna-2.10 pytz-2022.6 requests-2.25.1 sqlparse-0.4.3 urllib3-1.26.13

Python/srv/my-project on  01-python-intro [!?] via 🐍 v3.9.2 (lpp3ed) took 9s
```

### Your friend, the console

In this, the era of GUIs and touchscreen devices, it seems a little ridiculous to have to resort to a tool such as the console, when everything is just about one click away. Speed and productivity are important, and even though we have nothing against the mouse, being fluent with the console is very good for another reason: when you develop code that ends up on some server, the console might be the only available tool to access the code on that server.

---

## How to run a Python program

### Running Python scripts

Python can be used as a scripting language; in fact, it always proves itself very useful. Scripts are files (usually of small dimensions) that you normally execute to do something like a task. Many developers end up having their own arsenal of tools that they fire when they need to perform a task. It is rather common to have scripts running at a precise time on a server. For example, if your website database needs cleaning every 24 hours (for example, the table that stores the user sessions, which expire pretty quickly but aren't cleaned automatically), you could set up a Cron job that fires your script at 3:00 A.M. every day.

> The software utility Cron is a time-based job scheduler in Unix-like computer operating systems. People who set up and maintain software environments use Cron (or a similar technology) to schedule jobs (commands or shell scripts) to run periodically at fixed times, dates, or intervals.

### Running the Python interactive shell

Another way of running Python is by calling the interactive shell. We use the interactive shell every day. It's extremely useful to debug very quickly; for example, to check if a data structure supports an operation. Or maybe to inspect or run a piece of code. When you use Django (a web framework), the interactive shell is coupled with it and allows you to work your way through the framework tools, to inspect the data in the database, and much more. You will find that the interactive shell soon becomes one of your dearest friends on this journey you are embarking on. Another solution, which comes in a much nicer graphic layout, is to use the **Integrated Development and Learning Environment (IDLE)**. It's quite a simple **Integrated Development Environment (IDE)**, which is intended mostly for beginners. It has a slightly larger set of capabilities than the bare interactive shell you get in the console, so you may want to explore it.

### Running Python as a service

Apart from being run as a script, and within the boundaries of a shell, Python can be coded and run as an application.

### Running Python as a GUI application

Python can also be run as a **Graphical User Interface (GUI)**. There are several frameworks available, some of which are cross-platform, and some others that are platform-specific. In chapter 12, we'll see an example of a GUI application created using **Tkinter**, which is an object-oriented layer that lives on top of `Tk` (Tkinter means Tk interface).

> Tk is a GUI toolkit that takes desktop application development to a higher level than the conventional approach. It is the standard GUI for **Tool Command Language (Tcl)**, but also for many other dynamic languages, and it can produce rich native applications that run seamlessly under Windows, Linux, macOS, and more.

Tkinter comes bundled with Python; therefore, it gives the programmer easy access to the GUI world, and for these reasons, we have chosen it to be the framework for the GUI examples that are presented in this book. Among the other GUI frameworks, the following are the most widely used:

- PyQt5/PySide 2
- wxPython
- Kivy

---

## How is Python code organized?

Starting with the basics, how is Python code organized? Of course, you write your code into files. When you save a file with the extension `.py`, that file is said to be a Python module. It would be impractical to save all the code that it is required for software to work within one single file. That solution works for scripts, which are usually not longer than a few hundred lines (and often they are shorter than that). A complete Python application can be made of hundreds of thousands of lines of code, so you will have to scatter it through different modules, which is better, but not nearly good enough. It turns out that even like this, it would still be impractical to work with the code. So, Python gives you another structure, called a **package**, which allows you to group modules together. A package is nothing more than a folder that must contain a special file, `__init__.py`. This does not need to hold any code, but its presence is required to tell Python that this is not just a typical folder—it is actually a package. An example will make all of this much clearer.

```sh
Python/srv/my-project on  01-python-intro [!?] via 🐍 v3.9.2 (lpp3ed) took 4s
❯ tree -v example/
example/
├── core.py
├── run.py
└── util
    ├── __init__.py
    ├── db.py
    ├── math.py
    └── network.py

1 directory, 6 files
```

You can see that within the root of this example, we have two modules, `core.py` and `run.py`, and one package, `util`. Within `core.py`, there may be the core logic of our application. On the other hand, within the `run.py` module, we can probably find the logic to start the application. Within the `util` package, we expect to find various utility tools, and in fact, we can guess that the modules there are named based on the types of tools they hold: `db.py` would hold tools to work with databases, `math.py` would, of course, hold mathematical tools (maybe our application deals with financial data), and `network.py` would probably hold tools to send/receive data on networks. The `__init__.py` file is there just to tell Python that `util` is a package and not just a simple folder.

### How do we use modules and packages?

When a developer is writing an application, it is likely that they will need to apply the same piece of logic in different parts of it. It would be very bad practice to copy/paste (or, said more formerly, duplicate) the validation logic in every place where we expect a numeric answer. This would violate the **don't repeat yourself (DRY)** principle, which states that you should never repeat the same piece of code more than once in your application. In spite of the DRY principle, we feel the need here to stress the importance of this principle: you should never repeat the same piece of code more than once in your application! There are several reasons why repeating the same piece of logic can be very bad, the most important ones being:

- There could be a bug in the logic, and therefore you would have to correct it in every copy.
- You may want to amend the way you carry out the validation, and again, you would have to change it in every copy.
- You may forget to fix or amend a piece of logic because you missed it when searching for all its occurrences. This would leave wrong or inconsistent behavior in your application.
- Your code would be longer than needed for no good reason.

Python comes with a very extensive library. Now is a good time to define what a library is: a collection of functions and objects that provide functionalities to enrich the abilities of a language. For example, within Python's `math` library, a plethora of functions can be found, one of which is the `factorial` function, which calculates the factorial of a number.

> In mathematics, the factorial of a non-negative integer number, N, denoted as N!, is defined as the product of all positive integers less than or equal to N. For example, the factorial of 5 is calculated as:
>
> $5! = 5\times4\times3\times2\times1 = 120$
>
> The factorial of 0 is 0! = 1, to respect the convention for an empty product.

So, if you wanted to use this function in your code, all you would have to do is to import it and call it with the right input values.

```python
>>> from math import factorial
>>> factorial(5)
120
```

---

## Python's execution model

You can read all about Python's execution model in the official [language reference](https://docs.python.org/3/reference/executionmodel.html)

### Names and namespaces

Say you are looking for a book, so you go to the library and ask someone to obtain this. They tell you something like Second Floor, Section X, Row Three. So, you go up the stairs, look for Section X, and so on. It would be very different to enter a library where all the books are piled together in random order in one big room. When we write code, we have the same issue: we have to try and organize it so that it will be easy for someone who has no prior knowledge about it to find what they are looking for. When software is structured correctly, it also promotes code reuse. Furthermore, disorganized software is more likely to contain scattered pieces of duplicated logic. As a first example, let us take a book. We refer to a book by its title; in Python lingo, that would be a **name**. Python names are the closest abstraction to what other languages call variables. Names basically refer to objects and are introduced by **name-binding** operations.

```python
>>> n = 3  # integer number
>>> address = "221b Baker Street, NW1 6XE, London"  # Sherlock Holmes' address
>>> employee = {
... 'age': 45,
... 'role': 'CTO',
... 'SSN': 'AB1234567',
... }
>>> # let's print them
>>> n
3
>>> address
'221b Baker Street, NW1 6XE, London'
>>> employee
{'age': 45, 'role': 'CTO', 'SSN': 'AB1234567'}
>>> other_name
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'other_name' is not defined
```

We defined three objects in the preceding code; let's now examine their types and values:

- An integer number `n` (type: `int`, value: `3`)
- A string `address` (type: `str`, value: Sherlock Holmes' address)
- A dictionary `employee` (type: `dict`, value: a dictionary object with three key/value pairs)

So, what are `n`, `address`, and `employee`? They are **names**, and these can be used to retrieve data from within our code. They need to be kept somewhere so that whenever we need to retrieve those objects, we can use their names to fetch them. We need some space to hold them, hence: **namespaces**! A **namespace** is a mapping from names to objects. Examples are the set of built-in names (containing functions that are always accessible in any Python program), the global names in a module, and the local names in a function. Even the set of attributes of an object can be considered a namespace. The beauty of namespaces is that they allow you to define and organize your names with clarity, without overlapping or interference. For example, the namespace associated with the book we were looking for in the library can be used to import the book itself, like this:

```python
from library.second_floor.section_x.row_three import book
```

### Scopes

According to Python's documentation:

> "A scope is a textual region of a Python program, where a namespace is directly accessible."

Directly accessible means that, when looking for an unqualified reference to a name, Python tries to find it in the namespace. Scopes are determined statically, but actually, during runtime, they are used dynamically. This means that by inspecting the source code, you can tell what the scope of an object is. There are four different scopes that Python makes accessible (not necessarily all of them are present at the same time, of course):

- The **local** scope, which is the innermost one and contains the local names.
- The **enclosing** scope; that is, the scope of any enclosing function. It contains non-local names and also non-global names.
- The **global** scope contains the global names.
- The **built-in** scope contains the built-in names. Python comes with a set of functions that you can use in an off-the-shelf fashion, such as `print`, `all`, `abs`, and so on. They live in the built-in scope.

The rule is the following: when we refer to a name, Python starts looking for it in the current namespace. If the name is not found, Python continues the search in the enclosing scope, and this continues until the built-in scope is searched. If a name has still not been found after searching the built-in scope, then Python raises a `NameError` **exception**, which basically means that the name hasn't been defined (seen in the preceding example). The order in which the namespaces are scanned when looking for a name is therefore **local, enclosing, global, built-in (LEGB)**. This is all very theoretical, so let's see an example. In order to demonstrate local and enclosing namespaces, we will have to define a few functions.

```python
# scopes1.py
# Local versus Global
# we define a function, called local
def local():
    m = 7
    print(m)
# we define m within the global space
m = 5
# we call, or execute, the function local
local()
print(m)
```

When we execute this program with the following command

```sh
Python/srv/my-project on  01-python-intro [!?] via 🐍 v3.9.2 (lpp3ed)
❯ python scopes1.py
7
5
```

We see two numbers printed on the console: 7 and 5. What happens is that the Python interpreter parses the file, top to bottom. First, it finds a couple of comment lines, which are skipped, then it parses the definition of the function `local`. When called, this function will do two things: it will set up a name to an object representing number `7` and will print it. The Python interpreter keeps going, and it finds another name binding. This time the binding happens in the global scope and the value is `5`. On the next line, there is a call to the function `local`. At this point, Python executes the function, so at this time, the binding `m = 7` happens in the local scope and is printed. Finally, there is a call to the `print` function, which is executed and will now print `5`. What would happen if we removed that `m = 7` line? Remember the LEGB rule. Python would start looking for `m` in the local scope (function `local`), and, not finding it, it would go to the next enclosing scope. The next one, in this case, is the global one because there is no enclosing function wrapped around `local`. Therefore, we would see the number `5` printed twice on the console. Let's see what the code would look like in this case:

```python
# scopes2.py
# Local versus Global
def local():
    # m doesn't belong to the scope defined by the local function
    # so Python will keep looking into the next enclosing scope.
    # m is finally found in the global scope
    print(m, 'printing from the local scope')
m = 5
print(m, 'printing from the global scope')
local()
```

```sh
Python/srv/my-project on  01-python-intro [!?] via 🐍 v3.9.2 (lpp3ed)
❯ python scopes2.py
5 printing from the global scope
5 printing from the local scope
```

As expected, Python prints `m` the first time, then when the function `local` is called, `m` is not found in its scope, so Python looks for it following the LEGB chain until `m` is found in the global scope. Let's see an example with an extra layer, the enclosing scope:

```python
# scopes3.py
# Local, Enclosing and Global
def enclosing_func():
    m = 13
    def local():
        # m doesn't belong to the scope defined by the local
        # function so Python will keep looking into the next
        # enclosing scope. This time m is found in the enclosing scope
        print(m, 'printing from the local scope')
    # calling the function local
    local()
m = 5
print(m, 'printing from the global scope')
enclosing_func()
```

```sh
Python/srv/my-project on  01-python-intro [!?] via 🐍 v3.9.2 (lpp3ed)
❯ python scopes3.py
5 printing from the global scope
13 printing from the local scope
```

As you can see, the `print` instruction from the function `local` is referring to `m` as before. `m` is still not defined within the function itself, so Python starts walking scopes following the LEGB order. This time `m` is found in the enclosing scope.

---

## Objects and classes

We have already seen that objects are Python's abstraction for data. In fact, everything in Python is an object: numbers, strings (data structures that hold text), containers, collections, even functions. You can think of them as if they were boxes with at least three features: an ID (which is unique), a type, and a value. But how do they come to life? How do we create them? How do we write our own custom objects? The answer lies in one simple word: **classes**. Objects are, in fact, instances of classes. The beauty of Python is that classes are objects themselves, but let's not go down this road. It leads to one of the most advanced concepts of this language: **metaclasses**. For now, the best way for you to get the difference between classes and objects is by means of an example. Classes are used to create objects. In other words, we all know what a bike is; we know the class. But then your friend has her own bike, which is an instance of the bike class. Her bike is an object with its own characteristics and methods. You have your own bike. Same class, but different instance. Every bike ever created in the world is an instance of the bike class.

```python
# bike.py
# let's define the class Bike
class Bike:
    def __init__(self, colour, frame_material):
        self.colour = colour
        self.frame_material = frame_material
    def brake(self):
        print("Braking!")
# let's create a couple of instances
red_bike = Bike("Red", "Carbon fiber")
blue_bike = Bike("Blue", "Steel")
# let's inspect the objects we have, instances of the Bike class.
print(red_bike.colour) # prints: Red
print(red_bike.frame_material) # prints: "Carbon fiber"
print(blue_bike.colour) # prints: Blue
print(blue_bike.frame_material) # prints: Steel
# let's brake!
red_bike.brake() # prints: Braking!
```

The definition of a class happens with the `class` statement. Whatever code comes after the `class` statement, and is indented, is called the body of the class. In our case, the last line that belongs to the class definition is `print("Braking!")`. After having defined the class, we are ready to create some instances. You can see that the class body hosts the definition of two methods. A **method** is basically (and simplistically) a function that belongs to a class. The first method, `__init__`, is an **initializer**. It uses some Python magic to set up the objects with the values we pass when we create it.

> Every method that has leading and trailing double underscores, in Python, is called a **magic method**. Magic methods are used by Python for a multitude of different purposes, hence it's never a good idea to name a custom method using two leading and trailing underscores. This naming convention is best left to Python.

The other method we defined, `brake`, is just an example of an additional method that we could call if we wanted to brake. It contains only a `print` statement, of course—it's just an example.

---

## Guidelines for writing good code

Writing good code is not as easy as it seems. As we have already said, good code exposes a long list of qualities that are difficult to combine. Writing good code is, to some extent, an art. Regardless of where on the path you will be happy to settle, there is something that you can embrace that will make your code instantly better: **PEP 8**.

> A [**Python Enhancement Proposal (PEP)**](https://www.python.org/dev/peps) is a document that describes a newly proposed Python feature. PEPs are also used to document processes around Python language development and to provide guidelines and information more generally.

PEP 8 is perhaps the most famous of all PEPs. It lays out a simple but effective set of guidelines to define Python aesthetics so that we write beautiful Python code. Coding today is no longer a check-in/check-out business. Rather, it's more of a social effort. Several developers collaborate on a piece of code through tools such as Git and Mercurial, and the result is code that is produced by many different hands.

### Python culture

Python has been adopted widely in all coding industries. It is used by many different companies for different purposes, while also being an excellent education tool (it is excellent for that purpose due to its simplicity, making it easy to learn; it encourages good habits for writing readable code; it is platform-agnostic; and it supports modern object-oriented programming paradigms). One of the reasons Python is so popular today is that the community around it is vast, vibrant, and full of brilliant people. Many events are organized all over the world, mostly either around Python or some of its most adopted web frameworks, such as Django. Python's source is open, and very often so are the minds of those who embrace it. Check out the community page on the Python website for more information and get involved! There is another aspect to Python, which revolves around the notion of being **Pythonic**. It has to do with the fact that Python allows you to use some idioms that aren't found elsewhere, at least not in the same form or as easy to use (it can feel claustrophobic when one has to code in a language that is not Python, at times). Anyway, over the years, this concept of being Pythonic has emerged and, the way we understand it, it is something along the lines of doing things the way they are supposed to be done in Python. To help you understand a little bit more about Python's culture and being Pythonic, we will show you the Zen of Python—a lovely Easter egg that is very popular. Open up a Python console and type `import this`.

```sh
>>> import this
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
Namespaces are one honking great idea -- let's do more of those!
```
