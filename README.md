# Chat Server with Message Forwarding and Bad Word Detection

## Overview
This project implements a chat server where multiple clients can connect and send encrypted messages to each other. The server performs encryption and decryption on messages, ensures that bad words are filtered out, and supports forwarding messages between clients. It uses multithreading to handle multiple clients simultaneously and ensures synchronization with mutex locks.

## Features
- **Client-Server Communication**: Clients can send messages to each other via the server.
- **Encryption/Decryption**: Messages are encrypted using a simple cipher based on a provided key and decrypted before displaying.
- **Bad Word Detection**: The server checks if messages contain any predefined bad words (e.g., "evil", "bad", "hate"). If detected, the message is ignored and a warning is sent back to the client.
- **Forwarding Messages**: Clients can forward messages to other clients by specifying the recipient's client number.
- **Multiple Client Support**: The server can handle multiple clients simultaneously, each in their own thread.
- **Dynamic Client List**: The server maintains a dynamic list of connected clients and updates all clients when someone connects or disconnects.

## Requirements
- C++11 or later
- Linux/Unix-like environment (using socket programming)
- Compiler supporting C++ standard libraries (iostream, string, vector, thread, map, mutex, etc.)

## Files
- **server.cpp**: The main C++ file that implements the server-side logic, handling socket connections, message processing, and encryption.
- **README.md**: This file containing the documentation for the project.

## Setup Instructions
### Clone the Repository:
```bash
git clone <repository_url>
cd <repository_directory>
