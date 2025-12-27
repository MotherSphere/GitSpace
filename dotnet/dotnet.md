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

## Test
From the repository root:
```
cargo test dotnet::tests::ipc_handshake_ping_ok
cargo test dotnet::tests::ipc_credential_request_statuses
cargo test dotnet::tests::ipc_library_call
```
