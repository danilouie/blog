+++
authors = ["Danielle Louie"]
title = "Interactive Visualizations: Checkboxes"
date = "2024-08-26"
description = "This post contains a short tutorial on how to add interactive checkboxes into your visualization!"
tags = [
    "Pandas", "Interactivity", "Checkboxes"
]
categories = [
    "Tutorial", "Python", "Visualizations", "Coding"
]
series = ["Tutorials"]
+++

---

## Outline
1. [Introduction](#introduction)
2. [Library Imports](#library-imports)
3. [Example DataFrame](#ex-df)
4. [Initiating Interactivity](#initiate)
5. [Updating the Plot](#update-plot)
6. [Creating the Plot](#create-plot)
7. [Displaying the Widgets](#display)
8. [Final Visualization](#final-viz)
9. [Complete Code](#complete-code)
10. [Takeaways](#takeaways)
---

# Introduction {#introduction}
Welcome to my tutorial series on building interactive visualizations! This series was inspired by my own experiences, and I wanted to be able to compile my knowledge in a shareable platform as a means to continue educating myself and provide an accessible resource for others. 

This short tutorial focuses on how to add checkboxes into visualizations and build user-interactivity using ipywidgets. The goal of this tutorial is to provide you with guidance on how to build a plot that can update data in real-time based on user-input through checkboxes.

***<u>Notice</u>***
Before following along this tutorial, make sure you have Python and a source code editor (such as VSCode or Atom) installed. If you do not have Python, you can look <a href="https://www.python.org/downloads/" target="_blank" rel="noopener noreferrer">here</a> for installation instructions. I also recommend that you have a basic understanding of Python as this tutorial does not cover fundamentals for how to code.

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
Let's create an example DataFrame for our visualization. Checkboxes are especially helpful for large DataFrames that contain a lot of categories. With interactive checkboxes, we can improve the visibility of our plot by controlling the amount of data that we see (based on their categories); we can also select different data to visualize comparisons for analysis. You may use the example DataFrame I created below, build your own, or implement it to your existing code. 

```python
# Example DataFrame with Bird Species
bird_species = ['Eagle', 'Parrot', 'Owl', 'Penguin', 'Swan']
random_birds = np.random.choice(bird_species, 100)
df = pd.DataFrame(random_birds, columns=['Bird Species'])
df
```
# Initiating Interactivity {#initiate}
Next, let's write dive into the main part of this tutorial: building interactivity. 

Let's first initiate the plot interactivity in a new code cell with:

```python
# Initiate interactivity
plt.ion()
```

In order to show both our plot and checkboxes, let's create two widgets. Let's call the widget for the plot "output", and the widget for the checkbox "checkbox". Replace **df['Bird Species']** with the column of your DataFrame that you would like your plot to categorize.

```python
# Initiate interactivity
plt.ion()

# Create an output widget to capture the plot output
output = widgets.Output()

# Create a checkbox for each species
checkboxes = [widgets.Checkbox(value=True, description=boxes, indent=False) for boxes in sorted(df['Bird Species'].unique())]
```

# Updating the Plot {#update-plot}
Next, we're going to create a **function** that allows us to update the plot in real-time based on user input. For this tutorial, I will be creating a countplot, so I'll name my function **update_countplot**. I recommend creating a new code cell for this function.

```python
# Define the update function
def update_countplot(*args):
```
We want the function to take in the 'args' parameter because we want the function to accept an arbitrary number of positional arguments. When handling widget events, such as checkbox changes, the user may pass additional arguments that are not necessarily sed by the plot. With 'args' as the argument passed into the function, we can ensure that the function will be able to handle the additional arguments without running into an error.


Now, in order for the plot to update with each user input (aka, plotting new data), we need to be able to clear whatever the previous plot was. Let's also set the figure dimensions to ensure clarity and ease of visibility for our plot. 

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

Lastly, we want to show our plot.

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

# Displaying the Widgets {#display}
Our last steps are to make sure that our checkboxes are linked to our update function, and that our widgets are properly shown. Let's handle these tasks one by one. 

First, let's link the checkboxes to our update function. This ensures that however the user interacts with the checkboxes (checking or unchecking boxes) is accurately represented by the data portrayed in our plot. In a new code cell, implement the code below.

```python
# Link checkboxes to the update function
for cb in checkboxes: 
    cb.observe(update_countplot, 'value')
```

Widgets are like containers of data. We want to make sure that all of our checkboxes are neatly shown vertically in a widget. In the code below, I add some formatting to adjust the container to best fit my figure size. I recommend playing around with the formatting to see what each argument affects (length, width, spacing, etc.). Don't worry if the number of checkboxes visually exceeds your figure size. The widgets library automatically implements a scroll bar so the user has access to all of the data. 

```python
# Group checkboxes in a vertical box
checkboxes_container = widgets.VBox(children=checkboxes, layout=widgets.Layout(overflow='auto', height='650px', width='auto', margin='20px 0 0 30px'))
``` 

Ideally, I would like the checkboxes to be placed to the right of my countplot. To do this, I will organize my "output" widget (which contains my countplot), and my "checkboxes" widget side-by-side in a giant widget box. 

```python
# Use HBox to place the output widget and checkboxes side by side
ui = widgets.HBox([output, checkboxes_container])
```

Altogether, this code cell should look like: 

```python
# Link checkboxes to the update function
for cb in checkboxes: 
    cb.observe(update_countplot, 'value')

# Group checkboxes in a vertical box
checkboxes_container = widgets.VBox(children=checkboxes, layout=widgets.Layout(overflow='auto', height='650px', width='auto', margin='20px 0 0 30px'))

# Use HBox to place the output widget and checkboxes side by side
ui = widgets.HBox([output, checkboxes_container])
```

Finally, let's display all of our hard work! Simply create a new code cell and write: 

```python
# Display the UI
display(ui)

# Update the countplot on each input/run
update_countplot()
```

# Final Visualization {#final-viz}
Once you run all the code, you should be able to produce and interact with a bar graph as demonstrated by the video below.

{{< video src="/video/cb_tutorial.mp4" >}}

# Complete Code {#complete-code}
Below shows all the code separated into different code cells by my recommendation.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt 
import seaborn as sns
import ipywidgets as widgets
```
```python
# Example DataFrame with Bird Species
bird_species = ['Eagle', 'Parrot', 'Owl', 'Penguin', 'Swan']
random_birds = np.random.choice(bird_species, 100)
df = pd.DataFrame(random_birds, columns=['Bird Species'])
df
```
```python
# Initiate interactivity
plt.ion()

# Create an output widget to capture the plot output
output = widgets.Output()

# Create a checkbox for each species
checkboxes = [widgets.Checkbox(value=True, description=boxes, indent=False) for boxes in sorted(df['Bird Species'].unique())]
```

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
        plot = sns.countplot(ax=ax, data=filtered_df, x='Bird Species', palette='Paired', hue="Bird Species")
            
        # Graph details
        plt.xlabel('Bird Species', fontsize=20, weight='bold', labelpad=20)
        plt.ylabel('Count', fontsize=20, weight='bold', labelpad=20)
        plt.title('Bird Species Count', fontsize = 35, weight='bold')    
        plt.xticks(rotation=90)
        plt.show()
```
```python
# Link checkboxes to the update function
for cb in checkboxes: 
    cb.observe(update_countplot, 'value')

# Group checkboxes in a vertical box
checkboxes_container = widgets.VBox(children=checkboxes, layout=widgets.Layout(overflow='auto', height='650px', width='auto', margin='20px 0 0 30px'))

# Use HBox to place the output widget and checkboxes side by side
ui = widgets.HBox([output, checkboxes_container])
```
```python
# Display the UI
display(ui)

# Update the countplot on each input/run
update_countplot()
```

# Takeaways {#takeaways}
Congratulations! You have created a fully functioning interactive visualization with checkboxes. Feel free to tinker around with the code to see what other customizations you can add. There are many resources that include the variety of widget interactions that can be implemented with ipywidgets, such as this link <a href="https://ipywidgets.readthedocs.io/en/latest/examples/Widget%20List.html" target="_blank" rel="noopener noreferrer">here</a>, so I recommend browsing through them and experimenting!

---

