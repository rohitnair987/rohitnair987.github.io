---
layout      : post
title       : "Hoosier Chat Application"
excerpt     : "Indiana University Bloomington"
project     : true
tab 		: sd
git         : https://github.com/rohitnair987/Computer-Networks/tree/master/project3
startDate   : September 2016
endDate     : November 2016
tag:
- Java
- Computer Networks
- Chat
- Object Oriented Design
- AWS
- Socket programming
- Client-Server architecture
comments    : false
---

Hoosier Chat is a chat room application that allows users to send text messages to each other, broadcast messages and send files too! The application uses a client server architecture and is based on socket programming.

The Server (when active) sets up a server socket that listens at the IP address and port number it resides on. Clients can connect to this socket provided they know the IP and port that the server is active on. The server has one thread listening to new connections and creates a new socket connection for each client that requests it. This connections handles requests and push messages for that client only. The server has another thread which simply listens to the server’s console input and responds to the requests made.

The Client has one thread running to listen to the commands that the user types in to the client console and pass it to the server. So, unlike the server console thread, this one does a dual job instead of just one. Now the client also maintains another thread that is responsible to receive and process messages and data from the server. All interactions between clients are through the server so the clients need to listen to itself and the server only.

The application transmits all commands and messages in the form of strings from client to server and vice versa, except that for transferring a file I use byte transfers so I can transmit non-text based files as well.


### Features:
1.	Account registration
2.	Login
3.	Logout
4.	Broadcasting messages publicly
5.	Sending messages privately
6.	List online users
7.	Server Events
8.	Check status of a user
9.	Who am I
10.	Check whether a username exists in the system
11.	Sending files