# CECS 327 Lab - Peer to Peer Networks

### Assignment Description

The goal of this assignment is to become familiar with peer to peer (P2P) networks and having a client act as both client and server using the same codebase. You may work on this project in pairs if you choose.

Design a program which allows multiple computers to synchronize files across a local area network (LAN). In order to complete the assignment, I am requiring the use of [Docker](https://www.docker.com) to implement your distributed network which will simulate the networking environment and manage the seperate nodes in this network. [Docker Desktop](https://docs.docker.com/desktop) is my recommendation to use on laptop or desktop computers, whereas [Docker Engine](https://docs.docker.com/engine) provides the core functionality for servers, virtual machines, and embedded devices. If you are an advanced Linux user (or are running Docker in a VM), you may want to consider Engine over Desktop as it will provide the same functionality but in a lighter-weight package.

Note: if you are using Linux to run Docker (whether on hardware or in a virtual machine), note that your distribution likely has Docker included with its repositories and should be installed by [running the appropriate package install command](https://docs.docker.com/desktop/install/linux-install) (eg. `sudo apt install docker`).

Each Docker contianer will be a seperate instance of your running code. All nodes *must* be identical in code with the exception of the configuration locations, directory attachments, etc. Essentially, only their Docker config files may differ.

You will be "exchanging" files from one node to the other through the use of *[sockets](https://linux.die.net/man/7/socket)*, which are [Linux and Unix's way of implementing interprocess communication](https://www.linuxhowtos.org/C_C++/socket.htm).

Here is an example of the "networking" that I would like to have implemented (warning: lots of *set theory mathematics* ahead):

> Nodes $P_{1},P_{2},\ldots P_{n}$ have clients $C_{1},C_{2},\ldots C_{n}$ installed on each node respectively. $F_{1},F_{2},\ldots F_{n}$ are sets of files where $F_{1}$ is the set of files on node $P_{1}, F_{2}$ is the set of files on node $P_{2}$, and so forth.

> The goal of your program should be the unification of all sets of files, $F$, so that $P_{i},C_{i}\cup \{ F_{j}\}$ on each client.

Essentially, what I am asking you to do is to create your own mini version of [Dropbox](https://dropbox.com); rather, you will be making a program which will run many instances (nodes) in Docker and each "instance" will act as a node to synchronize all of the files which one instance "points" to (which may be on a local hard-drive, a network, or *anywhere* really) with the contents of whatever the other node "points" to.

Since your computer is emulating the "universe" for your running nodes, you can (and should) specify seperate "sync" locations for each node. This can be done by using a [Docker Compose](https://docs.docker.com/compose) configuration file for your assignment. Docker Compose allows for one file to configure many different Docker nodes all at once.

### Some Notes

* If you're feeling a bit lost right now, it's okay. Here is what I recommend to do to get yourself started:
  * Install [Docker](https://docs.docker.com/desktop) and [Docker Compose](https://docs.docker.com/compose) for your operating system.
  * Find a few pre-built Docker repositories and play with them. I particulary enjoy tinkering with the [repos made by linuxserver.io](https://www.linuxserver.io). Want to try out something fun? Check out [SteamOS on Docker](https://github.com/linuxserver/docker-steamos).
  * Once you feel like you have the basics of Docker usage, try making a Docker container with a defined port/socket and a simple program to handle that socket [using something like this](https://realpython.com/python-sockets).

* Want a bit more background about Docker, or maybe want to check out other cool things you can do with Docker? [There's an Awesome repository for that](https://github.com/veggiemonk/awesome-docker).

* Is Docker not installing/working correctly? Is it really slow or is your computer now acting strangely after you installed it? Docker is a virtual machine (containerd) and using it along with other VM software will cause a race condition. Make sure you have the (https://github.com/docker/for-win/issues/11764).

* You might need a [distributed hash table](https://stackoverflow.com/questions/144360/simple-basic-explanation-of-a-distributed-hash-table-dht) (DHT) implementation in order to complete this assignment, although, if you are clever, there is a way to do this assignment without one. :)

* Before diving in to the project, there are a few things that I recommend you consider:
  * How will your nodes discover other clients on the network? Remember, just because it's Docker doesn't mean we don't have to implement the LAN networking too.
  * How will your client deal with files of the same name but different contents? Different timestamps?
  * How will your client determine the order of syncing with regards to the files of other clients? (Docker might be able help here).

### Deliverables

*Demonstrate* your working code on a unique set of files for each Docker node (minimum of *four* active nodes) for the instructor.

Your submission must follow the following rules:

* Do *not* use compression on your files. This is extremely poor practice for code repositories, unless you have a very good reason for doing so.
* Ensure that all significant code is *commented* with your own explanations. Code or projects without comments *will not receive credit*.
* Your project, through git, should have enough commits to justify a semester-long project. Git repositories with very few commits on the repo will be heavily scrutinized and may receive reduced points.
* Please make your git commit comments *helpful* and *concise*. Commit comments like 'updated file' or 'uploaded doc' are not helpful. Commit comments like 'fixed network bug in `project.py`' and 'added code to support file comparison' are much better.
