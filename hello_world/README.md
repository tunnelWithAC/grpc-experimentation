### Steps

(Based on Python GRPC [Quick Start](https://grpc.io/docs/languages/python/quickstart/))

Generate files

```commandline
python -m grpc_tools.protoc -I./protos --python_out=. --pyi_out=. --grpc_python_out=. ./protos/helloworld.proto
```

Run Server

```commandline
python greeter_server.py
```

Run Client

```commandline
python greeter_client.py
```