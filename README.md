# CECS 327 Lab - Peer to Peer Networks

## Assignment Description
The goal of this assignment is to become familiar with peer to 
peer (P2P) networks and having a client act as both client and server using the same codebase. You may work on this project in pairs if you choose.

Design a program which allows two or more computers to 
synchronize files across a local area network (LAN). In order to complete the assignment, I am requiring the use of Docker to implement your distributed network. 

Each computer should run its own local instance of the client 
software, and the files which will be synchronized should be able to be synchronized multi-directionally.

Example: Nodes P_{1},P_{2},\ldots P_{n} have clients C_{1},C_{2},\ldots C_{n} installed on each node respectively. F_{1},F_{2},\ldots F_{n} are sets of files where F_{1} is the set of files on node P_{1}, F_{2} is the set of files on node P_{2}, and so forth.

The goal of your program should be the unification of all sets of files, F, so that P_{i},C_{i}\cup\left\{ F_{j}\right\} on each client.

## Some Notes
* If you're working in pairs for this assignemnt, please let me know ASAP and I will create a single git repository for both people to use.
* If you've done the previous assignment (and hopefully feel more comfortable using Docker), great! If not, this is where I would highly recommend to start. Also, if you did the lesson and want a bit "more", I encoruage you to find a few Docker repositories and play with them. I particulary enjoy tinkering with the [repos made by linuxserver.io](https://www.linuxserver.io).
* If you're feeling okay with Docker and still don't know where to start, try making a Docker container with a defined port/socket and a simple program to handle that socket [using something like this](https://realpython.com/python-sockets). 
## Tips
* You will most likely need a distributed hash table (DHT) 
  implementation in order to complete this assignment.
* Public WiFi networks often block port access amongst peers on the network, so you will not likely be able to test this on the campus's WiFi network or any other public network.
* Before diving in to the project, there are a few things that I recommend you consider:
    * How does the client discover other clients on the network?
    * How does the client deal with files of the same name but 
    different contents? Different timestamps?
    * How does the client determine the order of syncing with 
    regards to the files of other clients?

# Deliverables

Demonstrate your working code on a unique set of files for each client (minimum of two) for the instructor. Be sure to submit a copy of your source code files, makefile, and the write-up in a separate .txt, .md, .rtf, or web-renderable .html file only. Please do not compress your files for submission. Make sure that all code is commented with your own explanations or it will not be graded.

Your submission must follow the following rules, else *I will not grade it and you will receive a zero for the submission*:

* Do not use compression on your files
* Make sure that all significant code is *commented* with your own explanations
