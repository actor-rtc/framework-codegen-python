# framework_codegen_python

Protoc plugin for generating Actr Python framework code from protobuf service definitions.

## Status

🚧 **Placeholder** - Initial Python version

## What it generates

From a protobuf service definition:

```protobuf
service EchoService {
  rpc Echo (EchoRequest) returns (EchoResponse);
}
```

Generates:

1. **Handler base class** - User implements business logic
2. **Dispatcher** - Routes messages to handler methods
3. **Workload wrapper** - Integrates with ActrSystem

## Architecture

- Uses **Dispatcher** with static route table
- Uses **WorkloadBase** for `get_dispatcher()` integration
- Generates minimal, idiomatic Python glue code

## Usage

```bash
# Install
pip install framework_codegen_python

# Generate code
protoc -I proto \
  --python_out=generated \
  --plugin=protoc-gen-actrpython=framework_codegen_python \
  --actrpython_out=generated \
  proto/echo.proto
```

This package installs an executable named `framework_codegen_python`.
