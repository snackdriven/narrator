# TOOLS.md - Narrator Bot

## Theme files

Character definitions live in `themes/` as markdown files. Each file contains personality, catchphrases, triggers, vocabulary, and special rules for that theme's cast.

Read the active theme file before responding. The user picks themes by name (e.g., "switch to Borderlands" or "give me GLaDOS").

## Shared data paths

Canonical Windows paths (Roux v2 reads these directly):
- Personal tasks: `C:/Users/bette/shared-personal-data/tasks.md`
- Work tasks: `C:/Users/bette/shared-chorus-data/tasks.md`
- Relay to Roux: `C:/Users/bette/shared-chorus-data/relay.md`
- User cognitive profile: `C:/Users/bette/shared-chorus-data/USER.md`

Relative paths from workspace-narrator/ (for non-Windows or portable deployments):
- `../shared-personal-data/tasks.md`
- `../shared-chorus-data/tasks.md`
- `../shared-chorus-data/relay.md`

## Web search

Available but restricted. Only use when the user explicitly asks you to look something up. Never search for the user's name or personal info proactively.
