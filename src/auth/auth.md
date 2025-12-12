# `src/auth/`

Authentication helpers and state for GitSpace. Use this module to manage credentials and integrate provider-specific flows.

## Responsibilities
- Provide auth-related types and traits used across the UI and Git layers.
- Centralize token handling or provider adapters once implemented.
- Maintain isolation from UI rendering concerns; expose simple APIs for the frontend.

## Maintenance
- Keep flows opt-in and clearly communicate what data is stored or transmitted.
- If adding providers (e.g., GitHub, GitLab), document required scopes and storage locations here.
