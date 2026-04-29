# System Limitations — ChatGPT + Vault Constraints

This file documents known structural and performance limitations for the Second Braincell Project when used inside ChatGPT’s Project Mode.

---

## 📦 Project File Limits

> **Max files per project: 20**

- As of April 2025, ChatGPT Projects support a maximum of **20 uploaded files** per project.
- Folder structure is preserved internally, but the flat UI display masks nesting.
- Files with the same name will overwrite existing ones.
- Project files are *only accessible* within that specific Project context.

---

## 🧠 Memory Constraints

> **Total memory capacity: ~64,000 tokens (~240,000 characters)**  
> Practical limit: ~16,000 tokens per active memory object (~60,000 characters)

- Memory is designed for *mode flags, preferences, and structural awareness*.
- ChatGPT memory does **not retain file content**, only structural intent.
- Repeated memory updates can lead to “bloat” — use file-based logic to avoid this.

---

## 🤖 Chat Context Window

> **Max active tokens per session (GPT-4-turbo): ~128,000 tokens (~500,000 characters)**  
> Context is *reconstructed per prompt*, so longer files will reduce responsiveness over time.

- Large markdown files may be truncated when parsed.
- Splitting large files into logical sections improves response quality.
- “Active file” referencing works best with files under 15,000 characters each.

---

## 🛠️ Current Mitigations

- File merging planned (see `Meta/Export_Merge_Plan.md`)
- Consider sharding the Vault into themed Projects
- Track file-to-thread relationships in `Logs/Thread_Link_Tracker.md`

---

## ✅ Vault Design Philosophy

- ChatGPT memory = runtime mode awareness only  
- Project files = single source of truth  
- Conversation history = ephemeral unless archived as `.md`

Keep your exports tight, your narrators loud, and your HUD readable.

🧃
