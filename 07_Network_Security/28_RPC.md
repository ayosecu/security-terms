<br>

# RPC (Remote Procedure Call)
RPC (Remote Procedure Call) is **a protocol that allows a program to execute code or procedures on a remote server or computer as if it were executing locally**. RPC abstracts the complexity of network communication, allowing developers to write distributed applications where tasks or services can be run on remote systems without the need for manual socket programming.

## Key Concepts of RPC
  - **Predefined Set of Tasks**: With RPC, the server exposes a predefined set of tasks or procedures that remote clients can execute. These tasks are typically part of the server’s functionality, and clients can invoke them as if they were local functions or procedures. The server processes the request, performs the task, and returns the result to the client over the network.
  - **Used Inside Organizations**: RPC is commonly used within organizations **for internal services and communication between systems in a distributed architecture**. For example, it allows internal systems to request services or data from other systems on the same network, such as requesting data from a database or invoking a service on another server within the same corporate network. RPC **simplifies the development of distributed applications by allowing remote communication without explicitly handling the network code**.

## How RPC Works
1. **Client-Server Architecture**: RPC follows a client-server model. The client makes a request to the server to perform a task, and the server responds with the result.
2. **Stub Functions**: To make the remote procedure call seem local, RPC uses stubs. On the client side, the stub acts as a proxy for the remote procedure, handling communication over the network. On the server side, the stub receives the request and invokes the correct procedure.
3. **Serialization/Deserialization**: Data is serialized into a format that can be transmitted over the network (usually in **binary or JSON** format) and then deserialized back into usable data by the receiving end.

## Advantages of RPC
  - **Transparency**: RPC abstracts the network communication, allowing developers to call remote procedures as if they were local, making distributed application development easier.
  - **Efficiency**: By using RPC, organizations can spread tasks across multiple servers, distributing workloads and improving performance in large-scale systems.

## Use Cases in Organizations
  - **Internal Services**: In large organizations, RPC is used for inter-service communication, where one service might need to request data or a task from another service hosted on a different server.
  - **Microservices Architecture**: In modern microservices-based systems, RPC is often used for communication between services, allowing microservices to call functions on other microservices remotely.

## Summary
  - RPC (Remote Procedure Call) allows remote clients to execute a predefined set of tasks on a server as though the tasks were being executed locally.
  - It is commonly used inside organizations for internal services and system-to-system communication, streamlining the development and execution of distributed applications.  
<br>