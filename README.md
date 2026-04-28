# Ex.No:1a  			Study of Socket Programming
Name: Ritika S
Reg no: 212225220086
## Aim: 
To implement a program on Socket Programming
## Introduction:

 	Socket programming is a crucial aspect of network communication, allowing for data exchange between computers over a network. It forms the backbone of various networked applications, enabling communication between clients and servers. This study explores the fundamental concepts of socket programming, its use cases, and provides a practical example to demonstrate its implementation.
## Understanding Socket Programming:
	Socket programming involves the use of sockets, which serve as endpoints for communication. A socket is identified by an IP address and a port number, and it facilitates data transfer between a client and a server. The two main types of sockets are Stream Sockets, which provide a reliable, connection-oriented communication, and Datagram Sockets, which are connectionless and suitable for scenarios where reliability is less critical.
## Key Concepts in Socket Programming:
1.Sockets
•	A socket is a software representation of a communication endpoint in a network.
•	It is identified by an IP address and a port number.
•	Sockets can be classified into two main types: Stream Sockets and Datagram Sockets.
•	Stream Sockets provide a reliable, connection-oriented communication, while Datagram Sockets are connectionless and operate in a best-effort mode.

2. Client-Server Model

•	Socket programming typically follows the client-server model.
•	The server listens for incoming connections from clients, while clients initiate connections to the server.
•	Servers are passive, waiting for connection requests, and clients are active, initiating communication.

3, TCP/IP Protocol:

•	Transmission Control Protocol (TCP) and Internet Protocol (IP) are the foundational protocols for socket programming.
•	TCP provides reliable, connection-oriented communication, ensuring data integrity and order.
•	IP facilitates the routing of data between devices in a network.

4.Basic Socket Functions:

•	Socket programming involves a set of functions provided by the operating system or programming language to create, bind, listen, accept, connect, send, and receive data through sockets.
•	Examples of functions include socket(), bind(), listen(), accept(), connect(), send(), and recv().

## Program:
```
import socket
import threading
import time
HOST = '127.0.0.1'
PORT = 12345
def server_task():
    mentor = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    mentor.bind((HOST, PORT))
    mentor.listen(1)
    print("Server waiting for client...💫")
    conn, addr = mentor.accept()
    print("Connected to client:🫡", addr)
    while True:
        msg = conn.recv(1024).decode()
        if msg.lower() == "hi server👋🏻":
            reply = "Hello! How can I help you?❔"
        elif msg.lower() == "what are you doing?😊":
            reply = "I'm just chatting with you!!🩷"
        elif msg.lower() == "what did you have for dinner?🍛":
            reply = "I just had some delicious pizza!🍕"
        elif msg.lower() == "wow delicious!😋":
            reply = "yummy! Pizza is the best!🍕 But unhealthy😔.... Avoid during dinner time!!🤍"
        elif msg.lower() == "bye server🎀":
            reply = "goodnight! Sleep well! 😴"
            conn.send(reply.encode())
            break
        else:
            reply = "Sorry, I didn't understand.😐"
        conn.send(reply.encode())
    conn.close()
    mentor.close()
def client_task():
    time.sleep(1) 
    client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client.connect((HOST, PORT))
    messages = [
        "hi server👋🏻",
        "what are you doing?😊",
        "what did you have for dinner?🍛",
        "wow delicious!😋",
        "bye server🎀"
    ]
    for msg in messages:
        print("Client🤍:", msg)
        client.send(msg.encode())

        reply = client.recv(1024).decode()
        print("Server🎀:", reply)
        time.sleep(1)
    client.close()
server_thread = threading.Thread(target=server_task)
client_thread = threading.Thread(target=client_task)
server_thread.start()
client_thread.start()
server_thread.join()
client_thread.join()
```

## Server-Side Operations:

•	Servers create a socket using socket() and bind it to a specific IP address and port using bind().
•	They then listen for incoming connections with listen() and accept connections with accept().
•	Once a connection is establi
•	shed, servers can send and receive data using send() and recv().

## Client –Server Operations

Clients create a socket using socket() and connect to a server using connect().
After establishing a connection, clients can send and receive data using send() and recv().

## Use Cases of Socket Programming:
Socket programming finds applications in various domains, including web development, file transfer protocols, online gaming, and real-time communication. It is the foundation for protocols like HTTP, FTP, and SMTP, which power the internet. Socket programming enables the development of both server and client applications, facilitating the exchange of information between devices in a networked environment.
## Example Use Cases:

1.	Web servers: Web servers use socket programming to handle incoming HTTP requests from clients, serving web pages and content.
2.	Chat Application: Instant messaging and chat applications use sockets to enable real-time communication between users.
3.	File Transfer Protocol: Protocols like FTP (File Transfer Protocol) utilize socket programming for transferring files between a client and a server.
4.	Networked Games: Online multiplayer games rely on socket programming to facilitate communication between game clients and servers.
5.	RPC mechanisms: which allow processes to execute code on a remote server, often use socket programming for communication.
## Output: 
<img width="654" height="713" alt="Screenshot 2026-04-28 225826" src="https://github.com/user-attachments/assets/61e0f80b-252c-4e77-af79-6e8d7d22350e" />

## Result:
Thus the study of Socket Programming Completed Successfully
