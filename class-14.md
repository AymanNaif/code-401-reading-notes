# Data Visualization

## Matplotlib

- **matplotlib** is a Python package for 2D-graphics. It provides both a very quick way to visualize data from Python and publication-quality figures in many formats.

- **IPython and the pylab mode**

- **IPython** is an enhanced interactive Python shell that has lots of interesting features including named inputs and outputs, access to shell commands, improved debugging and much more. When we start it with the command line argument -pylab (--pylab since IPython version 0.12), it allows interactive matplotlib sessions that have Matlab/Mathematica-like functionality.

#### pyplot

- pyplot provides a convenient interface to the matplotlib object-oriented plotting library. It is modeled closely after Matlab(TM). Therefore, the majority of plotting commands in pyplot have Matlab(TM) analogs with similar arguments. Important commands are explained with interactive examples.

## Figures, Subplots, Axes and Ticks

- We can have more control over the display using **figure, subplot, and axes explicitly**. A **figure** in matplotlib means the whole window in the user interface. Within this figure there can be subplots. While **subplot** positions the plots in a regular grid, axes allows free placement within the figure. Both can be useful depending on your intention. When we call plot, matplotlib calls gca() to get the current axes and gca in turn calls gcf() to get the current figure. If there is none it calls figure() to make one, strictly speaking, to make a subplot(111). 

#### Figures

- A figure is the windows in the GUI that has "Figure #" as title. Figures are numbered starting from 1 as opposed to the normal Python way starting from 0. This is clearly MATLAB-style.

#### Subplots

- With subplot we can arrange plots in a regular grid. We need to specify the number of rows and columns and the number of the plot. 

[Matplotlib](https://github.com/rougier/matplotlib-tutorial#id4)
