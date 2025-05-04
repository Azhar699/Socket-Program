💬 Chat Server with Message Forwarding and Bad Word Detection
📘 Overview
This project implements a chat server where multiple clients can connect and send encrypted messages to each other. The server performs encryption and decryption on messages, ensures that bad words are filtered out, and supports forwarding messages between clients. It uses multithreading to handle multiple clients simultaneously and ensures synchronization with mutex locks.

✨ Features
Client-Server Communication: Clients can send messages to each other via the server.

Encryption/Decryption: Messages are encrypted using a simple cipher based on a provided key and decrypted before displaying.

Bad Word Detection: The server checks if messages contain any predefined bad words (e.g., "evil", "bad", "hate"). If detected, the message is ignored and a warning is sent back to the client.

Forwarding Messages: Clients can forward messages to other clients by specifying the recipient's client number.

Multiple Client Support: The server can handle multiple clients simultaneously, each in their own thread.

Dynamic Client List: The server maintains a dynamic list of connected clients and updates all clients when someone connects or disconnects.

⚙️ Requirements
C++11 or later

Linux/Unix-like environment (using socket programming)

Compiler supporting standard libraries (iostream, string, vector, thread, map, mutex, etc.)

📁 Files
server.cpp: Implements the server logic, socket handling, encryption, message routing.

README.md: Documentation file (this file).

🛠️ Setup Instructions
🔽 Clone the Repository
bash
Copy
Edit
git clone <repository_url>
cd <repository_directory>
🔧 Compile the Code
If you are using g++, compile the server code with threading support:

bash
Copy
Edit
g++ server.cpp -o server -pthread
🚀 Run the Server
bash
Copy
Edit
./server
🌐 Client Connection
Once the server is running, clients can connect by specifying the server IP and port (e.g., localhost:8080).

🧠 Key Functions
✅ containsBadWord
Checks if a message contains any predefined bad words.

cpp
Copy
Edit
bool containsBadWord(const string &message);
🔐 encrypt
Encrypts a text message using a simple cipher with the provided key.

cpp
Copy
Edit
string encrypt(string key, string text);
🔓 decrypt
Decrypts the message back to its original form using the same key.

cpp
Copy
Edit
string decrypt(string key, string res);
📤 sendMessageToClient
Sends an encrypted message to a specific client using their socket.

cpp
Copy
Edit
void sendMessageToClient(string encKey, string senderclientName, int recipientclientName,
                         const string &message, std::map<int, string> &cname, std::map<int, int> &cn);
🧩 handleClient
Handles incoming communication from a client. Decrypts, checks for bad words, and forwards valid messages.

cpp
Copy
Edit
void handleClient(int clientNumber, int clientSocket, string clientName,
                  std::map<int, string> &cname, std::map<int, int> &cn);
🗣️ sendMessage
Allows the server to send a message to any connected client.

cpp
Copy
Edit
void sendMessage(std::map<int, string> &cname, std::map<int, int> &cn);
🔄 Working of the Server
🛠️ Server Initialization
Binds a socket to port 8080 and listens for incoming connections.

🤝 Client Connections
Clients connect using the server’s IP and port.

A new thread is created to handle each client individually.

📬 Message Handling
Messages are encrypted before being sent and decrypted on the server.

Messages containing bad words are ignored, and a warning is sent to the sender.

Valid messages are forwarded to the recipient client.

The server maintains a real-time list of connected clients.

🛑 Stopping the Server
When the special keyword "123" is received from any client, the server shuts down and closes all connections.

💬 Example of Client Interaction
Client 1 Sends:
text
Copy
Edit
Hello Server!
Server:
If the message contains bad words → sends a warning.

If clean → logs it and optionally forwards it.

Client 2:
If Client 1 addressed Client 2 using their client number, the message is forwarded after encryption.

🌟 Future Enhancements
Authentication: Require clients to log in before accessing chat features.

GUI Interface: Add a user-friendly GUI using Qt or SDL.

Improved Encryption: Replace simple cipher with AES or other secure algorithms.

Message History: Save and retrieve chat history using a database.