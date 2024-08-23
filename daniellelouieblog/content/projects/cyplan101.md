+++
title = "Flood Risk in Houston"
author = ["Danielle Louie", "Kobe Bilstad"]
date = "2024-06-17"
tags = ["Java"]
+++

**Language:** R   |   **Program:** RStudio, Carto
**Authors:** Danielle Louie, Kobe Bilstad

Visit the <a href="https://github.com/danilouie/CS61B-Projects/tree/main/proj3" target="_blank" rel="noopener noreferrer">GitHub profile</a> for more details.

# Abstract
As climate change increases the intensity of storms, cities must improve their urban infrastructure to adapt to severe environmental disasters. The present study investigated six factors in Houston’s urban design to understand the city’s vulnerability to flooding: precipitation patterns, storm sewer systems, pavements, land use, topography, and socioeconomic demographics. When comparing the findings for each factor, we found that low-income Hispanic, White, and African American communities were more likely to face flood risks; these communities had higher numbers living in industrial and commercial regions along the coast, which are prone to severe flooding but face ineffective storm drainage due to prominent infrastructure made from impervious surfaces (concrete, asphalt, etc.). In addition, low-income communities live in neighborhoods that lack proper storm sewer drainage systems, exacerbating flash floods and dangerous flood points. We recommend that Houston improve its urban design equitably to decrease flood vulnerability and ensure the city's sustainability in the future. 

---

## Introduction
Similar to many other low-lying municipalities in the United States, the city of Houston, Texas has encountered significant flood risk for much of its history. However, these concerns were substantially heightened following the impact of Hurricane Harvey in August of 2017. The category four storm had brought tremendous amounts of precipitation and damage to southeastern Texas, especially the Houston metropolitan area. In the aftermath, large portions of the city experienced severe flooding that impacted residential areas and transportation infrastructure for multiple weeks. 
We aim to establish a potential link between the flooding caused by Hurricane Harvey and the role of infrastructure and urban design in exacerbating the effects of climate change. Specifically, we attempt to identify factors governing Houston’s flood risk including but not limited to: precipitation patterns, pavement and road conditions, efficiency of drainage systems, topography, land use, and geographic distribution of household income. In efforts to combine these factors together, we analyze how the city of Houston could not only be severely impacted by future events such as the 2017 floods, but also how vulnerability to natural disasters may drive economic and social inequality from an urban planning perspective. 

Our motivation for researching this topic comes from the varied nature of this issue — in other words, its pertinence to climate science, urban data analytics, and social justice. By understanding the lessons from Hurricane Harvey and its effect on Houston city planning, we hope to inform future infrastructure planning efforts that prioritize both economic growth and environmental sustainability, ensuring that cities like Houston are better prepared to face the challenges of climate change and extreme weather.

## Literature Review
After Hurricane Harvey devastated Houston, a growing amount of attention was directed toward flood statistics. Different types of floods that struck the city were analyzed, and Houston and Harris County began to acknowledge the city’s weaknesses — including climate change, funding, and warning systems (Blackburn & Baker, 2023). The city government began establishing flood mitigation policies and supporting the construction of a new reservoir to increase preparedness against future storms (University of Houston, 2022). Environmental injustice was also brought to attention as several studies conducted found that people of color, people with disabilities, and people with existing health issues were disproportionately impacted by the hurricane (Flores et al., (2020). Studies analyzed the recovery rate of Houstonians to observe the varied recovery rates in different neighborhoods; five years after Hurricane Harvey, 81.6% of survey respondents were either completely or mostly recovered, leaving 29.4% of the respondents still struggling (Strong, 2022).  

Furthermore, the destruction left in the wake of the cyclone had raised serious infrastructure concerns for the city of Houston to withstand future storms. The inundation of major interstate freeways and record water levels prompted investigations by the Infrastructure Resilience Division (IRD) and the American Society of Civil Engineers (ASCE) to document the lack of flood resilience of infrastructure with respect to heavy rainfall events (Mostafavi et al., 2022). The total estimated cost of damages caused by the storm hovers at around $125 billion, tied with Hurricane Katrina as the most expensive natural disaster in US history (Mooney, 2018). Despite this hefty price tag, Houston has seen almost no major infrastructure projects constructed in response to Hurricane Harvey (Fulton, 2022). This leaves ample room for discussion about contributing factors and urban planning solutions for Houston with respect to flood prevention.

## Methods
To conduct holistic research about Houston’s flood vulnerability, we analyzed six urban components in Houston to understand the reasons behind its proneness to flooding and to examine the interplay between various contributing factors, highlighting the unsustainability of Houston's infrastructure in managing flood risks.
1. ***Precipitation***: precipitation patterns were examined for Houston across multiple years to examine how rainfall in 2017 compared to other years. In the context of flooding, our group specifically looked at spikes in weather data graphs that indicate storms or major rainfall events.
2. ***Storm sewer systems***: using GIS software, we mapped out the main flood points, storm sewer systems, and floodways to evaluate the effectiveness of Houston’s drainage infrastructure. 
Pavements: with relevance to Houston’s high concentration of impervious surfaces, the quality of pavement was assessed using the Pavement Conditions Index (PCI). We then created a distribution of Houston’s roads based on their PCI scores to determine overall pavement quality for the metropolitan area. 
3. ***Income demographics***: mean and median incomes from the American Community Survey (ACS) for Harris County census tracts (2017) are displayed and accompanied by separate visualizations that are filtered by race and ethnic group. 
4. ***Topography & elevation***: data pulled from USGS (US Geological Survey) was used to generate a detailed elevation contour map of Houston as well as the surrounding suburbs. 
5. ***Land use***: polygons representing land use data, provided by the City of Houston, have also been mapped and grouped into ten different categories based on their general purpose. We also provide an overlay of the topography and land use maps using Carto GIS software. 

The data and findings for these six sources are discussed in detail in the subsequent ‘Results’ section. One key feature of our methods is that much of the data has been compiled and visualized in order to highlight noteworthy patterns; however, we concede that there are potentially other factors that may not be included in this analysis as well. 

## Results
*<u>Precipitation</u>*
To understand the influence of weather on floods in Houston, we analyzed daily precipitation patterns from 2017 to 2023 and calculated the mean amount in inches for each year. 



