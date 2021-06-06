# Testing and Modules

## In Tests We Trust - TDD with Python
- Unit tests are some pieces of code to exercise the input, the output and the behaviour of your code. You can write them anytime you want.
- The test file name should follow the same name of module name. For example, if our module is gender.py, our test name should be test_gender.py. 

##### thing to care about is the structure. A convention widely used is the AAA: Arrange, Act and Assert:
- Arrange: you need to organize the data needed to execute that piece of code (input);
- Act: here you will execute the code being tested (exercise the behaviour);
- Assert: after executing the code, you will check if the result (output) is the same as you were expecting.

##### The Cycle
The cycle is made by three steps:
- 🆘 Write a unit test and make it fail (it needs to fail because the feature isn’t there, right?)
- ✅ Write the feature and make the test pass! 
- 🔵 Refactor the code

###### NOTES:
- The greatest advantage about TDD is to craft the software design first
- Your code will be more reliable: after a change you can run your tests and be in peace
- Beginning may be hard — and that’s fine. You just need to practice!

## Recursion
The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called as recursive function. Using recursive algorithm, certain problems can be solved quite easily. Examples of such problems are Towers of Hanoi (TOH), Inorder/Preorder/Postorder Tree Traversals, DFS of Graph, etc.

- In the recursive program, the solution to the base case is provided and the solution of the bigger problem is expressed in terms of smaller problems.

###### the disadvantages of recursive programming over iterative programming is:
The recursive program has greater space requirements than iterative program as all functions will remain in the stack until the base case is reached. It also has greater time requirements because of function calls and returns overhead.

###### the advantages of recursive programming over iterative programming is:
Recursion provides a clean and simple way to write code

## Python Lists
- List literals are written within square brackets [ ]. Lists work similarly to strings -- use the len() function and square brackets [ ] to access data, with the first element at index 0.

- Python's *for* and *in* constructs are extremely useful, and the first use of them we'll see is with lists. The *for* construct -- for var in list -- is an easy way to look at each element in a list (or other collection).Do not add or remove from the list during iteration.

- The range(n) function yields the numbers 0, 1, ... n-1, and range(a, b) returns a, a+1, ... b-1 -- up to but not including the last number. The combination of the for-loop and the range() function allow you to build a traditional numeric for loop

- ###### Here are some other common list methods:

- list.append(elem) -- adds a single element to the end of the list. Common error: does not return the new list, just modifies the original.
- list.insert(index, elem) -- inserts the element at the given index, shifting elements to the right.
- list.extend(list2) adds the elements in list2 to the end of the list. Using + or += on a list is similar to using extend().
- list.index(elem) -- searches for the given element from the start of the list and returns its index. Throws a ValueError if the element does not appear (use "in" to check without a ValueError).
- list.remove(elem) -- searches for the first instance of the given element and removes it (throws ValueError if not present)
- list.sort() -- sorts the list in place (does not return it). (The sorted() function shown later is preferred.)
- list.reverse() -- reverses the list in place (does not return it)
- list.pop(index) -- removes and returns the element at the given index. Returns the rightmost element if index is omitted (roughly the opposite of append()).

## python strings
- Python strings are "immutable" which means they cannot be changed after they are created (Java strings also use this immutable style). Since strings can't be changed, we construct new strings as we go to represent computed values.

- ###### Here are some of the most common string methods :
- s.lower(), s.upper() -- returns the lowercase or uppercase version of the string

- s.strip() -- returns a string with whitespace removed from the start and end

- s.isalpha()/s.isdigit()/s.isspace()... -- tests if all the string chars are in the various character classes

- s.startswith('other'), s.endswith('other') -- tests if the string starts or ends with the given other string

- s.find('other') -- searches for the given other string (not a regular expression) within s, and returns the first index where it begins or -1 if not found

- s.replace('old', 'new') -- returns a string where all occurrences of 'old' have been replaced by 'new'

- s.split('delim') -- returns a list of substrings separated by the given delimiter. The delimiter is not a regular expression, it's just text. 'aaa,bbb,ccc'.split(',') -> ['aaa', 'bbb', 'ccc']. As a convenient special case s.split() (with no arguments) splits on all whitespace chars.

- s.join(list) -- opposite of split(), joins the elements in the given list together using the string as the delimiter. e.g. '---'.join(['aaa', 'bbb', 'ccc']) -> aaa---bbb---ccc

## Python Modules
Modular programming refers to the process of breaking a large, unwieldy programming task into separate, smaller, more manageable subtasks or modules. Individual modules can then be cobbled together like building blocks to create a larger application.

- ###### There are several advantages to modularizing code in a large application:
- Simplicity: Rather than focusing on the entire problem at hand, a module typically focuses on one relatively small portion of the problem. If you’re working on a single module, you’ll have a smaller problem domain to wrap your head around. This makes development easier and less error-prone.
- Maintainability: Modules are typically designed so that they enforce logical boundaries between different problem domains. If modules are written in a way that minimizes interdependency, there is decreased likelihood that modifications to a single module will have an impact on other parts of the program. (You may even be able to make changes to a module without having any knowledge of the application outside that module.) This makes it more viable for a team of many programmers to work collaboratively on a large application.
- Reusability: Functionality defined in a single module can be easily reused (through an appropriately defined interface) by other parts of the application. This eliminates the need to duplicate code.
- Scoping: Modules typically define a separate namespace, which helps avoid collisions between identifiers in different areas of a program.

- ###### There are actually three different ways to define a module in Python:
- A module can be written in Python itself.
- A module can be written in C and loaded dynamically at run-time, like the re (regular expression) module.
- A built-in module is intrinsically contained in the interpreter, like the itertools module.
