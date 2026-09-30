---
title: "Real-Time Network Traffic Monitoring System"
excerpt: "A Linux packet-capture service in C++ feeding a live browser dashboard, built during an industry internship."
collection: portfolio
---

An internal tool built during an industry internship: a system that captures network traffic on a production Linux server, stores it, and presents both live and historical views in a browser. I was the sole developer, working across the whole stack, capture service, backend, persistence, and dashboard.

The target server handles 100,000+ packets per second, so every module, capture, message bus, backend, persistence, and dashboard, had to stay lightweight and fast. A slowdown anywhere in the pipeline would cause it to fall behind the live traffic.

## Capture

The capture service is written in C++20 on top of libpcap, parsing Ethernet, IPv4, TCP and UDP headers from the packet stream. A BPF filter excludes the server's own traffic at the capture layer, since the dashboard's own network activity would otherwise show up in the feed it's reporting on.

## Backend and storage

Parsed packet metadata is published over ZeroMQ to two independent consumers: a C++ web server built on Drogon, which relays live updates to connected browsers over WebSockets, and a separate persistence service, which writes packets in batches to a TimescaleDB time-series database. Keeping persistence as its own process means a slow database can't affect the live feed. Historical queries and the live feed use the same filtering logic, since all packet fields are retained in storage.

## Dashboard

The front end is built in Vue 3, TypeScript, and Vite, with ECharts for the live bandwidth graph and TanStack Virtual for the packet table. Incoming updates are buffered and flushed on a fixed interval rather than triggering a re-render per packet, and the packet table only renders the rows currently visible rather than the thousands held in memory. A client-side filter language lets the user narrow the live feed by IP, port, or protocol.
