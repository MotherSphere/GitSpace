# Tasks and Folder Conventions

This document tracks work items and records the documentation conventions for GitSpace.

## Folder Documentation Convention
- Every project folder must include a Markdown file named after the folder itself.
  - Examples:
    - `tasks/` → `tasks/tasks.md`
    - `docs/` → `docs/docs.md`
    - future `config/` → `config/config.md`
    - future `ui/` → `ui/ui.md`
- Each folder-specific Markdown file must describe:
  - the purpose of the folder,
  - what kind of files it contains,
  - important notes for maintenance and future extensions.

## Current Tasks
- **GitKraken-inspired GUI layout**
  - Capture the primary panes (repo tree, history graph, diff/stage, branches, remotes) and how they resize/dock.
  - Prototype navigation flows between panels (keyboard shortcuts, context menus, drag-and-drop).
  - Document telemetry touchpoints and opt-in UX for UI events.

- **Rust/.NET interoperability**
  - Identify candidate features to host in .NET (e.g., platform-native dialogs, existing libraries to reuse).
  - Spike a thin IPC layer between Rust and .NET and document data contracts and error handling.
  - Evaluate packaging/distribution impact for dual-runtime components.

- **Repository discovery, browsing, and cloning**
  - Map the onboarding flow: workspace selection, search/browse (local + remote), clone with progress, and post-clone actions.
  - Design recent/recommended repository surfaces and shortcuts in the UI.
  - Add validation and helpful defaults for clone destinations and authentication.

- **Automated setup hooks**
  - Define a safe format for optional post-clone/install steps (schema, validation, sandboxing).
  - Specify user consent UI and logging around hook execution.
  - Provide guidance for repository authors to contribute their own hooks.

- **Credential storage hardening and error handling**
  - Require native keychain by default; prompt before falling back to encrypted files and capture explicit consent.
  - Introduce salted KDFs or a master password for derived keys; log keychain errors with actionable context instead of silently degrading.
  - Add structured error handling around credential load/save flows, distinguishing user denial, platform limitations, and unexpected failures.

- **Telemetry resilience and validation**
  - Bound offline queue size and age, add client timeouts, and implement backoff with jitter for retries.
  - Sign or authenticate payloads; consider certificate pinning for the telemetry endpoint.
  - Strengthen error handling: classify network vs. payload errors, persist failure diagnostics, and surface user-facing opt-in states.

- **Update channel safety**
  - Add timeouts and checksum/signature verification for release assets; ignore unsigned artifacts.
  - Document preview vs. stable channels and provide rollback behavior for failed updates.
  - Improve error reporting around update checks and downloads, including actionable messages for connectivity and verification issues.

## Launch-ready task list
- [ ] **CS-01: Harden credential storage fallbacks**
  - Require native keychain usage by default; show an explicit consent prompt before falling back to encrypted files.
  - Add a salted KDF or master password in the fallback path and log structured error details for keychain failures (user denial vs. platform limitation).
  - Validate recovery flows: missing keychain, corrupted encrypted file, and permission errors must surface actionable guidance.
- [ ] **TM-01: Stabilize telemetry pipeline**
  - Enforce queue caps (size + age), client timeouts, and retry backoff with jitter; add metrics around drops.
  - Authenticate or sign telemetry payloads and consider certificate pinning for the endpoint.
  - Implement error taxonomy (network vs. payload vs. auth) with persisted diagnostics and user-facing opt-in state.
- [ ] **UP-01: Secure update channel handling**
  - Add network timeouts plus checksum/signature verification; ignore unsigned or mismatched assets.
  - Document preview vs. stable channels, including rollback mechanics when downloads fail or validation is rejected.
  - Provide structured error handling for update checks/downloads with clear remediation for connectivity, verification, and disk issues.
