# `src/git/`

Git integration layer providing repository operations used by the UI.

## Contents
- `branch.rs` — list, create, delete, rename, and checkout branches (local and remote aware).
- `clone.rs` — clone workflows and repository initialization helpers.
- `diff.rs` — file diffs and change presentation utilities.
- `log.rs` — commit history retrieval.
- `merge.rs` — merge operations and conflict handling helpers.
- `remote.rs` — remote inspection and synchronization helpers.
- `stash.rs` — stash management.
- `status.rs` — working tree status aggregation.
- `tests/` — integration-style tests for the git module.

## Maintenance
- Keep git commands batched through shared helpers to ensure consistent error handling.
- Add new helpers behind thin abstractions so the UI can stay platform-neutral.
- Extend tests in `tests/` whenever adding new commands or edge cases.
