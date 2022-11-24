### Implementing gRPC Client and Server
Let’s try to understand the most important concepts of gRPC:

* Protocol Buffers: Defining messages and services defined by the server application. The gRPC services send and receive data as Protocol Buffer messages.
* Server: The server application implements and defines RPC services.
* Client: The client application uses the RPC services defined by the server.


Map Reduce 

https://miro.medium.com/max/640/1*jEDSbr5E-qUG4RJw3iZYjg.jpeg

### What are protocol buffers?
Just one more concept before getting to the code!

Protocol buffers are Google’s language-neutral, platform-neutral, extensible mechanism for serializing structured data. If you just define how you want your data to be structured once, then a specially generated source code can be used to easily write and read your structured data to and from a variety of data streams and also using a variety of languages.

Protocol buffers is an Interface Definition Language used to define API contracts in gRPC. In gRPC, the API contracts in written in `.proto` files. In gRPC APIs are defined by declaring messages and services.

**Message**: The message is a binary data structure that is exchanged between client and server. The message and service are declared in `.proto` files. If you want, you can create separate files for messages and services.

**Service:** A service is a remote method that is exposed by the server. The client can use the generated stub to call the remote method on the server.

### Code generation
You can use protoc the compiler to generate client and server code. The protoc compiler supports code generation in many different languages.

### Code Structure
There are three main files called the client, worker and driver. The client gives the input files and the number of output files and the worker ports (e.g. 127.0.0.1:8081). The worker nodes are launched with their ports and are responsible for the map and reduce operations. The driver takes the input from the client and distributes the work among all the worker nodes.



```commandline
python -m grpc_tools.protoc -I. --python_out=. --grpc_out=. driver.proto
```