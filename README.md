# Aikyam Protocol Buffers

Shared gRPC contracts for all Aikyam microservices.

## Structure

```
proto/
├── aikyam/feed/v1/           # Feed generation contracts
│   └── candidate.proto
├── aikyam/kg/v1/             # Knowledge graph contracts
│   └── knowledge_graph.proto
└── aikyam/ml/v1/             # ML ranking contracts
    └── ranker.proto
```

## Generating Java Code

```bash
# From consuming Java service
./mvnw protobuf:compile
```

## Generating Python Code

```bash
python -m grpc_tools.protoc \
  -I. \
  --python_out=. \
  --grpc_python_out=. \
  proto/aikyam/feed/v1/candidate.proto
```

## Versioning Policy

- **Backward-compatible changes:** Add fields, add enum values → minor version bump
- **Breaking changes:** Remove fields, change types → new package version (v2)
- **Never** remove a field — mark as `reserved` instead
