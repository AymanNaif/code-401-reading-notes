# Python Regular Expression 

Regular Expressions, often shortened as regex, are a sequence of characters used to check whether a pattern exists in a given text (string) or not. They are used at the server side to validate the format of email addresses or passwords during registration, used for parsing text data files to find, replace, or delete certain string, etc. They help in manipulating textual data, which is often a prerequisite for data science projects involving text mining.

**Regular Expressions in Python**

In Python, regular expressions are supported by the re module. The **re library** in Python provides several functions that make it a skill worth mastering.

**Basic Patterns: Ordinary Characters**

We can easily tackle many basic patterns in Python using ordinary characters. Ordinary characters are the simplest regular expressions. They match themselves exactly and do not have a special meaning in their regular expression syntax.

**Wild Card Characters: Special Characters**

Special characters are characters that do not match themselves as seen but have a special meaning when used in a regular expression. For simple understanding, they can be thought of as reserved metacharacters that denote something else and not what they look like.

**Repetitions**

It becomes quite tedious if you are looking to find long patterns in a sequence. Fortunately, the re module handles repetitions using the following special characters:

```+``` - Checks if the preceding character appears one or more times starting from that position.

```*``` - Checks if the preceding character appears zero or more times starting from that position.

```?``` - Checks if the preceding character appears exactly zero or one time starting from that position.

**Grouping in Regular Expressions**

The ***group*** feature of regular expression allows us to pick up parts of the matching text. Parts of a regular expression pattern bounded by parenthesis ```()``` are called groups. The parenthesis does not change what the expression matches, but rather forms groups within the matched sequence. 

**Greedy vs. Non-Greedy Matching**

When a special character matches as much of the search sequence (string) as possible, it is said to be a "Greedy Match".

**Function provided by 're'**

The re library in Python provides several functions to make our tasks easier, such as the ```re.search()```, ```re.match()```.



# [Shutil](https://pymotw.com/3/shutil/)

The shutil module includes high-level file operations such as copying and archiving.

**Copying Files**

```copyfile()``` copies the contents of the source to the destination and raises IOError if it does not have permission to write to the destination file.

**Copying File Metadata**

By default when a new file is created under Unix, it receives permissions based on the umask of the current user. To copy the permissions from one file to another, use ```copymode()```.

**Working With Directory Trees**

shutil includes three functions for working with directory trees. To copy a directory from one place to another, use ```copytree()```. It recurses through the source directory tree, copying files to the destination. The destination directory must not exist in advance.

**Finding Files**

The ```which()``` function scans a search path looking for a named file. The typical use case is to find an executable program on the shell’s search path defined in the environment variable PATH.

**Archives**

Python’s standard library includes many modules for managing archive files such as tarfile and zipfile. There are also several higher-level functions for creating and extracting archives in shutil. ```get_archive_formats()``` returns a sequence of names and descriptions for formats supported on the current system.

**File System Space**

It can be useful to examine the local file system to see how much space is available before performing a long running operation that may exhaust that space. ```disk_usage()``` returns a tuple with the total space, the amount currently being used, and the amount remaining free.
