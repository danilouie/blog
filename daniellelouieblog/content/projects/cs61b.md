+++
title = "2D Tile-Based World Exploration Engine"
author = ["Danielle Louie", "Michelle Ngo"]
date = "2023-11-01"
tags = ["Java"]
+++

**Language:** Java   |   **Program:** IntelliJ   |   [Project 3 Git Link](https://github.com/danilouie/CS61B-Projects/tree/main/proj3) 
**Authors:** Danielle Louie, Michelle Ngo

---

# Overview

The objective of this project was to build an interactive "game" with randomly generated, explorable dungeon maps based on a 2D grid of tiles. You have probably come across games that use this map style, such as Pokémon, Fire Emblem, or Stardew Valley! These games typically use graphical tiles to create a more colorful and lively game experience, but for this project, my partner and I utilized text based tiles. 

## How it works

For this project, my partner and I developed a dynamic main menu with functionality for generating random dungeon maps based off of user-input seeds. We implemented features for loading saved maps and facilitating a seamless exit from the game. We also incorporated interactive keypress controls and mouse functionality for movement, toggling map tools, and information display, which enhanced user engagement and overall gameplay experience. 

## Game Play

The end-game condition is simple: water all the "grass" tiles into "flower" tiles to unlock the final door. Each map starts with 20 grass tiles and a "locked" door in randomly generated locations. The game ends once the all the grass tiles have grown into flowers, and the avatar travels onto the tile containing the now unlocked door.  

## Video Tutorial
Below is a short tutorial of an example game play. 

{{< video src="/video/cs61b_tutorial.mp4" >}}

## Coding Process

The first goal in this project was world generation. The main objective of the map was that it had to be able to generate random rooms and hallways (with no dead ends), with every element reachable for exploration. In addition, the explorable parts of the map had to take up The map generation was prompted by a seed that the user would input, and the same seed should be able to generate the same map.

![map example](/images/cs61b/map.png)

Once the dungeons consistently generating, the next step was to create a Main Menu. The Main Menu would present three options to the user at the beginning of the game:
- Creating a new world, which the user would then be prompted to provide a seed.
- Loading a previously saved game.
- Quitting the game immediately.

My partner and I found that this was the most difficult part of this second step. Tackling this problem required building a system that would continously draw the most recent map (if prompted to save), check if there was a previously saved world, and then if prompted in the Main Menu, would load the world exactly as it was last left.

![main menu](/images/cs61b/main_menu.png)

The last step was the most fun as it involved building interactivity between the user and the game. The main objectives were:
- Enabling movement of an avatar using "WASD" keyboard controls.
- Identification of tile type based on where the mouse was hovering.
- A clock that displayed the current date and time. 

Out of selection of multiple features to incorporate in this game, my partner and I chose two:
- Triggering lights to turn on based on keyboard controls (we used the letter "T").
- Narrowing or widening the user's view of the map around the avatar based on keyboard controls (we used the letter "G").

In addition, we coded the game to use the keyboard control, "Y", to allow the user to water grass tiles to flower tiles if the avatar was within 1 tile of the grass tiles. The counters for the grass and flowers at the middle, top of the game consistently reflected the game progress. 

![playable world](/images/cs61b/playable_map.png)

## Takeaways

For projects that are as extensive as this, a **Design Document** is an extremely helpful way to build a framework for different objectives and keep track of your current progress. Before diving headfirst into coding, my partner and I first detailed out each objective of our project, as well as the steps that we were planning to take to accomplish these tasks. We even created a checklist to help us easily identify our progress in the midst of the comprehensive planning. In addition to being a helpful guide for our project, the Design Document also served as an effective tool for communication. In order to ensure that we were both on the same page, we each assumed responsibility to consistently update the document, allowing the document to actively reflect our progress and keep the both of us on the same page about each other's work. It also proved to be beneficial for debugging purposes.     

---

# Acknowledgements
This project was conducted during the 2023 Fall Semester of CS61B at UC Berkeley through the College of Computing, Data Science, and Society. Feel free to browse through this <a href="https://fa23.datastructur.es/materials/proj/proj3/" target="_blank" rel="noopener noreferrer">website</a> for an in-depth scope of the project requirements. If you are interested in other projects that I have built for this course, feel free to browse this <a href="https://github.com/danilouie/CS61B-Projects" target="_blank" rel="noopener noreferrer">Git Repository</a>.
