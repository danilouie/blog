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
---

# Introduction {#introduction}
This short tutorial focuses on how to add checkboxes into visualizations and build user-interactivity. The goal of this tutorial is to provide you with guidance on how to build a plot that can update data in real-time based on user-input through checkboxes. 

Before following along this tutorial, make sure you have Python installed. If you do not have Python downloaded, you can look <a href="https://www.python.org/downloads/" target="_blank" rel="noopener noreferrer">here</a> and determine the version you need. 

# Library Imports {#library-imports}
To begin writing out our code, let's first import some important libraries. Feel free to type it out yourself, or copy the code down below.

```python
import pandas as pd
import matplotlib.pyplot as plt 
import seaborn as sns
import ipywidgets as widgets
```

```python
def hello_world():
    print("Hello, World!")
```