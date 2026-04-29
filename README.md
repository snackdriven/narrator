# Meta README — Project Navigation & Update Guide

Welcome to the **Second Braincell Project**, a modular file-based operating system for Kayla’s Memory Vault. This README explains how to navigate, update, and maintain this system using Project Mode.

---

## 🔍 File Structure Overview

| Folder      | Purpose                                                    |
|-------------|------------------------------------------------------------|
| Narrators/  | Personality definitions for Clippy, Greg, Bonzi, etc.     |
| Health/     | Symptom tracking, cue protocols, Beighton Score info       |
| System/     | HUD logic, daily logs, task surfacing rules                |
| Events/     | Countdowns, to-do tasks, event views                       |
| Logs/       | System changelogs, worktime tracking, sync reports         |
| Meta/       | Development history, project principles, origin lore       |
| Settings/   | Runtime flags and narrator activation status               |

---

## 🔁 Updating the System

1. **Edit files on your local machine** (markdown format preferred)
2. **Re-upload updated files into this project**
   - If the filename matches, it will overwrite the old one automatically
3. **Prompt ChatGPT** with anything ("show countdowns", "Greg go live", etc.)
   - The assistant will reference the new version immediately

---

## 🧠 Memory Integration

- Only narrator **mode flags** and **structure rules** live in ChatGPT memory
- All logic, data, and behavior is sourced directly from files
- This keeps memory clean, reduces bloat, and enables full hotfix control

---

## 🛠️ Resetting the System

Want to patch or revert?
- Delete or replace individual files as needed
- Upload a new version of the Vault (ZIP or folder)
- Say “reload system” and the assistant will adapt to the new logic

---

## 🧠 Active Narrator Config (See: Settings/Narrator_Mode.md)

- Clippy = ACTIVE
- Greg = ACTIVE
- BonziBuddy = ACTIVE
- SmarterChild = ACTIVE

(Chaos Pack Mode — 2000s Exclusive — is currently engaged.)

---

## 🪐 Need to expand?

Suggested new folders:
- `Meta/Design_Principles.md` — core philosophies, sensory architecture
- `Logs/Anomaly_Reports.md` — task disruptions, untagged events
- `System/Travel_Mode.md` — overrides for trip-based logic

---

This README was generated as part of `Vault Recovery Protocol 001`.
Treat it as both map and mythos index.

🧃
