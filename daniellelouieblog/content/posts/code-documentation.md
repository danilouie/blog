+++
authors = ["Danielle Louie", "Magali de Bruyn"]
title = "Code Documentation"
date = "2024-11-20"
description = "Write once, reuse often: How do you build sustainable code? What are the best practices for documenting code?"
tags = [
    "Documentation",
]
categories = [
    "Coding"
]
series = ["Tutorials"]
+++

---

## Outline
1. [Introduction](#introduction)
2. [What is Code Documentation](#what-is-code-doc)
    - [Why do we need documentation?](#why-code-doc)
3. [Types of Documentation](#types)
    - [Design Documents](#des-doc)
    - [README](#readme)
    - [Licensing](#license)
    - [Docstrings](#docstrings)
    - [Comments](#comments)
    - [TODO and FIXME](#todo-fixme)
    - [Type Hinting](#type-hinting)
    - [Naming Conventions](#naming)
    - [GitHub Versioning](#github-version)
    - [Configuration Files](#config)
4. [Object-Oriented Programming](#oop)
5. [Slideshow Link](#slideshow)
6. [Workshop](#workshop)

---

# Introduction {#introduction}
What is code documentation? Why do we need it? What are the best practices for strong code documentation?

Whether you are a seasoned programmer or just beginnining to learn how to code, coding documentation is a crucial skill to practice. The following tutorial breaks down the questions above and explores different techniques for effectively documentating code. View the complete slide deck at the bottom of this page.

# What is code documentation? {#what-is-code-doc}
Code documentation is the practice of writing out how code was built, the purpose of the code or product, how the code works, and how to interact with it. Essentially, an ideal code documentation explains the entire process from the creation of the code to its current utilization. It transforms code from a black box, where there are unclear explanations and unintuitive code, to a glass box, a project that is easy to follow along and understand.

### Why do we need documentation? {#why-code-doc}
Code documentation is **key** for collaboration, sharing code, and exchange of knowledge. Often, you will be working with people from different backgrounds and varying levels of programming experience. Having a well-documented code makes it easier for you to not only explain your thought process in creating your code, but it also gives a useful resource for your audience to reference, empowering their ability to enter the technical space. Some general types of documentation (and their uses) include:
- **Internal**: for developers within an organization
- **External**: for people outside an organization involved with the program/project/code
- **Low-Level**: within the source-code (where the code is written) and explains specific lines/parts 
    - Examples: comments, docstrings.
- **High-Level**: the overall picture, such as the code architecure or design principles
- **Walkthrough**: "guided tour" that identifies points of interest in the code. 
    -  Link between low-level and high-level documentation.

Code documentation also helps to make *you* a better coder. Often times, we may return to a piece of code that we had written months ago; it's highly unlikely that you completely remember your entire thought process when coding, which makes a well-written documentation a useful reminder for you. This practice can also help to keep your code cohesive as you build or revisit your code, preventing knowledge loss and technical debt.

# Types of Documentation {#types}
What are some techniques in documenting code?

### Design Documents {#des-doc}
Design documents are blueprints for code and are usually written before any actual coding. These planning documents, whether in the form of a written manual or a flowchart, contain information about the design process(es), workflow, and initial feedback for the creation of a product. Design documents are extremely useful to refer back to throughout the entire coding process, and are a good point of reference that should be continuously updated.

![Design doc](/images/code_doc/design_doc.png)

### README {#readme}
READMEs are like "recipes", where well-written ones typically contain these five components:
1. What the project does - usually written as a summary in paragraph form.
2. Why the project is useful - where the author of the code describes their goals and intended use for the code.
3. How users can get started with the project - a set of instructions on what to download/install. 
4. Where users can get help with your project - where to obtain these sources of data or software needed to run the code.
5. Who maintains and contributes to the project - all the people who worked on the project.
READMEs may also include liabilities and policies for using the code in the form of licences, contribution guidelines, and code of conducts. READMEs typically come in the form of markdown files, which is displayed as **README.MD**.

### Licensing {#license}
A license tells what people can or cannot do with your code. Similar to READMEs, they can come in the form of text files (.txt) or markdown files (.md). It is always good practice to have a license for your code so that permission to use (or not use) the code is explicitly stated. There are many licenses on the web, such as the MIT License, that are commonly used.

![Licensing](/images/code_doc/licensing.png)

### Docstrings {#docstrings}
Docstrings are usually found right after defining a function and describe the purpose of the function. A well-written docstring defines the parameters (input/arguments), returns (output), and an explanation of how the function works. In Python, docstrings are written with three pairs of double-quotes: """Docstring""".

![Docstrings](/images/code_doc/docstrings.png)

### Comments {#comments}
Comments are more informal than docstrings and are more like "annotations" within the source code. They are mainly used for debugging, modifications, questions, and reminders, and usually refer to a specific line or lines of code. When collaborating, comments can also be used to leave brief feedback. Comments are usually written in these two forms: #Comment, //Comment.

![Comments](/images/code_doc/comments.png)

### TODO and FIXME {#todo-fixme}
TODOs and FIXMEs are specified comments to indicate what needs to be done and what needs to be fixed. As defined by the names:
- TODOs are written to detail parts of code that need to be worked on eventually, such as adding features, cleaning up code, or refactoring code.
- FIXMEs are reminders of broken code that need to be fixed but not urgently.
TODOs and FIXMEs should **NOT** be present in stable code as they are used to indicate large portions of code that have to be altered. If there are only small parts of code that need to be fixed, it is better practice to write a quick comment.

### Type Hinting {#type-hinting}
Type hinting indicates the expected <a href="https://www.geeksforgeeks.org/data-types-in-programming/" target="_blank" rel="noopener noreferrer">data types</a> for function arguments and return values. This practice is extremely helpful for functions that have many arguments and outputs as it shows how data might be manipulated. Different coding languages have different requirements for type hinting. For instance, Java requires type hinting for all variables to run code whereas Python does not.

![Type hinting](/images/code_doc/type_hinting.png)

### Naming Conventions {#naming}
Having good naming conventions is important for organization of code. Properly naming files, variables, functions, classes, just to name a few examples, make it easier for you and collaborators to navigate through all components of a larger project. It is best practice to establish naming conventions beforehand to avoid confusion, and it is also helpful to document naming convention formats in documents such as READMEs.

![Naming conventions](/images/code_doc/naming_conventions.png)

### GitHub Versioning {#github-version}
In GitHub, leaving detailed commit messages or pull requests (PR) are useful for keeping track of progress while coding. 

Commit messages are key markers for specified points of progress, and they are especially significant when code needs to be reverted to a previous stage - therefore, having a detailed commit message is very important as it indicates the point of progress! 

![versioning1](/images/code_doc/versioning1.png)

Similarly, leaving messages for PR help collaborators to keep track of each other's work.

![versioning2](/images/code_doc/versioning2.png)

### Configuration Files {#config}
Configuration files control the technical components of a programs, such as where data is stored and what features are selected. Think of these files as what controls the "settings" of the program, or in more technical terms, the operating system. These files typically list the needed build and dependencies (external libraries, packages, etc.) needed in order to properly run a program or software. You can find configuration fiiles in the following formats: YAML, XML, JSON, requirements.txt.

# Object-Oriented Programming {#oop}
Object-oriented programming provides structure and legibility to code by grouping certain components together. Proper documentation makes it easier to work towards object-oriented programming because it makes it easier to see the data, functions, classes, and other parts of code that you are working with, as well as how each part interacts with one another. By having object-oriented code, debugging, reusability, and scalability become more accessible.

# Slideshow Link {#slideshow}
Here is the compiled slideshow used for the presentation! The link to the slide deck is <a href="https://docs.google.com/presentation/d/e/2PACX-1vRJLmoh3zjl1uBD4gLYsC_UOsagV2jxwoRuDMZPb6tb3FZpcaobpDeYLY-CSJQRBqAkmO36AwZrgmRM/pub?start=false&loop=false&delayms=3000" target="_blank" rel="noopener noreferrer">here</a>.

{{< slideshow "https://docs.google.com/presentation/d/e/2PACX-1vRJLmoh3zjl1uBD4gLYsC_UOsagV2jxwoRuDMZPb6tb3FZpcaobpDeYLY-CSJQRBqAkmO36AwZrgmRM/embed?start=false&loop=false&delayms=3000">}}

# Workshop {#workshop}
<a href="https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository" target="_blank" rel="noopener noreferrer">Clone</a> this <a href="https://github.com/danilouie/ecotech-documentation" target="_blank" rel="noopener noreferrer">GitHub repository</a> to add the workshop to your local machine. In the repository, you will find a script called **docuvent.py** - this script is filled with code that can be better documented! Work your way through this file, and once you feel satisfied, compare your answers to the **answer-key.py** file. Please note that your answers may differ, and there may be some things that you documented that were not captured in the answer key!

*Note: None of the scripts are expected to run. They are simply written to practice documentation.*

---

# Acknowledgements 
This presentation was given as part of the <a href="https://dse.berkeley.edu/news/ecotech-connect" target="_blank" rel="noopener noreferrer">EcoTech Connect Discussion Series</a> hosted by DSE at UC Berkeley.

---
