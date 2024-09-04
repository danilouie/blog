+++
authors = ["Danielle Louie"]
title = "Interactive Visualizations: Checkboxes"
date = "2024-08-26"
description = "This post contains a short tutorial on how to add interactive checkboxes into your visualization!"
tags = [
    "Pandas", "Interactivity", "Checkboxes"
]
categories = [
    "Tutorial", "Python", "Visualizations"
]
series = ["Tutorials"]
+++

## Outline
1. [Introduction](#introduction)
2. [Library Imports](#library-imports)
3. [Example DataFrame](#ex-df)
4. [Initiating Interactivity](#initiate)
5. [Updating the Plot](#update-plot)
6. [Creating the Plot](#create-plot)
---

# Introduction {#introduction}
This short tutorial focuses on how to add checkboxes into visualizations and build user-interactivity using ipywidgets. The goal of this tutorial is to provide you with guidance on how to build a plot that can update data in real-time based on user-input through checkboxes. 

Before following along this tutorial, make sure you have Python installed. If you do not have Python downloaded, you can look <a href="https://www.python.org/downloads/" target="_blank" rel="noopener noreferrer">here</a> and determine the version you need. 

# Library Imports {#library-imports}
To begin writing out our code, let's first import some important libraries: pandas, matplotlib, seaborn, and ipywidgets. You have likely seen the first four to code and create visualizations in Python or Jupyter Notebooks. The last one, **ipywidgets**, is what will help us to build interactivity.
Feel free to type it out yourself, or copy the code down below.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt 
import seaborn as sns
import ipywidgets as widgets
```

# Example DataFrame {#ex-df}
Let's create an example DataFrame for our visualization. Checkboxes especially helpful for large DataFrames that contain a lot of categories. With interactive checkboxes, we can improve the visibility of our plot by controlling the amount of data that we see (based on their categories); we can also select different data to visualize comparisons for analysis. You may use the example DataFrame I created below, build your own, or implement it to your existing code. 

```python
# Example DataFrame with Bird Species
bird_species = ['Eagle', 'Parrot', 'Owl', 'Penguin', 'Swan']
random_birds = np.random.choice(bird_species, 100)
df = pd.DataFrame(random_birds, columns=['Bird Species'])
df
```
# Initiating Interactivity {#initiate}
Next, let's write dive into the main part of this tutorial: building interactivity. 

Let's first initiate the plot interactivity with:

```python
# Initiate interactivity
plt.ion()
```

In order to show both our plot and checkboxes, let's create two widgets. Let's call the widget for the plot "output", and the widget for the checkbox "checkbox". Replace **df['Bird Species']** with the column of your DataFrame that you would like your plot to categorize.

```python
# Create an output widget to capture the plot output
output = widgets.Output()

# Create a checkbox for each species
checkboxes = [widgets.Checkbox(value=True, description=boxes, indent=False) for boxes in sorted(df['Bird Species'].unique())]
```

# Updating the Plot {#update-plot}
Next, we're going to create **function** that allows us to update the plot in real-time based on user input. For this tutorial, I will be creating a countplot, so I'll name my function **update_countplot**. 

```python
# Define the update function
def update_countplot(*args):
```
We want the function to take in the 'args' parameter because we want the function to accept an arbitrary number of positional arguments. When handling widget events, such as checkbox changes, the user may pass additional arguments that are not necessarily sed by the plot. With 'args' as the argument passed into the function, we can ensure that the function will be able to handle the additional arguments without running into an error.


Now, in order for the plot to update with each user input, we need to first clear the previous plot. Let's also set the figure dimensions to esnure clarity and ease of visibility for our plot. 

```python
def update_countplot(*args)
    with output:
        # Clear the previous plot
        output.clear_output(wait=True) 
        # Create a figure and axes for plotting each time 
        fig, ax = plt.subplots(figsize=(20, 12))
```

Next, we want to make sure that the plot only shows the checkboxes that the user has selected. In that case, the function should check through all the boxes, and then output a filtered DataFrame that only contains the categories that reflect the boxes the user checked. If you are creating your own variables, make sure that you do not accidentally reassign variables that were used prior!

```python
def update_countplot(*args)
    with output:
        # Clear the previous plot
        output.clear_output(wait=True) 
        # Create a figure and axes for plotting each time 
        fig, ax = plt.subplots(figsize=(20, 12))
        # Filter data based on selected species
        selected_box = [cb.description for cb in checkboxes if cb.value]
        filtered_df = df[df['Bird Species'].isin(selected_box)]
```

# Creating the Plot {#create-plot}
Our next steps are to create the plot within the function we created above. We cannot write the plot outside the function because it would not properly update with respect to user input. This concept is similar to defining a variable after we have already run the function, rendering it useless. 

As mentioned above, I will be creating a countplot to represent my data. The code to create the countplot is probably one that you have seen many times, but let's take a refresher! I will be using seaborn, with the palette 'Paired', but feel free to use matplotlib and whatever palette you are more comfortable with.

```python
plot = sns.countplot(ax=ax, data=filtered_df, x='Bird Species', palette='Paired')
```

I'll also be including some code to clean up our plot. This includes adding labels for the axes, adding a title, and formatting the labels so they are legible. Remember, it is always good practice to include these details in your graph - it helps readers understand the information you are trying to portray through a single visualization!

```python
# Graph details
plt.xlabel('Bird Species', fontsize=20, weight='bold', labelpad=20)
plt.ylabel('Count', fontsize=20, weight='bold', labelpad=20)
plt.title('Bird Species Count', fontsize = 35, weight='bold')    
plt.xticks(rotation=90)
```

Lastly, we want to show our plot!

```python
plt.show()
```

Altogether, our update function should look like this: 

```python
# Define the update function
def update_countplot(*args):
    with output:
        # Clear the previous plot
        output.clear_output(wait=True) 
        # Create a figure and axes for plotting each time 
        fig, ax = plt.subplots(figsize=(20, 12))
        # Filter data based on selected species
        selected_box = [cb.description for cb in checkboxes if cb.value]
        filtered_df = df[df['Bird Species'].isin(selected_box)]

        # Plot 
        plot = sns.countplot(ax=ax, data=filtered_df, x='Bird Species', palette='Paired')
            
        # Graph details
        plt.xlabel('Bird Species', fontsize=20, weight='bold', labelpad=20)
        plt.ylabel('Count', fontsize=20, weight='bold', labelpad=20)
        plt.title('Bird Species Count', fontsize = 35, weight='bold')    
        plt.xticks(rotation=90)
        plt.show()
```

Double-check your indentations and code format!