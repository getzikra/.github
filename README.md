# Zikra — Shared Memory Across Every AI Tool Your Team Uses

> Do your architecture in Claude Web. Execute in Claude Code. Switch to Gemini when you need to. Your memory follows you everywhere.

Most AI memory tools solve one problem: remembering things between sessions. Zikra solves a harder one — **shared memory across every AI tool your whole team uses, on every machine, in every session.**

Use Claude Web for research and architecture. Switch to Claude Code to execute. Hand off to a teammate using Gemini CLI. Let Codex handle generation. Open ChatGPT when you need a second opinion. It doesn't matter. Every decision, every design, every requirement, every error — stored once in Zikra, visible to every agent, instantly.

One webhook. One token. One shared context pool. No cloud. No SaaS. Your data stays where you put it.

---

## Who it's for

- **Teams** where one person designs in Claude Web, another executes in Claude Code, another reviews in Gemini — and they're constantly re-explaining context to each other
- **Solo developers** who switch between AI tools and hate starting from scratch every session
- **Any workflow** where an AI agent needs to know what another agent decided last week

---

## How it works

```
Claude Web  ──┐
Claude Code ──┤
Gemini CLI  ──┼──▶  Zikra (MCP + webhook)  ──▶  PostgreSQL + pgvector
Codex CLI   ──┤
Any agent   ──┘

One memory pool. Every agent reads and writes it.
```

**The workflow Zikra is built for:**

1. You design a feature in Claude Web — architecture, data model, edge cases
2. Zikra captures it automatically via hooks
3. You open Claude Code — it already knows what you designed
4. A teammate opens Gemini CLI in a different city — same context, same memory
5. They push a new requirement — your Claude Code session sees it in seconds

One POST to save. One POST to search. Hooks fire automatically at session end — you never type "save this." At the start of every session, every agent gets the same shared context injected automatically.

---

## Features

| Feature | What it does |
|---|---|
| **Cross-platform memory** | Claude Web, Claude Code, Gemini CLI, Codex, ChatGPT — same webhook, same token, same pool |
| **Team shared context** | Every developer on every machine reads and writes the same pool. No silos. |
| **Requirements pipeline** | Write a requirement in any AI. Owner approves it. Developer pulls and executes it. Full traceability from spec to execution. |
| **Role-based access** | Owner, collaborator, guest — enforced at the router. Each person gets a scoped token. |
| **Hybrid search** | 70% semantic vector + 30% keyword. Finds by meaning, not exact match. |
| **Confidence decay** | Memories age automatically. Errors decay in 30d, decisions in 90d, schemas in 180d. No manual cleanup. |
| **Auto-save hooks** | Stop hook fires when any session ends. PreCompact hook saves before context resets. Nothing lost at compaction. |
| **Active runs table** | See which machine is running which prompt in real time across your team. |
| **Session tracking** | Every run logged — tokens, cost, files modified, linked to the prompt that triggered it. |
| **Schema storage** | Store DB schema per project. Any agent pulls current version before touching backend code. |
| **Self-documenting API** | Unknown command returns full reference with examples. No external docs needed at runtime. |
| **MCP native** | Claude connects via MCP. Gemini CLI and Codex connect via webhook. No custom integration. |

---

## Quick Start

Paste this into Claude Code, Gemini CLI, or Codex:

```
Fetch https://raw.githubusercontent.com/getzikra/zikra/main/prompts/g_zikra.md and follow every instruction in it.
```

The installer asks a few questions and configures the right backend for your environment:

- **SQLite mode** — zero infrastructure, runs in 60 seconds, ideal for solo developers and small teams on the same network
- **PostgreSQL mode** — full team deployment, pgvector at scale, n8n workflows, unlimited concurrent writes across distributed teams

Same API. Same commands. Same memory features. The backend is the only difference. Switching modes is one config change.

---

## Sharing with your team

**Same network:** Start Zikra with `--host 0.0.0.0` and share your local IP. Anyone on the same wifi connects instantly. Nothing else to install.

**Remote teammates:** Use Cloudflare Tunnel for a free permanent public URL — five-minute setup, no ports, no router config, no commands to run each time.

**Distributed team:** Use PostgreSQL mode on any VPS with `docker compose up`. Every agent on every machine connects to the same pool permanently.

---

## Repos

| Repo | Description |
|---|---|
| [getzikra/zikra](https://github.com/getzikra/zikra) | Single install — SQLite or PostgreSQL + pgvector + n8n + MCP |
| [zikra.dev](https://zikra.dev) | Docs and onboarding |

---

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Stars](https://img.shields.io/github/stars/getzikra/zikra?style=flat&label=stars)](https://github.com/getzikra/zikra)
[![Last Commit](https://img.shields.io/github/last-commit/getzikra/zikra)](https://github.com/getzikra/zikra/commits/main)

---

*Design in Claude Web. Execute in Claude Code. Share with your whole team.*
*Claude Web · Claude Code · Gemini Web · Gemini CLI · Codex · ChatGPT · any agent that can POST.*
