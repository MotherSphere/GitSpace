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
