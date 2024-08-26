# desc
jzero common desc

```shell
protoc -I./third_party third_party/jzero/api/http.proto --go_out third_party/jzero/api
```

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
        option (jzero.api.http) = {
            middleware: "Auth"
        };
        option (jzero.api.zrpc) = {
            middleware: "Auth"
        };
    };
}
```

```protobuf
service Hello {
    option (jzero.api.http_group) = {
        middleware: "Auth"
    };
    option (jzero.api.zrpc_group) = {
        middleware: "Auth"
    };

    rpc SayHello(SayHelloRequest) returns(SayHelloResponse) {
        option (google.api.http) = {
            get: "/api/v1/hello"
        };
    };
}
```
