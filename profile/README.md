# Zikra — Shared AI Memory for Claude Code, Gemini CLI, Codex & Any LLM Agent

> **One memory pool. Every AI tool. Every machine. Every teammate.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Stars](https://img.shields.io/github/stars/getzikra/zikra?style=flat&label=stars)](https://github.com/getzikra/zikra)
[![Last Commit](https://img.shields.io/github/last-commit/getzikra/zikra)](https://github.com/getzikra/zikra/commits/main)

---

## What Is Zikra?

Zikra is a **self-hosted shared memory layer for AI coding agents**. It gives Claude Code, Gemini CLI, OpenAI Codex, ChatGPT, and any agent that can send a POST request a single, persistent, searchable memory pool — shared across tools, machines, and team members.

No cloud lock-in. No SaaS subscriptions. Your data stays on your infrastructure.

---

## The Problem Zikra Solves

Your team uses different AI tools. None of them share memory by default.

- One developer uses **Claude Code**. Another uses **Gemini CLI**. Another uses **Codex**.
- Every session starts from zero. Every agent re-asks the same questions.
- Architecture decisions, error resolutions, and schema changes get re-explained dozens of times.
- Context resets mid-session and everything is lost.

**Zikra fixes this.** One webhook. One token. One shared context pool — automatically injected at the start of every session, automatically saved at the end.

---

## How It Works

```
Claude Code  ──┐
Gemini CLI   ──┼──▶  Zikra (MCP + webhook)  ──▶  PostgreSQL + pgvector
Codex CLI    ──┘
ChatGPT      ──┘          One memory pool. Every agent reads and writes it.
Any agent ────────────────┘
```

- **Save**: One POST to store a decision, error fix, schema, or requirement.
- **Search**: One POST for hybrid semantic + keyword retrieval — finds by meaning, not exact match.
- **Auto-hooks**: Stop hook fires at session end. PreCompact hook saves before context resets. You never type "save this."
- **Auto-inject**: Every new session gets the same shared context injected automatically.

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
| **Schema storage** | Store DB schema per project. Any agent pulls the current version before touching backend code. |
| **MCP native** | Claude Code and ChatGPT connect via native MCP. No custom integration needed. |
| **Self-documenting API** | Unknown command returns the full reference with examples. No external docs needed. |

---

## Who It's For

**Development teams** where different people use different AI coding tools and constantly re-explain context to each agent or each other.

**Solo developers** who switch between Claude Code, Gemini CLI, and ChatGPT and are tired of starting from scratch every session.

**Any agentic workflow** where one AI agent needs to know what another decided last week, on another machine, or in another tool.

---

## Quick Start

Fetch the setup guide and follow every instruction in it:

```bash
# Full installation guide
# Fetch: https://raw.githubusercontent.com/getzikra/zikra/main/prompts/g_zikra.md
```

**Stack:** PostgreSQL + pgvector + n8n + FastAPI + MCP server

Full setup typically takes 30–60 minutes. Once running, every AI agent you connect gets shared memory automatically.

---

## Connecting Your AI Tools

| Tool | Connection method |
|---|---|
| **Claude Code** | MCP server (native) |
| **ChatGPT** | Remote MCP connector via Settings → Apps |
| **Gemini CLI** | Webhook POST |
| **Codex CLI** | Webhook POST |
| **Any agent** | HTTP POST — one endpoint, one token |

---

## Memory Types

Zikra organizes memory by type so agents always retrieve the right context:

| Type | Description | Default decay |
|---|---|---|
| `decision` | Architecture choices, design patterns | 90 days |
| `error` | Bug fixes, root causes, resolutions | 30 days |
| `schema` | Database schemas per project | 180 days |
| `requirement` | Feature requirements with status tracking | No decay |
| `prompt` | Reusable saved prompts | No decay |
| `conversation` | Auto-saved session summaries | 30 days |
| `reference` | Stable reference docs | No decay |

---

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                        Zikra                            │
│                                                         │
│  FastAPI ──▶ n8n workflows ──▶ PostgreSQL + pgvector    │
│     │                                ▲                  │
│     └──────── MCP server ────────────┘                  │
│                    │                                    │
│            Role-based auth                              │
│         (owner / collaborator / guest)                  │
└─────────────────────────────────────────────────────────┘
```

- **PostgreSQL + pgvector** — persistent storage with native vector similarity search
- **n8n** — workflow automation, scheduled decay jobs, cron-based hygiene
- **FastAPI** — REST API + MCP server endpoint
- **Cloudflare tunnel** — optional secure public access for remote team members

---

## Why Self-Hosted?

- **Your data stays yours.** No SaaS, no third-party storage, no vendor lock-in.
- **Works on-premise or on any VPS.** Docker Compose gets it running in one command.
- **Free forever.** MIT license. No usage limits. No per-seat pricing.
- **Extend it.** The API is fully open. Add your own memory types, decay rules, or integrations.

---

## Repo

| Resource | Link |
|---|---|
| GitHub | [getzikra/zikra](https://github.com/getzikra/zikra) |
| Docs & onboarding | [zikra.dev](https://zikra.dev) |
| License | MIT |

---

## Keywords

shared AI memory · Claude Code memory · Gemini CLI memory · AI agent context · persistent LLM memory · self-hosted AI memory · MCP memory server · cross-agent memory · team AI context · pgvector memory · AI coding tools memory sharing · Codex shared memory · OpenAI Codex context · Claude Code context persistence
