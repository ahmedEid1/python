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









----
## Chapter -3 (Iteration) 
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
## Chapter -2 (Classes)
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
## Chapter -1
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

