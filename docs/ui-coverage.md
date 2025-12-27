# UI Coverage Inventory

This document captures UI/layout entry points, interactive elements, and styling/animation notes for
`src/` plus any UI definitions in `assets/` or `docs/`. It is intended as a coverage list to help
ensure future animation and interaction work targets all relevant UI elements.

## UI entry points and layout wiring

- `src/main.rs`
  - **Role:** App entry point; starts eframe/egui and mounts `GitSpaceApp`.
  - **UI surfaces:** Root application window.
  - **Styling/animation:** Inherits egui theme; no explicit animations.

- `src/ui/app.rs`
  - **Role:** Root UI composition and lifecycle; wires panels, theme, telemetry, and layout.
  - **UI surfaces:** Central panel content; orchestrates layout + panel content.
  - **Styling/animation:** Theme applied via `Theme::apply`; no explicit animations.

- `src/ui/layout.rs`
  - **Role:** Shell layout (header, sidebars, tab bar, main content).
  - **UI surfaces:** Header, left navigation, right context panel, tab strip, tab content routing.
  - **Styling/animation:** egui `Frame` fills/strokes; custom tab underline painting; hover cursors.
  - **Interactive elements:**
    - Sidebar selectable labels (workspaces/actions).
    - Right-panel buttons: “Open in file manager”, “Copy path”, “Switch repository”, “Branch view”.
    - Tab bar labels with click/drag reorder; context menu “Switch to …”.

- `src/ui/theme.rs`
  - **Role:** Theme palette, typography, spacing, and egui visuals.
  - **Styling/animation:** Sets egui `Visuals` (colors, fills, text styles). No animations.

## Panel-level coverage (interactive elements)

### `src/ui/recent.rs` — Recent workspaces
- **Interactive elements:**
  - Filter input (`TextEdit`) + “Browse…” button.
  - Scrollable list of repo buttons (sized buttons acting as list items).
  - Empty state: “Open a workspace folder” button.
  - Quick access list: clickable labels (Home/Desktop/Documents/Downloads).
- **Styling/animation:** Buttons filled with theme colors; hover cursor change and path label.

### `src/ui/clone.rs` — Clone workflow
- **Interactive elements:**
  - Provider cards (GitHub/GitLab) with click selection.
  - Search input + “Search” button.
  - Results `ComboBox` selectable list.
  - URL input.
  - Destination input + “Choose” button.
  - “Clone repository” button.
  - Progress bar (read-only display).
- **Styling/animation:** Provider cards custom-painted with `painter.rect`; buttons themed; no animations.

### `src/ui/repo_overview.rs` — Repository overview
- **Interactive elements:**
  - Branch section resize grip (drag handle).
  - Remotes list (framed cards).
  - Quick action buttons: “Fetch”, “Pull”, “Push”, “Open terminal”, “Open file explorer”.
- **Styling/animation:** Frames with fills/strokes; custom painter for stat chips and resize grip.

### `src/ui/stage.rs` — Staging & commits
- **Interactive elements:**
  - Staged/unstaged file lists with checkboxes and “Diff” buttons.
  - File context menu: “Restore file…”.
  - Commit editor: template `ComboBox`, multiline input, “Add Signed-off-by” checkbox.
  - Stash controls: stash message input, “Create stash”, “Apply”, “Drop”.
  - Restore dialog (`Window`): file list, “Cancel”, “Restore”.
- **Styling/animation:** Multiple framed panels (diff preview, commit editor, stash controls).

### `src/ui/history.rs` — Commit history
- **Interactive elements:**
  - Filters panel: branch `ComboBox`, author/search/since/until inputs, “Apply filters” button.
  - Commit list: clickable framed rows (list items).
  - Details pane: collapsible file diffs.
- **Styling/animation:** Custom painter for history graph; framed list rows.

### `src/ui/branches.rs` — Branch explorer
- **Interactive elements:**
  - New branch bar: text input + “Create” button.
  - “Show stale only” checkbox.
  - Branch tree with collapsible headers and clickable branch labels.
  - Branch context menu:
    - Pin/Unpin
    - Checkout
    - Checkout & Track (remote only)
    - Delete branch (local only)
    - Merge into current
    - Rebase onto current
    - Compare with current
    - Open in History
    - Archive (local only)
    - Rename with inline input + “Apply”
  - Remote pagination: “◀”/“▶” buttons.
  - Comparison/selection panels: scrollable commit list.
- **Styling/animation:** Frames for badges, themed labels; no explicit animations.

### `src/ui/auth.rs` — Authentication
- **Interactive elements:**
  - Provider sections with host/token inputs.
  - “Validate & Save” button.
  - Saved hosts list with “Remove” buttons.
- **Styling/animation:** Custom `AuthActionButton` styles; section frames.

### `src/ui/settings.rs` — Settings
- **Interactive elements:**
  - Collapsible sections: Appearance, Repositories, Keybindings, Network, Privacy, Updates, Import/Export.
  - Theme `ComboBox`, control height slider.
  - Clone destination inputs + “Choose folder” / “Choose folder (native helper)” buttons.
  - Keybinding list: “Remove”, “Add keybinding”.
  - Network inputs + checkboxes.
  - Privacy checkboxes + “Purge collected diagnostics”.
  - Updates: checkbox, release channel `ComboBox`, “Check for updates now”.
  - Actions: “Save preferences”, “Reset to defaults”.
  - Import/Export: “Import settings”, “Export settings”.
- **Styling/animation:** Standard egui widgets; no animations.

### `src/ui/notifications.rs` — Toast notifications
- **Interactive elements:**
  - “Dismiss” button.
  - Action buttons: “Retry”, “Copy log path”, “Open release”, “Enable analytics”, “No thanks”.
  - “Open logs directory” hyperlink.
- **Styling/animation:** Custom colored toast frame with rounding; no animation API used.

## Docs + assets references

- `assets/assets.md`
  - Nerd Font assets (icons) used for provider branding in UI.

- `docs/ui-stack.md`
  - Confirms egui/eframe as UI framework (no web CSS stack).

- `docs/gitkraken-layout.md`
  - Describes layout rails, tab strip, navigation behaviors (context menus, drag/drop).

## Styling/animation summary

- **Styling:** Egui theme (`Theme::apply`) plus per-widget `Frame` fills/strokes/rounding and custom
  painting via `ui.painter()`.
- **Animation:** No explicit animation APIs (no tweening, keyframes, or CSS transitions). Interactions
  are immediate-mode (hover/click/drag) via egui responses.
