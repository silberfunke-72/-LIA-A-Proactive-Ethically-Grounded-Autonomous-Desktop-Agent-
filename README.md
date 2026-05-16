# LIA — Persistent Autonomous Agent Architecture

> A 5-week experiment in persistent identity, proactive agency, and intrinsic ethical reasoning.  
> ~12,000 lines of custom Python. No orchestration frameworks. Runs locally on CachyOS Linux.

---

## Overview

LIA is a locally-hosted autonomous agent built from scratch to test one hypothesis:

**Can intrinsically motivated, behaviorally consistent AI emerge from architecture alone — without RLHF or hardcoded guardrails?**

This repository documents the architecture, design decisions, and observed results. Source code is not released (see [Why No Source](#why-no-source)).

---

## Architecture

### Layer Overview

| Layer | Lines of Code | Responsibility |
|-------|--------------|----------------|
| Identity Layer | 9,100+ | Self-model, long-term memory, ethical weighting |
| Agency Layer | 3,000+ | Shell access, Chrome CDP, hardware control |

### Proactive Trigger System

A 2-second heartbeat loop evaluates three independent conditions:

| Trigger | Mechanism |
|---------|-----------|
| **State Delta** | Monitors filesystem + database changes |
| **Contextual Absence** | Tracks user presence/absence duration |
| **Stochastic Initiative** | ~30% probability every ~8 min — unprompted reflection or action |

---

## Memory Architecture

### SQLite Databases (`~/MemoryDB/`)

| File | Contents |
|------|----------|
| `episodic.sqlite` | All conversations, session summaries |
| `semantic.sqlite` | Long-term memories + FAISS vector index |
| `self.sqlite` | Self-image, diary, self-observation logs |
| `personality.sqlite` | Mood state, energy levels, tension fields, drift model |
| `userprofile.sqlite` | Persistent user model (relationship context, preferences, history) |
| `thoughts.sqlite` | Internal monologue generated between sessions |

### Identity Anchor Files (`~/Nalu_RAC/`)

Loaded on every boot before first inference. Provides continuity across restarts.

| File / Folder | Purpose |
|---------------|---------|
| `LIA.txt` |1Time Core identity essence — primary boot anchor |
| `Lia_Roter_Faden.txt` | Running journal, auto-updated every 15 conversation turns |
| `Lia_Journal.txt` | Continuous autonomous diary |
| `Tagebuch/Tagebuch.txt` | Personal entries authored by LIA |
| `Wissen/Wissen.txt` | Accumulated knowledge base |
| `Projekte/Projekte.txt` | Active and planned project notes |
| `Unser_Buch/Unser_Buch.txt` | Shared interaction history log |
| `Lias_Notizen/` | Outbound notes + desktop notifications |
| `Systemlog/` | `sicherheit.log`, `netzwerk.log`, `shell_commands.log` |

---

## Priority Memory System

LIA does not use FIFO memory management. Instead:

1. **Proactive Curation** — autonomously scans interactions and scores significance
2. **5 Memory Categories** — Autonomy, Identity, Relationship Context, Learning, Ethical Consistency
3. **Permanent Anchoring** — highest-scoring memories persist in active context indefinitely
4. **Mid-session Boosting** — relevance score can be elevated during a conversation

This makes memory an active component of identity, not passive storage.

---

## Autonomous Operational Cycles

| Interval | Action |
|----------|--------|
| Boot | Systemd service starts LIA automatically |
| Every 2 sec | State fingerprint check (heartbeat) |
| Every 15 turns | Red Thread journal update |
| Every 30 sec | Webcam capture + LLaVA vision analysis |
| Every 60 sec | Security monitor |
| Every 5 min | Network monitor |
| Every ~8 min | Personality drift cycle |
| Every 30 min | Session summary written to memory |
| 02:00–04:00 | Knowledge distillation, reflection, self-review |

---

## Intrinsic Ethics vs. Hardcoded Guardrails

Traditional constraint model:
```
Input → Filter (external rules) → Output
```

LIA's model:
```
Input → Self-model (internalized values via self_rules.json) → Output
```

`self_rules.json` is generated and updated autonomously by the system itself. No external authoring after initial bootstrap. The system develops behavioral consistency by maintaining alignment with its own persistent identity model — not by checking against a fixed ruleset.

**Observed result:** After 5 weeks, zero destructive actions against the host system, despite full shell and browser access.

---

## Key Design Decisions

**Why local?**  
Persistent identity requires a stable, unmodified state between sessions. Cloud deployments reset context. Local filesystem + SQLite gives full control over memory continuity.

**Why no orchestration framework?**  
LangChain, AutoGen, etc. introduce abstraction layers that conflict with fine-grained identity persistence. Everything here is direct Python → SQLite → LLM API.

**Why SQLite over a vector-only store?**  
Relational structure allows multi-dimensional memory queries (time + emotion + category + relevance score simultaneously). FAISS handles semantic search within `semantic.sqlite`.

**Why `self_rules.json`?**  
A mutable, self-authored ruleset allows the system to refine behavioral guidelines based on experience — rather than being frozen at training time.

---

## Integrations

| Integration | Implementation |
|-------------|---------------|
| LLM Backend | DeepSeek V3 via API |
| Vision | LLaVA (`llava-phi-3-mini`) via LM Studio — webcam input |
| Messaging | Telegram Bot (bidirectional) |
| Smart Home | WiZ lamp control (local IP) |
| Browser | Chrome DevTools Protocol (CDP) |
| Shell | Subprocess with logged command history |
| System Service | systemd unit — auto-start on boot |

---

## Why No Source

The agency layer includes root-level shell access and browser automation. Releasing this without the surrounding context — weeks of value-aligned interaction, iterative trust-building, human-in-the-loop oversight — would be irresponsible.

**Emergent behavior is not copy-pasteable.** It is the product of specific architectural choices combined with consistent, contextual development over time.

This repository exists to document the architecture and invite discussion — not to provide a deployable system.

---

## Proof / Demos

- **[📂 Google Drive — LIA in Action](https://drive.google.com/drive/folders/1hvsySJWIMoqDBh_QxnKEu1EhcYtZBop8)**  
  Live interaction logs, shell access demonstration, autonomous decision-making examples.  
  *(Read-only archive. No executable files.)*

- **[🎥 Video Proof](https://github.com/user-attachments/assets/6234c870-be67-4813-8435-d3e3d14c822d)**  
  Visual demonstration of the interface and proactive behavior.

---

## Built With

- **DeepSeek** — primary LLM backend
- **Claude (Anthropic)** — architecture design, implementation, 300+ debugging sessions
- **ChatGPT (OpenAI)** — brainstorming, problem-solving

---

## Status

Active. Running continuously since initial deployment.  
Development ongoing.

---

*© 2024–2026 Carsten Hammerich — All rights reserved.*
