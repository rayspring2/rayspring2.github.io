---
title: "Networked Soccer Stars Game"
weight: 2
#date: 2023-02-01
tags: ["python","pygame ","cpp", "server"]
author: ["By: Rayhaneh Einollahi"]
description: "A Soccer Stars-inspired game written in Python, featuring multiplayer support via a C++ server" 
summary: "A Soccer Stars-inspired game written in Python, featuring multiplayer support via a C++ server" 
cover:
  image: "image.jpg"
  alt: "image"
  relative: false
#editPost:
 #   URL: "https://doi.org/10.1073/pnas.1816454115"
 #   Text: "Other Journal Name"


---

A multiplayer version of **Soccer Stars** with a **C++ server** for networking and a **Python client** for gameplay.  
The server manages connections and synchronizes the game state, while each client handles rendering and player input.

---

## 🏗️ Project Structure
- **server/** → C++ code for the game server (handles connections, turns, and state updates).  
- **client/** → Python code (Pygame) for rendering the board, player input, and local game logic.  

---

## 🎮 Features
- Multiplayer over TCP sockets  
- Supports **2 or more players**  
- Centralized C++ server synchronizing game state  
- Python client with Pygame interface  
- Turn-based kicking mechanics  
- Real-time score updates

<p align="center">
  <img src="Soccer_Stars.gif" alt="Bottom Center GIF" width="700"/>
</p>

---
<a href="https://github.com/Rayhaneh-Einollahi/networked_Soccer_Stars" target="_blank" rel="noopener" 
   style="display:inline-block; padding:12px 24px; font-weight:bold; background-color:#24292e; 
          color:white; border-radius:8px; text-decoration:none; font-size:16px;">
  ⭐ Star on GitHub
</a>

---


