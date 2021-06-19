# Data Analysis

## JupyterLab
- JupyterLab is a next-generation web-based user interface for Project Jupyter.

- JupyterLab enables you to work with documents and activities such as Jupyter notebooks, text editors, terminals, and custom components in a flexible, integrated, and extensible manner

- You can arrange multiple documents and activities side by side in the work area using tabs and splitters. Documents and activities integrate with each other, enabling new workflows for interactive computing

- JupyterLab also offers a unified model for viewing and handling data formats. JupyterLab understands many file formats (images, CSV, JSON, Markdown, PDF, Vega, Vega-Lite, etc.) and can also display rich kernel output in these formats

---

## Numpy

- `NumPy` : which stands for Numerical Python, is a library consisting of multidimensional array objects and a collection of routines for processing those arrays. Using NumPy, mathematical and logical operations on arrays can be performed.

- `NumPy` : is a commonly used Python data analysis package. By using NumPy, you can speed up your workflow, and interface with other packages in the Python ecosystem, like scikit-learn, that use NumPy under the hood. NumPy was originally developed in the mid 2000s, and arose from an even older package called Numeric. This longevity means that almost every data analysis or machine learning package for Python leverages NumPy in some way.

- Before using NumPy, we’ll first try to work with the data using Python and the csv package :

- Import the `csv` library.

- Open the `.csv` file.

- With the file open, create a new csv.reader object.

- etc...

- With NumPy, we can work with multidimensional arrays.we’ll focus on 2-dimensional arrays. A 2-dimensional array is also known as a matrix or ( list of lists). A matrix has rows and columns.By specifying a row number and a column number, we’re able to extract an element from a matrix.

- the core of NumPy is written in a programming language called C, which stores data differently than the Python data types. NumPy data types map between Python and C, allowing us to use NumPy arrays without any conversion hitches.

- NumPy has several different data types, the important ones are :

- `float` — numeric floating point data.

- `int` — integer data.

- `string` — character data.

- `object` — Python objects

- NumPy makes it simple to perform mathematical operations on arrays. This is one of the primary advantages of NumPy, and makes it quite easy to do computations.

- NumPy makes it possible to test to see if rows match certain values using mathematical comparison operations like `<, >, >=, <=, and ==`

- With NumPy, it’s very common to combine multiple arrays into a single unified array

**you can see the NumPy sheet cheat in this link : https://s3.amazonaws.com/dq-blog-files/numpy-cheat-sheet.pdf**
