+++
authors = ["Danielle Louie"]
title = "Working with DataFrames"
date = "2024-09-12"
description = "A beginner's guide to working with dataframes and commonly used functions."
tags = [
    "Pandas"
]
categories = [
    "Tutorial", "Python", "DataFrames"
]
series = ["Tutorials"]
+++

---

## Outline
1. [Introduction](#introduction)
2. [Reading a Dataframe](#read-df)
3. [Viewing Elements](#view)
    - [Head and Tail](#head-tail)
    - [iloc and loc](#iloc-loc)
    - [Data Types](#data-type)
4. [Creating Columns](#create-col)
5. 

---

# Introduction {#introduction}
Dataframes, data structures that are very similar to tables, are key elements in data science. They are extremely useful for organizing information, and many instances of data science use dataframes to clean and organize data, manipulate tabular data, and even to produce visualizations. The following tutorial aims to provide a basic overview of useful functions when working with dataframes.

It is completely normal to be googling functions and their usage, no matter what fluency you have in coding! There are so many methods towards the same solutions, so it is good practice to continously learn about all the coding possibilities, and then determining which ones you like best. I write this tutorial in hopes that I can compile some of the most common practices in one page and aid you in improving your coding efficiency! I will also link useful webpages if you are interested in learning more about any of the topics covered.


***<u>Notice</u>***
Before following this tutorial, make sure you have Python and a source code editor (such as VSCode or Atom) installed. If you do not have Python, you can look <a href="https://www.python.org/downloads/" target="_blank" rel="noopener noreferrer">here</a> for installation instructions. 

# Reading a Dataframe {#read-df}
Let's start our code by importing important **libraries**. Libraries contain prewritten code that serve as tools for tasks that coders often have to reuse. The most important one that we need to import will be Pandas. 

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt 
import seaborn as sns
```

Now, let's <a href="https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html" target="_blank" rel="noopener noreferrer">create a dataframe</a>. There are many ways to create a dataframe, as shown by the link above. However, arguably, many dataframes that you will be working with in class or in a job will be imported (usually as a .csv file); this is because dataframes are meant for working with large amounts of data, and coding a dataframe from scratch would be too tedious.

For this tutorial, I have created a <a href="https://github.com/danilouie/blog/blob/main/files/minecraft_wood.csv" target="_blank" rel="noopener noreferrer">downloadedable dataframe</a> for you to practice with! However, feel free to practice coding a simple dataframe if you want to try!

To open up the csv file as a dataframe in your source code editor, type:

```python
# df is the variable we are assigning the dataframe to in this example
# File path tells your computer where the csv is stored. 
df = pd.read_csv("FIlE PATH TO CSV")

# An example of how the filepath may look like
df = pd.read_csv("/Users/daniellelouie/Documents/minecraft_wood_.csv")

# Print out the a view of the dataframe
df
```

Make sure you change the filepath to wherever you stored the dataframe. For Mac users, an easy way to get your file path is to first locate it in your computer, right click on the document, press the "option" key, and click the option "Copy ___ as Pathname". If you are using Windows, you can click on the bar that may show something like "This PC > Documents...", and then copy the filepath revealed.

# Viewing Elements {#view}
As you may have noticed, there are a lot of rows in this dataframe, and simply typing out "df" only shows the first several and last several rows. The "..." indicates that there are rows not visible. 

![minecraft wood raw](/images/dataframe_tutorial/minecraft_block_df.png)

You can see the total number of rows and columns at the bottom of the dataframe. In this case, we have 61 rows and 2 columns. 

###### Head and Tail {#head-tail}
The function <a href="https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.head.html" target="_blank" rel="noopener noreferrer">head</a> shows us the first 5 rows by default.

```python
df.head()
```

On the other hand, the function <a href="https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.tail.html" target="_blank" rel="noopener noreferrer">tail</a> shows us the last 5 rows by default. 

```python
df.tail()
```

If we wanted to specify how many rows we wanted to see for either function, we just have to input the number of rows we want to see as an argument. For instance, let's say that we want to see the first 10 rows of the dataframe: 

```python
df.head(10)
```

Or, if we want to see the last 15 rows:

```python
df.tail(15)
```

###### iloc and loc {#iloc-loc}

We can also use the functions <a href="https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.iloc.html" target="_blank" rel="noopener noreferrer">iloc</a> and <a href="https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html" target="_blank" rel="noopener noreferrer">loc</a> to extract information from dataframes. These functions return the information we want as a **Series**, which is a one-dimensional array of data. 

The function **iloc** uses numerical indices to identify the row and column of the data we want to call. Let's see some examples. 

```python
# Print out the 1st row of the dataframe as a Series
# Remember that the indices starts from 0!
df.iloc[0]

# Print out the 37th row of the dataframe as a Series
df.loc[36]

# Print out the item in the 7th row and 1st column 
df.iloc[6, 0]

# Print out the item in the 28th row and 2nd column 
df.iloc[27, 1]
```

We can *splice* data by specifying the row and column indices we want. Splicing can return either a dataframe or a series.

```python
# Return up to (not including) the 8th row of the dataframe -> returns a dataframe
df.iloc[:8]

# Return up to (not including) the 8th row in the first column -> returns a series
df.iloc[:8, 0]

# Return up to (not including) the 2nd column of the dataframe -> returns a dataframe
df.iloc[:, :1]

# Return all rows in the first column -> returns a series
df.iloc[:, 0]
```

We can also generate the same outcomes using **loc**. The main difference is the **loc** uses the names of columns as an argument instead of their indices; it still uses indices for rows. Let's see how we would write the code above using **loc** instead. 

```python
# Print out the 1st row of the dataframe as a Series
df.loc[0]

# Print out the 37th row of the dataframe as a Series
df.loc[36]

# Print out the item in the 7th row and 1st column 
df.iloc[6, 'Name']

# Print out the item in the 28th row and 2nd column
```

We can also splice data with **loc**!

```python
# Return up to (not including) the 8th row of the dataframe -> returns a dataframe
df.iloc[:8]

# Return up to (not including) the 8th row in the first column -> returns a series
df.iloc[:8, 'Name']

# Return up to (not including) the 2nd column of the dataframe -> returns a dataframe
df.loc[:, ['Name']]

# Return all rows in the first column -> returns a series
df.iloc[:, 'Name']
```

Ultimately, it comes down to personal preference for which one you want to use. Sometimes, it may be more intuitive to use indices, while other times, we may remember the column names better - there is no right or wrong choice!


##### Data Types {#data-type}
Dataframes can contain many different <a href="https://www.geeksforgeeks.org/python-data-types/" target="_blank" rel="noopener noreferrer">data types</a> such as **strings**, **integers**,  **floats** or **booleans**. In short, **strings** are sequences of characters, like a word, phrase, or sentence; **integers** are numbers without decimal points; **floats** are numbers with decimal points; **booleans** are binary depictions of True or False values, usually depicted with 1 (True) and 0 (False).

To see what kind of data type our dataframe contains, we can use a function called **type()**.

```python
# Determine the type of data in the first column by extracting one object
type(df.iloc[0][0])
```

Running the above code should result in an output "str", which indicates that the datatype we observed is a string! Since our dataframe does not contain any other datatypes, let's practice using this function with simple data. 

```python
# The following code should print out "int" for "integer"
type(1)

# The following code should print out "float" 
type(3.14)

# The following code should print out "bool" for "boolean"
type(False)
```

# Creating Columns {#create-col}
Let's take a look at our data table again. That's quite a lot of different types of wooden minecraft blocks! What if we want to look at the specific type of wood that each block is made of?

We can create a new column in the dataframe that extracts the our wanted data (the specific type of wood) from the first column.  
