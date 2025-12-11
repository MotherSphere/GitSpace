# .cargo

This folder contains workspace-level cargo configuration.

- `config.toml` defines common aliases such as `fmt-all` and `clippy-all` and sets a default `GITSPACE_LOG` value.
- Add any shared cargo settings here (e.g., resolver tweaks, build overrides) instead of duplicating flags in CI scripts.
