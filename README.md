# desc
jzero common desc

## proto

### jzero

1. gateway

* http.proto
* zrpc.proto

```protobuf
service Hello {
    rpc SayHello(SayHelloRequest) returns(SayHelloResponse) {
        option (google.api.http) = {
            get: "/api/v1/hello"
        };
        option (jzero.gateway.http) = {
            middleware: "Auth"
        };
        option (jzero.gateway.zrpc) = {
            middleware: "Auth"
        };
    };
}
```

```protobuf
service Hello {
    option (jzero.gateway.http_group) = {
        middleware: "Auth"
    };
    option (jzero.gateway.zrpc_group) = {
        middleware: "Auth"
    };

    rpc SayHello(SayHelloRequest) returns(SayHelloResponse) {
        option (google.api.http) = {
            get: "/api/v1/hello"
        };
    };
}
```
