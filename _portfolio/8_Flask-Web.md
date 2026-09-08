---
title: "Simple Flask Web Application"
excerpt: "Role-based web application in Python and Flask with session management and RESTful endpoints."
collection: portfolio
---

A web application developed in Python and Flask for a Computer Networks course.
It provides user registration and authentication, separate dashboards for
administrators and regular users, and a simple system for submitting and
displaying posts.

## Authentication and Access Control

The application implements role-based access control and cookie-based session
management, including a "Remember Me" option. Access to administrative pages
is restricted based on the user's role, while session expiration is handled
when users log out.

Failed login attempts are tracked by IP address, with excessive attempts
blocked to provide basic protection against brute-force attacks.

## Web Interface and API

The application follows a RESTful structure, using appropriate HTTP methods
and status codes for its endpoints. Server-side templates are used to render
the different application views, while SQLite provides persistent storage for
user accounts and posts.

## [Source on GitHub](https://github.com/hoseinn-gh/Web-application-project)
