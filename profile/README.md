# Zikra — Persistent Memory for Claude Code

> Claude forgets everything when a session ends. Zikra fixes that — permanently, on your machine.

Zikra is a self-hosted memory layer for Claude Code. Every decision, error, and project context you generate gets stored in PostgreSQL with pgvector and surfaced automatically in future sessions. No cloud. No SaaS. Your data stays where you put it.

---

## Which variant is right for you?

| Feature | **Zikra** (Full) | **Zikra Lite** | claude-mem | supermemory |
|---|---|---|---|---|
| Self-hosted | ✅ | ✅ | ✅ | ❌ |
| Backend | PostgreSQL + pgvector | SQLite | SQLite/file | Cloud |
| Vector / semantic search | ✅ | ✅ | ❌ | ✅ (cloud) |
| Webhook support | ✅ n8n | ❌ | ❌ | ❌ |
| n8n integration | ✅ native | ❌ | ❌ | ❌ |
| Confidence decay | ✅ | ✅ | ❌ | ❌ |
| Free | ✅ | ✅ | ✅ | Freemium |

---

## Quick Start

**Zikra (Full) — n8n + PostgreSQL + pgvector:**
```
Fetch https://raw.githubusercontent.com/getzikra/zikra/main/prompts/g_zikra.md and follow every instruction in it.
```

**Zikra Lite — SQLite + FastAPI, ready in 60 seconds:**
```
Fetch https://raw.githubusercontent.com/getzikra/zikra-lite/main/prompts/g_zikra_lite.md and follow every instruction in it.
```

---

## Repos

| Repo | Description |
|---|---|
| [getzikra/zikra](https://github.com/getzikra/zikra) | Full stack: n8n workflows + PostgreSQL + pgvector + MCP server |
| [getzikra/zikra-lite](https://github.com/getzikra/zikra-lite) | Lightweight: SQLite + FastAPI + MCP server |
| [zikra.dev](https://zikra.dev) | Docs and onboarding |

---

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Stars — Zikra](https://img.shields.io/github/stars/getzikra/zikra?style=flat&label=zikra%20stars)](https://github.com/getzikra/zikra)
[![Stars — Zikra Lite](https://img.shields.io/github/stars/getzikra/zikra-lite?style=flat&label=zikra-lite%20stars)](https://github.com/getzikra/zikra-lite)
[![Last Commit](https://img.shields.io/github/last-commit/getzikra/zikra)](https://github.com/getzikra/zikra/commits/main)

---

Built for developers who want memory that stays on their machine.

