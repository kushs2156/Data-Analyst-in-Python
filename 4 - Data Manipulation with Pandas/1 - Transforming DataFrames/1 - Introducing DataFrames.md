pandas is a Python package for data manipulation. It can also be used for data visualisation; we'll get to that in Chapter 4. We'll start by talking about DataFrames, which form the core of pandas. In chapter 2, we'll discuss aggregating data to gather insights. In chapter 3, you'll learn all about slicing and indexing to subset DataFrames. Finally, you'll visualise your data, deal with missing data, and read data into a DataFrame. Let's dive in.
## pandas is built on NumPy and Matplotlib
pandas is built on top of two essential Python packages, NumPy and Matplotlib. NumPy provides multidimensional array objects for easy data manipulation that pandas uses to store data, and Matplotlib has powerful data visualisation capabilities that pandas takes advantage of. pandas has millions of users, with PyPi recording about 14 million downloads in December 2019.
## Rectangular data
There are several ways to store data for analysis, but rectangular data, sometimes called "tabular data" is the most common form. In this example, with dogs, each observation, or each dog, is a row, and each variable, or each dog property, is a column. pandas is designed to work with rectangular data like this. In pandas, rectangular data is represented as a DataFrame object. Every programming language used for data analysis has something similar to this. R also has DataFrames, while SQL has database tables. Every value within a column has the same data type, either text or numeric, but different columns can contain different data types.
## Exploring a DataFrame
When you first receive a new dataset, you want to quickly explore it and get a sense of its contents. pandas has several methods for this. The first is ==`head()`==, which returns the first few rows of the DataFrame. We only had seven rows to begin with, so it's not super exciting, but this becomes very useful if you have many rows.

The ==`info()`== method displays the names of columns, the data types they contain, and whether they have any missing values.

A DataFrame's ==`shape`== attribute contains a tuple that holds the number of rows followed by the number of columns. Since this is an attribute instead of a method, you write it without parentheses.

The ==`describe()`== method computes some summary statistics for numerical columns, like mean and median. "count" is the number of non-missing values in each column. describe is good for a quick overview of numeric variables, but if you want more control, you'll see how to perform more specific calculations later in the course.
## Components of a DataFrame
DataFrames consist of three different components, accessible using attributes. The ==`values`== attribute, as you might expect, contains the data values in a 2-dimensional NumPy array.

The other two components of a DataFrame are labels for columns and rows. The ==`columns`== attribute contains column names, and the ==`index`== attribute contains row numbers or row names. Be careful, since row labels are stored in dot-index, not in dot-rows. Notice that these are Index objects, which we'll cover in Chapter 3. This allows for flexibility in labels. For example, the dogs data uses row numbers, but row names are also possible.
## pandas Philosophy
Python has a semi-official philosophy on how to write good code called The Zen of Python. One suggestion is that given a programming problem, there should only be one obvious solution. As you go through this course, bear in mind that pandas deliberately doesn't follow this philosophy. Instead, there are often multiple ways to solve a problem, leaving you to choose the best. In this respect, pandas is like a Swiss Army Knife, giving you a variety of tools, making it incredibly powerful, but more difficult to learn. In this course, we aim for a more streamlined approach to pandas, only covering the most important ways of doing things.
## Let's practice!
Enough meditating, time to write some code!