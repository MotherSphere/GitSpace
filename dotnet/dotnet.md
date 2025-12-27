# .NET helper project

## Structure
```
dotnet/
└── GitSpace.Helper/
    ├── GitSpace.Helper.csproj
    └── Program.cs
```

## Build
From the repository root:
```
dotnet build dotnet/GitSpace.Helper/GitSpace.Helper.csproj
```

## Run
```
dotnet run --project dotnet/GitSpace.Helper -- "Hello from GitSpace"
```

## Credential request validation
From the repository root:
```
cat <<'EOF' | dotnet run --project dotnet/GitSpace.Helper
{
  "id": "req-credential-get",
  "command": "credential.request",
  "payload": {
    "service": "gitspace-docs",
    "account": "user@example.com",
    "action": "get"
  }
}
EOF
```
Expect `status=not_found` when the secret does not exist.

```
cat <<'EOF' | dotnet run --project dotnet/GitSpace.Helper
{
  "id": "req-credential-store",
  "command": "credential.request",
  "payload": {
    "service": "gitspace-docs",
    "account": "user@example.com",
    "action": "store",
    "secret": "example-token"
  }
}
EOF
```

```
cat <<'EOF' | dotnet run --project dotnet/GitSpace.Helper
{
  "id": "req-credential-erase",
  "command": "credential.request",
  "payload": {
    "service": "gitspace-docs",
    "account": "user@example.com",
    "action": "erase"
  }
}
EOF
```

## Test
From the repository root:
```
cargo test dotnet::tests::ipc_handshake_ping_ok
cargo test dotnet::tests::ipc_credential_request_statuses
cargo test dotnet::tests::ipc_library_call
```
