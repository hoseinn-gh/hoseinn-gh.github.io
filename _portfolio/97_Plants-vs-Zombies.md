---
title: "Networked Plants vs. Zombies Game"
excerpt: "Two-player game in C++ and Qt, built around a multithreaded TCP client-server."
collection: portfolio
---

A two-player online strategy game built in C++ and Qt, with a central TCP
server handling accounts, matchmaking, player state, and match coordination developed for Advanced Programming course.
The clients provide the GUI and real-time game logic, including unit placement,
movement, collision detection, attacks, projectiles, and animations.

## Architecture

The project uses a client-server architecture with JSON messages exchanged
over QTcpSocket. The server manages connections, accounts, the online-player
lobby, invitations, resource validation, and match results, while the clients
handle the graphical interface and real-time game logic.

Each connected client is handled by its own QThread, allowing the server to
handle multiple clients concurrently rather than being limited to a fixed
number of connections.

## Game Logic

The client uses an object-oriented hierarchy for plants and zombies, with
shared character properties and specialized subclasses for different unit
behaviour. Qt timers drive movement, attacks, projectiles, resource
generation, and the round timer, while collision detection handles
interactions between units.

Matches consist of two rounds, with players switching sides after the first
round. The server coordinates the match lifecycle and records the resulting
statistics and match history.

## [Source on GitHub](https://github.com/hoseinn-gh/plants-vs-zombies)
