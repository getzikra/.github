# Zikra — Shared Memory for Claude Code, Gemini CLI & Codex

> Your team uses different AI tools. None of them share memory by default. Zikra fixes that.

Zikra is a self-hosted memory layer that works across **Claude Code, Gemini CLI, Codex, and any agent that can send a POST request**. Decisions, errors, architecture notes, and requirements are stored once and surfaced automatically — to every agent, on every machine, for every team member.

One webhook. One token. One shared context pool. No cloud. No SaaS. Your data stays where you put it.

---

## Who it's for

- **Teams** where one person uses Claude Code, another uses Gemini CLI, another uses Codex — and they're constantly re-explaining context to each other
- **Solo developers** who switch between AI tools and hate starting from scratch every session
- **Any workflow** where an AI agent needs to know what another agent decided last week

---

## How it works
Claude Code ──┐
Gemini CLI  ──┼──▶  Zikra (MCP + webhook)  ──▶  PostgreSQL + pgvector
Codex CLI   ──┘          ↑
Any agent ────────────────┘    One memory pool. Every agent reads and writes it.

One POST to save. One POST to search. Hooks fire automatically at session end — 
you never type "save this." At the start of every session, every agent gets 
the same shared context injected automatically.

---

## Features

| Feature | What it does |
|---|---|
| **Cross-platform memory** | Claude Code, Gemini CLI, Codex, ChatGPT — same webhook, same token, same memory pool |
| **Team shared context** | Every developer on every machine reads and writes the same pool. No silos. |
| **Role-based access** | Owner, collaborator, guest — enforced at the router. Each person gets a scoped token. |
| **Hybrid search** | 70% semantic vector + 30% keyword. Finds by meaning, not exact match. |
| **Confidence decay** | Memories age automatically. Errors decay in 30d, decisions in 90d, schemas in 180d. No manual cleanup. |
| **Requirements pipeline** | Write a requirement in any AI. Owner promotes it. Developer pulls and executes it. Full traceability. |
| **Auto-save hooks** | Stop hook fires when any session ends. PreCompact hook saves before context resets. |
| **Active runs table** | See which machine is running which prompt in real time across your team. |
| **Session tracking** | Every run logged — tokens, cost, files modified, linked to the prompt that triggered it. |
| **Schema storage** | Store DB schema per project. Any agent pulls current version before touching backend code. |
| **Self-documenting API** | Unknown command returns full reference with examples. No external docs needed. |
| **MCP native** | Claude connects via MCP trigger. No custom integration. |

---

## Quick Start

**Zikra — PostgreSQL + pgvector + n8n (recommended for teams):**
Fetch https://raw.githubusercontent.com/getzikra/zikra/main/prompts/g_zikra.md and follow every instruction in it.

**Zikra Lite — SQLite + FastAPI, ready in 60 seconds (great for solo or small teams):**
Fetch https://raw.githubusercontent.com/getzikra/zikra-lite/main/prompts/g_zikra_lite.md and follow every instruction in it.

Both variants have the same full feature set and identical API surface. 
The difference is infrastructure — SQLite vs PostgreSQL. 
**Upgrade from Lite to Full is one URL change.**

---

## Zikra vs Zikra Lite

| | **Zikra** | **Zikra Lite** |
|---|---|---|
| Backend | PostgreSQL + pgvector | SQLite |
| Concurrent team writes | ✅ Unlimited | Limited |
| Scale | Billions of rows | Millions of rows |
| n8n workflows + scheduling | ✅ | ❌ |
| Automated decay via cron | ✅ | Manual |
| Setup time | 30–60 min | ✅ 60 seconds |
| All memory features | ✅ | ✅ |
| Full API surface | ✅ | ✅ |
| Free | ✅ MIT | ✅ MIT |

---

## Repos

| Repo | Description |
|---|---|
| [getzikra/zikra](https://github.com/getzikra/zikra) | Full stack: PostgreSQL + pgvector + n8n + MCP server |
| [getzikra/zikra-lite](https://github.com/getzikra/zikra-lite) | Lightweight: SQLite + FastAPI + MCP server |
| [zikra.dev](https://zikra.dev) | Docs and onboarding |

---

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Stars — Zikra](https://img.shields.io/github/stars/getzikra/zikra?style=flat&label=zikra%20stars)](https://github.com/getzikra/zikra)
[![Stars — Zikra Lite](https://img.shields.io/github/stars/getzikra/zikra-lite?style=flat&label=zikra-lite%20stars)](https://github.com/getzikra/zikra-lite)
[![Last Commit](https://img.shields.io/github/last-commit/getzikra/zikra)](https://github.com/getzikra/zikra/commits/main)

---

*One memory. Every agent. Every team member.*
