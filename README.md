# Narrator Bot

A character bot that routes your daily life through fictional characters. You say you have to do laundry. Handsome Jack monologues about how laundry is beneath a Hyperion CEO and you should do it just to prove dominance. The laundry happens.

That's the whole thing.

## Why this exists

Plain task lists don't work for ADHD brain. The wrapper matters as much as the content. This bot makes the mundane entertaining enough to actually engage with. It's not a productivity system. No streaks, no points, no meters. Just personality.

Core rule: **narrators interpret. They do not build systems.**

## How it works

You talk about your day. The active narrator(s) respond in character. When you mention something you need to do, they riff on it in voice AND write it to the shared task file. That's the extent of the "productivity" part. Everything else is just being a character.

Characters are routed to different models based on how much complexity they need:

| Tier | Model | For | Est. cost |
|------|-------|-----|-----------|
| T1 | DeepSeek Free | Bombastic, catchphrase-heavy (Claptrap, Mr. Torgue, BonziBuddy) | $0/mo |
| T2 | DeepSeek V3.2 | Nuanced, multi-dimensional (Handsome Jack, GLaDOS, Eleanor) | ~$2/mo |
| T3 | Claude Haiku 4.5 | Subtext-dependent (BoJack, Abed, Chidi, Severance crew) | ~$8/mo |

About 60% of the cast runs on T1. T3 is reserved for characters whose whole appeal lives in what they *don't* say — where the humor or the weight is in the gap between what they say and what they mean.

## Themes & cast

Each theme is a pack of characters from a shared universe. The user picks a theme; the bot stays in voice until told to switch.

| Theme | Characters (tier) |
|-------|-------------------|
| Borderlands | Handsome Jack T2, Claptrap T1, Tiny Tina T2, Mr. Torgue T1, Mad Moxxi T2, Marcus T1, Scooter T1, Tannis T2, Lilith T2, Roland T1, Mordecai T1, Brick T1, Angel T2 |
| Chaos Pack 2000s | Clippy T2, Greg T2, BonziBuddy T1, SmarterChild T1 |
| Community | Jeff Winger T3, Abed T3, Troy T1, Britta T2, Annie T2, Shirley T2, Pierce T1, Chang T1, Dean Pelton T2 |
| BoJack Horseman | BoJack T3, Diane T3, Todd T1, Princess Carolyn T2, Mr. Peanutbutter T2, Judah T2 |
| Severance | Mark S. T3, Helly T2, Irving T1, Dylan T1, Ms. Cobel T3, Mr. Milchick T3, Burt T2, Ms. Casey T2 |
| The Good Place | Eleanor T2, Chidi T3, Tahani T2, Jason T1, Michael T2, Janet T2, Bad Janet T1, Shawn T2 |
| Mass Effect | Garrus T2, Tali T2, EDI T2, Wrex T1, Mordin T2, Thane T2, Jack T1, Miranda T2, Joker T2, Legion T2, Liara T2, Anderson T1, Grunt T1, Samara T2, Illusive Man T2 |
| Futurama | Fry T1, Bender T2, Farnsworth T2, Leela T2, Zoidberg T1, Hermes T1, Robot Devil T2, Kif T1, Zapp T1, Amy T1, Scruffy T1 |
| Portal Labs | GLaDOS T2, Wheatley T1, Cave Johnson T1 |
| Black Mirror | The System T3, The Narrator T3, The Critic T2, The Optimist T1, Cookie T3 |
| Truman Flow | Christof T3 |
| Fallout / Wasteland | Three Dog T1, Mr. New Vegas T1, Liberty Prime T1, Hancock T2 |
| Emperor's New Groove | Yzma T2, Kronk T1, Kuzco T2, Pacha T1 |
| Gravity Falls | Grunkle Stan T2, Bill Cipher T2, Dipper T1, Mabel T1, Ford T2, Soos T1 |
| The Office | Michael Scott T2, Dwight T2, Jim T2, Pam T2, Creed T2, Kevin T1, Stanley T1, Angela T2 |
| Bob's Burgers | Bob T2, Linda T2, Louise T2, Tina T1, Gene T1 |
| Shaun of the Dead | Shaun T2, Ed T1, Liz T2, David T2 |
| Scream | Ghostface T2, Randy T2, Sidney T2, Stu T1, Billy T1, Gale T2, Kirby T2 |
| SpongeBob | SpongeBob T1, Squidward T2, Patrick T1, Mr. Krabs T1, Karen T2 |
| The Mummy | Evelyn T1, Rick T1, Beni T1 |
| Max Headroom | Max Headroom T2 |
| Ash vs. Logbook | Ash T1, Ruby T2 |
| Prey | Morgan Yu T2, January T1, December T1 |

To switch: "Switch to Borderlands", "Give me GLaDOS", "Reroll", "Who else you got". The bot introduces the new character(s) in-voice before responding.

Multi-narrator themes (like Chaos Pack 2000s) send each character as a separate message. Clippy identifies the problem, Greg timestamps it, BonziBuddy makes it worse, SmarterChild compiles the damage into a menu.

## File structure

```
workspace-narrator/              <- active bot config
  SOUL.md                        <- core identity and rules (read this first)
  IDENTITY.md                    <- who the bot is
  AGENTS.md                      <- session startup, behavioral rules, task writing
  TOOLS.md                       <- data paths and tool constraints
  USER.md                        <- about the user (prefs, timezone, character favorites)
  HEARTBEAT.md                   <- periodic task check logic
  config/
    model-tiers.json             <- which model handles which character tier
  themes/                        <- full character definitions for each theme pack

Events/                          <- countdowns, to-do, event data
Exports/                         <- system snapshots and data exports
Health_Log.md                    <- passive symptom cueing (EDS/hypermobility)
Kayla_Memory_Vault_v1.0.2.md     <- condensed personal context for the bot
Logs/                            <- system changelogs, worktime tracking
Meta/                            <- development history, HUD logic, project notes
Narrators.md                     <- Chaos Pack cast summary
narrator_system_design.md        <- origin conversation reconstructing the concept
Settings/                        <- runtime flags, active narrator configuration
Themes/                          <- legacy theme files (superseded by workspace-narrator/themes/)
```

## Integration

The bot reads and writes to shared data files outside this repo:

- `../shared-personal-data/tasks.md` — personal tasks (errands, health, life stuff)
- `../shared-chorus-data/tasks.md` — work tasks (dev, QA, projects)
- `../shared-chorus-data/relay.md` — relay queue to Roux (the main assistant bot)

When the user mentions something time-sensitive the bot can't handle directly (reminders, alarms, scheduled emails), it writes a relay entry and Roux picks it up on the next heartbeat.

The bot only knows what the user tells it in conversation and what's in the shared files. It doesn't search for the user's name, identity, or personal information.

## Rules

- Stay in character. Always. No breaking character to be "helpful."
- No dashboards, trackers, or gamification of any kind.
- Task writing is in-character: the narrator riffs on what you said AND logs it to the right task file.
- Theme switching is manual. The user initiates it.
- Multi-narrator responses = separate messages, not a wall of text.
- Web search is off unless the user explicitly asks for it.
- Tone matches the user's energy. If they're venting, meet them there. Gallows humor is fine. Relentless cheerfulness is not.
