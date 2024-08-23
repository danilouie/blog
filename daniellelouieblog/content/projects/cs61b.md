+++
title = "2D Tile-Based World Exploration Engine"
author = ["Danielle Louie", "Michelle Ngo"]
date = "2023-11-01"
tags = ["Java"]
+++

**Language Used:** Java   |   [Project 3 Git Link](https://github.com/danilouie/CS61B-Projects/tree/main/proj3)

## Overview

The objective of this project was to build an interactive "game" with randomly generated, explorable dungeon maps based on a 2D grid of tiles. You have probably come across games that use this map style, such as Pokémon, Fire Emblem, or Stardew Valley! These games typically use graphical tiles to create a more colorful and lively game experience, but for this project, my partner and I utilized text based tiles. 

## How it works

For this project, my partner and I developed a dynamic main menu with functionality for generating random dungeon maps based off of user-input seeds. We implemented features for loading saved maps and facilitating a seamless exit from the game. We also incorporated interactive keypress controls and mouse functionality for movement, toggling map tools, and information display, which enhanced user engagement and overall gameplay experience. 

## Game Play

The end-game condition is simple: water all the "grass" tiles into "flower" tiles to unlock the final door. Each map starts with 20 grass tiles and a "locked" door in randomly generated locations. The game ends once the all the grass tiles have grown into flowers, and the avatar travels onto the tile containing the now unlocked door.  

## Video Tutorial
Below is a short tutorial of an example game play. 

{{< video src="/video/cs61b_tutorial.mp4" >}}

## Acknowledgements
This project was conducted during the 2023 Fall Semester of CS61b at UC Berkeley. Feel free to browse through this [website](https://fa23.datastructur.es/materials/proj/proj3/) for an in-depth explanation of the project requirements. If you are interested in other projects that I have built for this course, feel free to browse this [Git Repository](https://github.com/danilouie/CS61B-Projects).


Instructions for how to render image [here](https://werat.dev/blog/automatic-image-size-attributes-in-hugo/)
