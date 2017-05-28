class: center, bottom


# From Zero to Hero

---
# Desclaimer

1. This is not Algorithm 101 - We're not gonna cover all python data types

---
class: top, right, fit-image
layout: false
background-image: url(http://localhost:8000/images/zen_of_python.png)


---
# Objetivo

Criar uma pipeline completa utilizando _Pipeline as Code_ com Jenkins e Docker como
plataforma do projeto.

???
Introduzir o conceito de Pipeline as code, Docker, Jenkins

---


class: left, middle
background-position: bottom;

# Como faremos

Criaremos duas pipelines.

--

1. Acionada após `push` na branch `develop`

--
1. Acionada após `push` na branch `master`

---

# Operators



---
# List

Lists are the workhorse of python:

```python
# Basic list
my_list = ['foo', 5, 5.0, True]

# Index Lookup
my_list[0]

# Inserting
my_list.append('New Element')

# Removing components - By index or the last one
my_list.pop(1)

# Removing by value
my_list.remove(5)

# Slicing
my_list[0:1]
my_list[-4:]

# the in operator
'foo' in my_list
```

---

# Control Flow

We have if/elif/else. We don't have semicolons. Everything is handled by identation, and we use ":" to start a block

```python
if expression:
    statement(s)
elif expression:
    statement(s)
elif expression:
    statement(s)
...
else:
    statement(s)
```

Logic Conditions

```python
if x and y:
  statement

if a or b:
  statement
```

---
# Control Flow

Almost Pure English

```python
if something is None:
  statement

if something is not None:
  statement
```

---
# Freaking For Loop ma friend

Most common way to loop:

```python
for item in ['foo', 'bar', 'biz']:
  print(item)

```
Range function:
```python
for i in range(10):
    print(i)
```

Len function might be helpful
```python
mah_list = ['foo', 'bar', 'biz']
for item in range(len(mah_list)):
  print(item)
```

---

# Functions

```python
def foo(arg1, arg2):
  do_something
```

Return is optional, python will `return None` if you miss `return`
```python
>>> def do_nothing():
...   print("foo")
...
>>> val = do_nothing()
foo
>>> val is None
True
```
---
# Functions

You can have optional arguments:
```python
def foo(name, caps=True):
  greeting = "Hello {}".format(name)
  if caps:
    print(greeting.upper())
  else:
    print(greeting)
...
>>> foo('bernardo')
HELLO BERNARDO
>>> foo('bernardo', caps=False)
Hello bernardo
```

Builtin Functions:
```python
len(), abs(), print()
```
---
# Functions

Returning and documentation:

```python
>>> def stupid_sum(a, b):
...   """ This function sum two arguments and return the result """
...   return a + b
...
>>> stupid_sum.__doc__
' This function sum two arguments and return the result '
>>> stupid_sum(1, 1)
2
```

---
# Exercise 01

Create a function called `check_linux_version`:

1. Receive a parameter with kernel information
2. That returns `el5` if the kernel belongs to a Enterprise Linux 5
3. That returns `el6` if the kernel belongs to a Enterprise Linux 6
4. That returns `el7` if the kernel belongs to a Enterprise Linux 7
5. That returns `unkown_version` if the none of the above


---

# Exercise 02

We will write a function similar to the GNU `grep` program.

The function will:

1. Receive two parameters `pattern` and `content`

*pattern* is the string we're looking for

*content* is a string with the file content


The function should return a list with **all lines** that has the given `pattern`

If the pattern wasn't found return an **empty list**

---

# Exception Handling

_Errors should never pass silently._ ~ Zen of Python

```python
  try:
    x = 5 + 'hey'
  except:
    print("you're stupid!")
```
--

#### Pass

_Unless explicitly silenced._ ~ Zen of Python
```python
  try:
    x = 5 + 'hey'
  except:
    pass
```
--

#### Raising Exceptions

```python
  try:
    x = 5 + 'hey'
  except:
    raise MyCustomCoolException("You're stupid!")
```

---
# Exception Handling

Specific errors / Finally

```python
  try:
    x = 5 + 'hey'
  except ZeroDivisionError:
    print("Shall not see")
  finally:
    print("Aloha")
```

---

# Tuples

Tuple is an ordered sequence of items same as list.The only difference is that tuples are immutable. Tuples once created cannot be modified.

Tuples are used to write-protect data and are usually faster than list as it cannot change dynamically.



---
#Dictionaries

Dictionary is an unordered collection of key-value pairs.

It is generally used when we have a huge amount of data. Dictionaries are optimized for retrieving data. We must know the key to retrieve the value.

an be marshall/unmarshall to JSON

```python
>>> foo = {}
```

???
1. Create a dict from cmd. Show how to access the value
1. Insert/Update key
1. Looping over a dict
1. Find if key exists with `in` and `has_key`
1. Method `keys`/`iterkets`, `values`
1. Show `iteritems` method
1. `del dict[key]`
1. `dict.get(key, default)`

---
# Exercices

1. Given a string return a dict where letters from the string are keys and the value are the count of it in the string.

Example: banana
```
{'b': 1, 'a': 3, 'n': 2}
```

#Set

A set object is an unordered collection of distinct hashable objects. Common uses include membership testing, removing duplicates from a sequence, and computing mathematical operations such as intersection, union, difference, and symmetric difference. (For other containers see the built in dict, list, and tuple classes, and the collections module.)

---

# Python Modules

When our program grows bigger, it is a good idea to break it into different modules.

A module is a file containing Python definitions and statements. Python modules have a filename and end with the extension .py.

```python
import sys
sys.path

for path in sys.path:
  print(path)
```

---

# I/O

Handling Files

```python
f = open("test.txt", 'r')
f.read()
f.close()
```

???
1. read, than readlines than readline
1. line loop, print with `end=''`
1. try,finally
1. `with` context manager
1. Show the `seek` example to read the content again
Show the old way py26 than the new way

--

Writing
```python
with open("test.txt", mode='w') as writer:
  writer.write("my content\n")
  writer.write("this is nice\n")
```

???
1. Writing file
1. Append a file

---

# Exercise xx

Write a grep script, for real this time! Use your grep engine (Exercise 02) to save some time.

The file name should be exact: **grep.py**

The script should receive two arguments. First, the **search pattern**, Second the **file path**.

The script should exit with **returncode 1** and return a message if: 

  1. Both arguments were not provided. Print message: **Two arguments are required, pattern and file path.**
  1. The file doesn't exists. Print message: **File *filename* doesn't exists**

The script should return:
  1. The same way as GNU grep, return **each match in a new line**.
  1. Nothing if no lines matches

Remember the pythonic way is **ask for forgiveness not permission!**

BONUS: Replace GNU grep with your new script using a shell alias: `alias grep="/path/to/grep.py"`

---

# Regular Expression

Regular expressions are handled by module `import re`

Most methods follows the same structure:

1. Pattern
2. String
3. Flags

--

### FINDALL

Return a list with all matches

```python
import re
re.findall(r'\d+', "Bernardo has 25 years old and he's a "
"DevOps Engineer at AvenueCode")
```

???

Findall
`\d` = any digit
+ = One or more occurance

---

# Regular Expression

Compiling a regular expression

```python
regex = re.compile('http\://|https://')
regex.match("https://avenuecode.com")
```

???
Demonstrate re.match() = Return match object or None

--
Searching for a pattern

```python
print(re.match(r'avenuecode', "https://avenuecode.com"))
print(re.search(r'avenuecode', "https://avenuecode.com"))

```
???
.group() to return the matched string

--

Find all occurences

```python
test = """
https://avenuecode.com
https://avenuecode.com.br
https://acdc.avenuecode.com
https://jenkins.avenuecode.com"""
print(re.search(r'avenuecode', "https://avenuecode.com"))
print(re.findAll(r'avenuecode', "https://avenuecode.com"))
```

---
# Regular Expression

Replacing stuff!

```python
re.sub(r'avenuecode', 'ac4success', "https://avenuecode.com")
```

-- 
Grouping

```python
regex = re.match(r'(http|https)\://(\w*).(\w.*)', "https://jenkins.avenuecode.com", flags=re.MULTILINE)
regex.group(1))
```

---

# Interacting with Underlying OS

```python
import os
```

Interacting with the File System


Getting file information
???
os.getcwd()
os.listdir()
os.stat(file) // 
os.makedirs('foo/bar')
os.listdir() // or give path

# Modification time example
mod_time = os.stat('.gitignore').st_mtime
print(datetime.datetime.fromtimestamp(mod_time))

---

# OS

Environment Variables
```python
os.environ

os.getenv('PATH')
```
--

Creating a file at home. How can we do that?


???
Example: LOGNAME to collect username

print(os.path.join(os.getenv('HOME'), 'foo.txt'))
print(os.path.expanduser("~/foo.txt"))

Get file
os.path.exists()

Remove it
os.remove()

File path manipulation
os.path.basename -- filename
os.path.dirname -- directory
os.path.split -- split file/path
os.path.splitext(f) -- split file and extension

os.uname()

os.system -- calls os, but let's work on subprocess
---

# SHUTIL

```python
import shutil
```

???
1. Create a file
1. shutil.copy to /tmp
1. shutil.move to user home
1. Create a bunch of temp files
1. Use shutil.copytree
1. Remove it using shutil.rmtree
1. Create a backup using shutil.make_archive

```python
shutil.make_archive('backup', format='zip', root_dir='/Users/bvale/projects/python-devops/exercise01')
```

---

# Exercises

1. Write a script that compress files older than 7 days from a given folder

```shell
./script /tmp/backup
```

2. Write a second script that removes all files from a folder that has an specific extension:

```shell
./script2 /tmp/files bkp
```

---

# Subprocess :)

The subprocess module allows you to spawn new processes, connect to their input/output/error pipes, and obtain their return codes. This module intends to replace several older modules and functions:

```
os.system
os.spawn*
os.popen*
popen2.*
commands.*
```

PEP 324 – PEP proposing the subprocess module

--

Let's give it a try :)

```python
subprocess.call(cmd)
```

???
`subprocess.call(cmd)` wait for cmd exec and return resultcode

1. Explain result code
1. Explain list of commands
1. Explain shell=True with exit and ls and the threats with `;` plus rm -rf --no-preserve-root
1. Explain stdout with a file

---
# Subprocess :)

What if we don't wanna write a logic to identify errors ?

--


```
subprocess.check_output(cmd)
```

???
1. Show the exceptions and the output

---
#Subprocess

Complex cases. Popen!

https://docs.python.org/2/library/subprocess.html#popen-constructor

???
Explain why popen is usefull, e.g: cwd, env, rc, stdout, stderr

Open process and explain the lifecycle `child = subprocess.Popen(["jconsole"])`
1. child.poll()
1. child.kill()

1. Open a shell with child = subprocess.Popen("/bin/bash", stdin=subprocess.PIPE, stdout=subprocess.PIPE)
and use communicate to send data

---
# Exercice Time

Write a script to deploy a static website.

1. Install nginx or apache
1. Push your html to nginx home/apache home
1. Reload the web server if you need

To test it use Vagrant or Docker

For docker, run a centos:7 with this command:

```
docker run -it --rm -v $(pwd)/deploy.py:/tmp/deploy.py -p 81:80 centos:7

python /tmp/deploy.py
```

---

# Sys

```python
import sys
```