# `src/ui/tests/`

Tests for UI behaviors and shared UI state.

## Purpose
- Validate panel wiring, navigation, and layout assumptions.
- Guard telemetry/event emission from the UI surfaces.
- Provide regression coverage for UI-specific bugs or layout changes.

## Maintenance
- Prefer lightweight UI state tests and avoid heavy graphics assertions.
- Keep helpers reusable so new panels can share setup code.
