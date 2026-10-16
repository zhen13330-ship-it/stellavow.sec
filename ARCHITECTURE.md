# System Architecture

A high-level, **code-free** view of how the AI-assisted pentesting system is structured.

---

## Design Goal

Build a **stable AI security subject** whose concrete capabilities are **modular and pluggable**.

- The **subject** (reasoning, context, memory, planning, execution, decision) is stable.
- Concrete abilities come from **Skill / Plugin / Module**.
- New tools and new AI capabilities slot in as **equipment** — no need to rebuild the system.

This is **not** a workflow engine, and **not** a monolithic tool with everything baked in.

---

## Layered Architecture

```
                    AI-Pentest-System
                          │
            ┌─────────────┴─────────────┐
            │     CORE (the subject)     │
            │   系统主体 · 稳定不变       │
            │                            │
            │  ┌────────────┐ ┌────────┐ │
            │  │AI Reasoning│ │Context │ │
            │  │ 思考推理    │ │ 上下文  │ │
            │  └────────────┘ └────────┘ │
            │  ┌────────────┐ ┌────────┐ │
            │  │  Memory    │ │Planning│ │
            │  │ 经验记忆    │ │  规划   │ │
            │  └────────────┘ └────────┘ │
            │  ┌────────────┐ ┌────────┐ │
            │  │ Execution  │ │Decision│ │
            │  │   执行     │ │  决策   │ │
            │  └────────────┘ └────────┘ │
            └─────────────┬─────────────┘
                          │
            ┌─────────────▼─────────────┐
            │   SECURITY INTELLIGENCE    │
            │       安全智能层            │
            │                            │
            │  • Asset understanding     │
            │    资产理解                │
            │  • Technical analysis      │
            │    技术分析                │
            │  • Risk assessment         │
            │    风险判断                │
            │  • Attack path analysis    │
            │    攻击路径分析            │
            └─────────────┬─────────────┘
                          │
            ┌─────────────▼─────────────┐
            │    CAPABILITY LAYER        │
            │        能力层              │
            │                            │
            │   Skill    Plugin   Module │
            └─────────────┬─────────────┘
                          │
            ┌─────────────▼─────────────┐
            │      TOOL / EXTERNAL       │
            └─────────────┬─────────────┘
                          │
            ┌─────────────▼─────────────┐
            │     EXTERNAL WORLD         │
            │       外部世界             │
            └────────────────────────────┘
```

---

## Core — The Stable Subject

The Core is the **AI security subject**. It does not change when new tools appear. It owns:

| Component | Role |
|-----------|------|
| **AI Reasoning** | 思考推理 — thinks through each step |
| **Context** | 上下文 — holds current task state |
| **Memory** | 经验记忆 — stores what worked before |
| **Planning** | 规划 — breaks objectives into actions |
| **Execution** | 执行 — drives capabilities |
| **Decision** | 决策 — chooses the next move |

> The subject **understands, analyzes, and decides**. It does not bake in any specific security capability.

---

## Security Intelligence Layer

Sits between the subject and capabilities. Translates generic reasoning into **security-specific judgement**:

- **Asset understanding** — what is the target, what does it expose?
- **Technical analysis** — what technology is in play, what are its weaknesses?
- **Risk assessment** — how severe is each finding?
- **Attack path analysis** — what sequence of actions could reach the goal?

---

## Capability Layer — Pluggable Equipment

This is where **concrete abilities** live. Three plugin types:

| Type | Purpose |
|------|---------|
| **Skill** | A reusable, self-contained know-how unit (e.g. "how to run sqlmap") |
| **Plugin** | An integration with an external tool or service |
| **Module** | A larger capability block (a full security domain) |

When a new tool or a new AI capability emerges, it is added here — as **equipment** — without touching the Core.

---

## Tool / External → External World

Capabilities talk to the outside world through tools — scanners, frameworks, APIs, databases. The Core never reaches out directly; it always goes through a capability.

---

## Why This Structure

| If it were... | The problem |
|---------------|-------------|
| A **workflow engine** | Every new task needs a new flow; the system can't reason |
| A **monolithic tool** | New capability = rewrite the whole thing |
| **This design** | The subject stays stable; capabilities are equipment you swap in |

The subject provides **intelligence**. The plugins provide **capability**.
