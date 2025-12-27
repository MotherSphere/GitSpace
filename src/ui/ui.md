# `src/ui/`

egui-based UI components for GitSpace.

## Contents
- `app.rs` — `GitSpaceApp` root component that wires panels and telemetry.
- `layout.rs` — panel and docking layout definitions inspired by GitKraken.
- `context.rs` — shared UI context and state passing.
- `clone.rs`, `recent.rs`, `repo_overview.rs` — discovery and repository overview panels.
- `history.rs`, `branches.rs`, `stage.rs` — repository interaction panels.
- `auth.rs`, `settings.rs`, `notifications.rs` — auxiliary panes for credentials, configuration, and messaging.
- `theme.rs` — theme and styling helpers.
- `animation.rs` — shared motion tokens, easing curves, and effect presets.
- `tests/` — UI-focused tests.

## Maintenance
- Keep UI interactions decoupled from git commands via shared state/context.
- Emit telemetry judiciously and respect user opt-in settings. UI navigation emits tab switch and tab reordering events only after consent.
- Keep navigation accessible: provide keyboard shortcuts (Ctrl/Cmd + 1-8), context menus, and drag-and-drop tab reordering alongside pointer clicks.
- Use animation tokens from `animation.rs` for motion timing and effects; respect reduced-motion preferences for all UI transitions.
- Update this document when adding new panels or significant layout changes.
