
<span class="tag">Tags</span>:   [[Programming in C]] [[Coding]] [[Socket Programming]] [[Network]]

Created at 2024-10-02 16:10
<span class="tag">Status</span>: <span class="danger">Not done yet</span>
<span class="danger">Sources</span>:

# C Socket Programming

## Includes
PC 1 <------> Switch <------> PC 2
PCs connect to each other throw a switch.

`#include <stdio.h>` ---> Standard Input and Output.

`#include <sys/type.h>` ---> This file contains a couple of datatypes that are used in `syscalls`.

`#include <sys/socket.h>` ---> It gives us the definition of structures needed to work with sockets.

`#include <netinet/in.h>` ---> It adds constants and structures needed for domains and 

`#include <stdlib.h>` ---> It adds four new types of variables, a couple of macros and a bunch of functions for different purposes.

## Server-Client relationship

Server                                                   Client
`socket()`--->Makes a socket<---`socket()`
`bind()`--->It assigns `addr` to the socket.
`listen()`--->It listens to the requests.
`accept()`<-------------------------`connection()`
`read()`<---------------------------`write()`
`write()`-------------------------->`close()`

- Socket types and ports should be the same.
- If the server closes client wouldn't be able to connect to it.

## Socket Function
```c
int sockfd = Socket(int domain, int type, int protocol);
//Example:
int sockfd = Socket(AF_INET, SOCK_STREAM, 0); 
```
`domain = AF_INET` -> IPV4 -> For address family
`type = SOCK_STREAM` -> it is for TCP
`type = SOCK_DGRAM` -> it is for UDP
`protocol = 0` -> 0 is for TCP

## Bind Function
```c
int bind = Bind(int sockfd, const struct sockaddr *addr, socklen_t addrlen);
// Example:
int bind = Bind(sockfd, /*The Address sockaddr */, /* addrlen */)
```
`sockfd` -> The file descriptor(previous function)
`sockaddr` -> The address
`addrlen` -> Address struct size in bytes

## Addr Struct
```c
struct sockaddr{
	sa_family_t sa_family;
	char sa_data[14];
}
```
- This is the same struct that was passed throw the function in the prior heading
- If the Bind() function is successful it will return **0** and if not it returns **1**

## Listen Function
```c
int listen(int sockfd)
```

# References
