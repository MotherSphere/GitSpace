# Roadmap

This roadmap expands the strategic tasks from `tasks/tasks.md` with context and next steps.

## GitKraken-inspired UI
- Define the baseline layout (left navigation, history graph, diff/stage panel, branch/remotes sidebar).
- Prototype key interactions: drag-and-drop between panels, context menus for branches/commits, keyboard shortcuts for navigation.
- Capture UX telemetry events (with opt-in) to validate panel usage and navigation efficiency.
- Deliverable: a clickable mock or prototype demonstrating pane docking/resizing and history interactions.

## Rust/.NET Interoperability
- Candidates: platform-native dialogs, credential providers, or specialized libraries that already exist in .NET.
- Design a minimal IPC/FFI contract (data payloads, error codes, retries) and describe lifecycle/hosting expectations.
- Publish JSON examples in `/schemas` and keep them aligned with `docs/dotnet-contracts.md`.
- Investigate packaging: ensuring bundled runtimes do not complicate install/update flows.
- Align release packaging with the self-contained helper build so the runtime ships with each desktop artifact.
- Document required .NET SDK setup in `docs/dotnet-setup.md`.
- Deliverable: a spike proving a Rust UI calling into a .NET helper with documented contracts.

## Repository Discovery, Browsing, and Cloning
- Design the onboarding path: workspace chooser, search/filter for local and remote repositories, and cloning with progress feedback.
- Define “Recent” and “Recommended” repository surfaces, including caching and telemetry for feature adoption.
- Add guardrails: default clone destinations, credential prompts, and failure recovery guidance.
- Deliverable: UX flow diagrams plus validation rules for each step.

## Automated Setup Hooks
- Specify a safe manifest/schema for optional post-clone steps (e.g., JSON or TOML) with explicit consent prompts.
- Require sandboxing and logging for any script execution; document allowed commands and environment variables.
- Provide templates and docs for repository authors to add their own hooks.
- Deliverable: draft schema + sample hook definitions with user-facing consent copy.
