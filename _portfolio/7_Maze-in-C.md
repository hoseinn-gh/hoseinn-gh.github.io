---
title: "Console-Based Maze Game in C"
excerpt: "A console-based maze game in C with user accounts, messaging, and a doubly linked-list game replay system."
collection: portfolio
---

A console-based maze game developed in C for the Basic Programming
course. Alongside the maze gameplay, the application includes user accounts,
saved game history, a messaging system, and game replay functionality.

## Game and Data Management

The game represents the maze using multiple layers to track the environment,
player position, and interactions with game objects. Every player move is
recorded in a doubly linked list, allowing completed games to be replayed by
traversing the recorded moves forwards or backwards.

User profiles, game saves, and messages are stored persistently in binary
files. The application implements searching and sorting for managing user and
message data, and uses a temporary-file update mechanism to safely modify
persistent records without directly overwriting the original data.

The project is organized into separate functions for the game, menus,
messaging, account management, and file operations, bringing the different
features together into a single interactive console application.

## [Source on GitHub](https://github.com/hoseinn-gh/C-Console-Maze-Game)
