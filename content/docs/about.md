---
title: About
weight: 6
---

# About WiTTY

WiTTY is written in the [go programming language](https://go.dev/), using the 
[Gin web framework](https://github.com/gin-gonic/gin), [gorilla/websocket](https://github.com/gorilla/websocket), [pty](https://github.com/creack/pty), and the wonderful [xterm.js](https://xtermjs.org/)!
The workflow is simple, the client initiates a terminal 
window (xterm.js) and creates a websocket with the server, which relays the data between pty and xterm. 

The program has been tested on Linux, WSL2, Raspberry Pi 3B (Debian), and MacOSX using Google Chrome, Firefox, and Safari.

Most icons were provided by [fontawesome](https://fontawesome.com/) under this [license](https://fontawesome.com/license).