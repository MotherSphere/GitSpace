# `src/`

This folder contains the Rust source for GitSpace, including the application entry point, shared utilities, and feature-specific modules. Start here to understand how the crate wires together UI, Git operations, telemetry, and configuration.

## Contents
- `main.rs` boots the `GitSpaceApp` UI and initializes logging.
- `logging.rs` configures log capture for the eframe/egui application.
- `update.rs` handles application update checks.
- `error.rs` provides shared error types.
- `config.rs` holds user and runtime configuration.
- `auth/` implements authentication primitives.
- `git/` wraps Git interactions.
- `ui/` defines the egui-based interface.
- `telemetry.rs` records anonymized diagnostics.

## Maintenance
- Keep module docs aligned with the README and architecture notes.
- Add new subfolder docs following the convention described in `tasks/tasks.md`.
- Document feature flags or environment assumptions near the relevant modules.
