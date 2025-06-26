+++
title = "California Data Energy 2022"
subtitle = "Data Source: US State Energy Data System "
authors = ["Danielle Louie"]
date = "2025-05-14"
categories = ["Python", "Sketchingpy"]
description = "Observe the following data pertaining to California in 2022: Total Energy Consumption by Sector, Average Energy Prices by Sector, Renewable Energy Consumption, Petroleum and Natural Gas Consumption, Total Energy Consumption, Real GDP, and Energy Consumption per Real GDP."
+++

---

# Outline
1. [Overview](#overview)
2. [Design Process](#design-process)
3. [Takeaways](#takeaways)

---
# Overview {#overview}
The goal of this final project was to visualize at least 6 variables in the dataset of our choosing. I used the <a href="https://www.eia.gov/state/seds/" target="_blank" rel="noopener noreferrer">US State Energy Data System</a> and focused specifically on energy data for California in 2022. The following page dives into the design process for my final visualization.

![final project gif](/images/stat_198/Final_Project.gif)

# Design Process {#design-process}
Starting with the very left, the visualization displays a bar chart, with the upper bar chart depicting the **Total Energy Consumption by Sector** and the bottom depicting **Average Energy Prices by Sector**. I intentially chose to make the lower bars a slightly darker shade to show that the bar charts are depicting two pieces of information for the same sector (identified by the hue). The upper and lower y-axis are also scaled to the data they represent: the upper y-axis has the units billion BTU (British Thermal Unit) while the lower y-axis depicts American Dollars per million BTU. From the visualization, we can observe that *Transportation* consumes the most energy while having the second lowest average price out of the four sectors.

In the upper middle, I created a radar chart to show California's **Renewable Energy Consumption** in billion BTU. Surprisingly, California consumed a significantly greater amount of biofuel compared to the other four types: solar, wind, hydripower, and geothermal. I decided to use a radar chart because it helped to effectively portray the difference scales of consumption in a limited amount of space. I also chose to use green for the data points to tie in the concept that this chart was showing green energy.

The line graph depicts the trend in **Petroleum and Natural Gas Consumption** in million BTU from 1960 to 2022. The line graph shows a slight spike around the 1970s and 1980s, and then both fossil fuel sources begin to decrease steadily. 

Finally, on the very right, an interactive, ranked bar chart shows California's standing in three unique categories: **Total Energy Consumption**, **Real GDP**, and **Energy Consumption per Real GDP**.

# Takeaways {#takeaways}


---

# Acknowledgements
This project was conducted during the 2025 Spring Semester of STAT198 at UC Berkeley through the College of Computing, Data Science, and Society. Special shout out to <a href="https://gleap.org/" target ="_blank" rel="noopener noreferrer">Sam Pottinger</a> for sharing his love for creativity and informative science through data visualizations! Feel free to browse through the <a href="https://interactivedatascience.courses/" target="_blank" rel="noopener no referrer">course website</a>. Feel free to check out another one of my creations for this course at this page or browse through my <a href="https://github.com/danilouie/stat-198" target="_blank" rel="noopener noreferrer">GitHub repository</a>!. 

---