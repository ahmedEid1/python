## Chapter 1
- Scaler Types :
    - int
      - unlimited precision signed integers
    - float
      - `float("nan"), float("inf"), float("-inf")`
    - None
      - null value
    - bool
        - `True` or `False`
            - `0, [], ''` is falsy
---
- Zen :
  - **_Flat is better than nested_**
  - _**explict is better than implicit**_   
----
- `input()` : request input text from the user
-----
----
## Chapter 2 (Collections)
- **str**
    - str is a sequence type
    - sequence of unicode code points
    - immutable
    - multiLine string use 3 double quotes `""" """`
    - row string (don't need to escape things) `r''`
    - methods on strings :
        - `capitalize()` : return a new string
----
- `Zen : practicality beats purity`
----
- **bytes**
    - `b''`
    - sequence of bytes
    - used for :
        - raw binary data
        - fixed-width single-byte encoding (ex. ASCII)
---
- how to convert between strings and bytes ?
    - you need to know the encoding of the bytes used to represent the string
        - form string to byte :
            - `encode()`
        - from byte to string :
            - `decode()`
    
---
- `list`
    - [] 
    - sequence of objects
    - Mutable
    - methods on lists :
        - `append` : add to the end of the list
        
----
- `dict`
    - Map keys to values
    - `{key: value}`
    - after python3.7 : 
        - keys are kept in insertion order
-----
---
## Chapter 3 (Modularity)
- **Modules** :
    - **self-contained reusable pieces that can be combined in new ways to solve different problems**


- `**` : is the exp. (^) operator in python


- `__name__` :  allow us to detect whether a module is to run as a script or imported into another module 
    - ex. `if __name__ == '__main__'`
    

- to access command line args :
    - use `sys.argv[]`
        - [0] is the script name

----
## Chapter 4 (Objects)
- **assignment operations bind objects to names (never copy by value)**
- ints are immutable 
- list are mutable 
- `id()` : return a unique identifier for an object
---
- **python vars are all named references to objects** 
---
- args are referenced passed to functions 
    - so you need to copy vars before passing them if you don't want them to change
- return also return references and  does not copy the objects
----
- argument with default values must come after those with no default values
---
#### default value evaluation 
- default ars are evaluated when `def` is executed
    - **immutable** default value do not cause a problem
    - **mutable** default value can cause a confusing effect
- always use immutable objects as default values
----
- **python will not generally preform implicit conversion between types**
    - **_except in ifs and loops_**
---
#### Scopes in python :
1. **local** : inside the current function
2. **enclosing** : inside enclosing functions
3. **global** : at the top level of a module
4. **built in**
    - **LEGB**

- scopes are added from `import` or `def` of a function or a class 
- to access the global scope :
    - use `global` 
-----
- Zen : special cases are not special enough to break the rules
----
- the repetition operation :
    - if you multiply string by a number :
        - you get a string with a length equals to the number
------
## Chapter 5 (Built-in collections)
### tuples :
- immutable sequence of arbitrary objects
- use `()` instead of `[]`
- one element tuple :
    - `(element,) ` [add the comma after the element]
----
#### tuple unpacking :
- destructing operation that unpacks data structure into named references
---
### Strings :
- immutable
- use `join` for contacting string
    - `join()` : takes a collection of strings and concat them with separator between them
        - the separator is the string that the method is called on
- `partition(sperator)`:
    - return a tuple (before, separator, after)
----
### Range 
- **sequence representing an arithmetic progression of integers**
- create using `range()`
    - one arg >>> stop value
    - two args >>> start and stop
    - three args >>> start, stop and step
-------
### enumerate 
- **_construct an iterable of (index, value) tuples around another iterable_**

---
### List 
- mutable
- you can index from the end using negative numbers
    - the last element is `-1`
---
#### Slicing 
- a_list[start : stop]
    - stop not included 

- you can copy a list you can use :
    - `a_list[:]`
        - the elements inside that the list are still referencing the same objects
            - this is called a **shallow copy**
- `del` :
    - you can use it to delete elements from the list

- `reversed(a_list)`:
    - does not return a list but s reverse iterator
        - you can pass the returned value to `list()` to get a list
-----
### Dictionaries 
- dict coping shallow by default
- `my_dict.update(a_dict)`:
    - extend a dict using another dict 
-  `my_dict.items()`:
    - return the key and value

----
### Sets 
- **_unordered collection of unique elements_**
- mutable
- build using `{}`
- to create an empty set : use `set()` :
    - because `{}` create an empty dict
---
#### difference between `discard()` and `remove()`:
- remove raise an exception if the element does not exist
    - discard do nothing
-----    
#### set algebra operations 
- union :
    - `a_set.union(another set)`
- intersection :
    - `a_set.intersection(another set)`
-  difference
    - `a_set.difference(another set)`
        - all elements in the first set that are not in the second set
    

- in one set or the other but not both :
    - `symmetric_difference()`
    

- `issubset()`
- `issuperset()`
- `isdisjoint()` :
    - true if the two sets have nothing in common 
----
---
### protocols 
- a protocol is a set of operations that a type must support to implement the protocols
- examples :
    - Container
    - Sized
    - iterable
    - Sequence 
    - Mutable sequence (list)
    - Mutable set (set)
    - Mutable Mapping (dict)
-----
## Chapter 6 (Exceptions)
#### Exception handling :
- mechanism for interrupting normal program flow and continuing in a surrounding context
    - raise an exception >>> handle the exception
    - unhandled exception cause the program to terminate
---------------
- use `try except` to handle exceptions
---
- exceptions resulting from a programmer errors :
    - ex. (indention, syntax, name)
        - should be identified and solved during development and not handled at run time
---------
- `!r`:
    - if you insert `!r` after ab expression in a fString :   
        - its ripple representation get inserted into the string
            - `f'{exp!r}''`
----
- you can re-raise and exception using :
    - `raise` in the catch block after you finished handling it

-----
- avoid catching `type errors`:
    - if it works : then this increase functionality 
    - if not : let type errors arise on their own
---
#### prepare for failure :
- there are two ways :
    - LBYL
    - EAFP
- EAFP is preferred in python
    - hope for the best but prepare for consequences 


- Exceptions + EAFP :
    - make it very hard for problems to be silently ignored 
-----------
- put any clean up actions in :
    - `finally`

----
## Chapter 7 (Iteration) 
#### Comprehension :
- Concise syntax for describing (list, set and dictionaries)
    - readable and expressive 
    - ex. `[len(word) for word in words]`
    

- dict comprehension does not work on the dict source (but return the keys)
    - so use `dicr.items()` to get values and keys
    
- you can filter the comprehension using a **predict** 


- comprehension should normally have no side effect 
----
- Zen : `simple is better than complex`
---

#### iteration protocol
- iterator :
    - can be passed to `next()` to get the next value in the sequence 
- iterable :
    - can be passes to `iter()` to produce an iterator 
---
#### Generator
- iterables defined by functions
- lazy evaluation (compute the next value on demand)
- can model infinite sequence of values with no definite end
- a generator function must include at least one `yield` statement
- each time you call a generator function  it return a separate generator 


- generator expression :
    - `(x  for x in range(1, 10000000000000))`
        - return a generator
----
#### iteration tools
- `sum()`
- `enumerate()` (todo: look up?!)
- `any()` : return true if any elements is true
- `all()` : return true if all the elements is true 
- `zip()` : synchronize iteration across two or more iterables
  

- we also have the `itertools` provide a lot of useful functions
    - `islice(iterator, num)` : perform lazy slicing of any iterators 
    - `count()` : an unbounded arithmetic sequence of ints
    - `chain()` : lazily contacting some iterables togethers   
    
 
---
## Chapter 8 (Classes)
- **classes** :
    - define the structure and behaviour of an object


- ` python let you strike the wright balance between functions and classes`


- `__init__`  : used for initializing new objects
    - `__init__` : 
        - is an initialized not a constructor 
            - so it configures the object after it is already constructed
            - the constructor is provided by the python, and it checks for a `__init__` method and call it if it exists
    
    - `self` is like `this` in java
-----
- by convention : implementation details of an object should stat with `_`
---
- **Class invariants :**
    - truths  about an object that endure for its lifetime
    - you can enforce them in the `__init__` method
---
- **the law of Demeter :**
    - the principle of least knowledge
    - help reduce coupling
- you should never call methods on objects you received from other calls (only talk to your friends)
    - ex. use method to interact with a composite object and don't call the methods on the object directly
-----
- Zen : `complex is better than complicated`
    - many moving parts combined in a clever box are now one good tool
---
- **tell, don't ask :**
    - tell other objects what to do instead of :
        - asking them for their state and response to it 
    - can reduce coupling 
-----
- polymorphism :
    - using objects of different types through a uniform interface
    - achieved in python through __duck Typing__
    

- what is duck typing ?
    - an object's fitness to use only determined at use
-----
- inheritance :
    - python use late binding for inheritance 
        - no method calls or attribute look up are bonded to actual objects until the moment they are called
            - so you can try any method on any object
    - inheritance is used in python for sharing implementations
    
---
## Chapter 9
- what is a resource ?
    - program element that must be released or closed after use
    - python mange resources using context managers
---
- `open(file, [mode], [encoding])` : open a file for reading or writing 
-----
- getting the default encoding of a system :
    - `import sys`
    - `sys.getdefaultencoding()`
-----
- opening files modes :
    - w, r, a
    - selector : 
        - b, t
----
- `write()`:
    - return the number of codePoints written to the file
-  `open()` :
    - return a file-like object
    
-  `read([num])`:
    - **without args** : return all the content of the file in the first call then '' ''
    - **in text mode**: takes number of char to read
    - **in byte mode**: takes number of bytes to read

- `seek()` : used to move the courser
    - can only be moved to `0` or values form` tell()`
    
- `readLine()` : read the line by line on every call
- `readLines()` : return a list of all the lines in the file
-----
- python has `writeLines` but not `writeline` !
- `writeLines` :
    - takes a list of string to add to the file
        - note : you must add the ` \n` yourself to start a new line
----
- **the file object is iterable, so you can loop over it line by line**
----
- how to print without adding a new line between every two print statement ?
    - you can use `sys.stdout.write()`
---
- to ensure the file get close :
    - put the `open` in a `try` and the `close` in the `finally`
        - or use a with-block
----
##### with-block
- control flow structure for managing resources
    - can be used with any object that support the context-manager protocol
------------------------
- bitwise operations :
    - `&` (bitwise and)
    - `|` (bitwise or)
    - `>>` (right-shift)
    - `<<` (left-shift)
---------
- to wrap your object with a context manager :
    - `from contextlib import closing`
    - wrap the constructor with the method :
        - `with closing(myObject()) as obj`

