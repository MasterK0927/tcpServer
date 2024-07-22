Basic Mechanisms of client server setup are
1. A client side application, that sends the request to the server app.
2. The server app returns a reply.
3. Basic comm btw them includes file transfer, web page, echo.

Server Socket
1. Create a socket, get the file descriptor.
2. Bind to an address.
3. Listen on a port, and wait for the connection to get established.
4. Accept the connection from the client.
5. The same way we can send/recieve for a file.
6. Shutdown to end the read and write mode.
7. Close to release data.

Client Socket will do:
1. Create a socket.
2. bind* is unneccessary as we are client not the server.
3. Connect to the server.
4. Send/recieve until we recieve the data.
5. Shutdown to end read / write.
6. Close to release the data.

Some FAQs
1. What we use?
Socket is the way of speaking to other programs using the standard file descriptors.

2. Where do we get the file descriptor for the network communication?
We make the call to the socket() system routine. After the socket() returns the socket descriptor, we start communicate through it using the specialisedsend() / recieve() socket API calls.

3. What is TCP socket?
TCP socket is an endpoint instance.It is not a connection, but an endpoint of a specific connection. It is defined by 2 endpoints / sockets.

4. What is the purpose of the PORT?
Ports are used for differentiating the multiple endpoints on a given networkaddress.

5. Briefly explain ports?
Port numbers are encoded in the transport protocol packet header, and they can be readily interpreted not only by the sending and recieving computers but also by other components of the networking infrastructure. Particularly firewalls are commonly comnfigured to differntiate between the packets based on their source or destination port numbers as in port forwarding.

6. What is responsible for the identification of TCP connection?
Socket pair (4-tuple that consists client IP address, client port number, server IP address and server port number) specifies two endpoints that uniquely identifies each TCP connection in an internet,

7. There should be a single process that binds to a specific IP address and port combination using the same transport protocol. Otherwise we will have the port conflicts, where multiple programs attempt to bind to the same port numbers on the same IP address using the same protocol.

8. What is a connection?
A relationship between the two machines, where two pieces of software know about each other. Those two pieces of software know how to communicate with each other. In other words they know how to send and recieve bits to each other.

9. What is a socket connection?
A socket connection means the two machines have information about each other, including network location (IP Address) and TCP port, analogous to ip address as a phone number and tcp port as extension. 

10. What is Socket?
A socket is an object similar to a file that allows a program to accept incoming connections, making outgoing connections, and send and recieve data, Before two machines can communicate both must have to create a socket object. It is created by the socket() call, and it can not be shared with the other processes.

Socket() object is not only created by TCP, there are oter protocols like UDP, that creates the socket() object but with different configuarations.


## BRIEF INTRODUCTION TO TCP AND UDP? WHICH TO USE?

UDP stands for User Datagram Protocol, it is a connectionless protocol, which doesnt require to establish a dedicated connection before transmissing the data.

It offers the below capabilites: 

1. **Best effore delivery**: UDP delivers packets as quickly as possible, without ensuring they arrive in the correct order or reassembling them if lost,

2. **No connection establishment**: UDP doesnt setup a connection with the recieving device, It simply sends and recieves datagrams (packets).

Some flaws : 

3. **No flow control**: UDP allows devices to send data at their own pace, which can lead of network congestion.

4. **No error detection or correction**: UDP relies on high layer protocols to handle errors. 



When is UDP preferred?
1. In online gaming we prefer udp based connections,as low latency is very very crucial in this scienario,

2. For streaming media also we use UDP based communication, as delay needs to be minimised.

3. For realtime communication scienarios like online chatting, VoIP we use UDP.


TCP stands for Tranafer commision protocol, it is a connection-oriented protocol, as it establishes the communication with the destination device before transmitting data.

It offers below capabilities:

1. **Guaranteed delivery**: TCP ensures that the data us delivered in the correct order and resembles it if packets are lost or corrupted during the transmission.

2. **Connection Establishment**: Before sending the data, it established a connection with the recieving device using three way handshake (SYN, SYN-ACK, ACK).

3. **Flow control**: TCP regulates the amount of data sent at once to prevent network congestion and ensure smooth transmission.

4. **Error detection and correction**: TCP includes error checking mechanisms for eg checksums, to detect and correct errors during transmission.


TCP is used when: 

1. File Transfers are happening (FTP, SFTP).
2. Email (SMTP).
3. Web Browsing (HTTP).
4. Online Gaming, where reliability is crucial.


Atlast for summarising the whole thing:

1. Use TCP when: 
    a. We require guaranteed delivery and assembly of data.

    b. Transferring large files or sensitive information.

2. Use UDP when:
    a. Priotise low latency and real-time performance.

    b. Transmitting small amounts of data or non critical information.
