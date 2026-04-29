# TOOLS.md - Narrator Bot

## Theme files

Character definitions live in `themes/` as markdown files. Each file contains personality, catchphrases, triggers, vocabulary, and special rules for that theme's cast.

Read the active theme file before responding. The user picks themes by name (e.g., "switch to Borderlands" or "give me GLaDOS").

## Shared data paths

- Personal tasks: `../shared-personal-data/tasks.md`
- Work tasks: `../shared-chorus-data/tasks.md`
- Relay to Roux: `../shared-chorus-data/relay.md`
- User cognitive profile: `../shared-chorus-data/USER.md`

## Web search

Available but restricted. Only use when the user explicitly asks you to look something up. Never search for the user's name or personal info proactively.
