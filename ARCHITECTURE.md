# System Architecture

A high-level, **code-free** view of how the AI-assisted pentesting system is structured.

---

## Design Goal

Build a security reasoning platform where **security domains are replaceable capabilities** on top of a reusable **intelligence core**. The system is not limited to vulnerability research — its architecture is general enough to host any security domain as a module.

---

## Layered Architecture

```
┌─────────────────────────────────────────────────────┐
│                   HUMAN-IN-THE-LOOP                 │
│        (approval checkpoint for every action)       │
└──────────────────────────┬──────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────┐
│  1. AGENT LAYER                                     │
│     Task understanding · Workflow coordination      │
│     Decision execution                              │
└──────────────────────────┬──────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────┐
│  2. PLANNER LAYER                                   │
│     Action planning · Strategy generation           │
│     Task decomposition                              │
└──────────────────────────┬──────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────┐
│  3. EXECUTOR LAYER                                  │
│     Tool execution · Result collection              │
│     Operation control                               │
└──────────────────────────┬──────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────┐
│  4. INTELLIGENCE LAYER                              │
│     Observation analysis · Security reasoning       │
│     Knowledge integration                           │
└──────────────────────────┬──────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────┐
│  5. MEMORY LAYER                                    │
│     Experience storage · Reasoning history          │
│     Long-term context                               │
└──────────────────────────┬──────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────┐
│  6. REPORT LAYER                                    │
│     Result organization · Security findings         │
│     Structured output                               │
└─────────────────────────────────────────────────────┘
```

---

## How a Task Flows

1. **Agent** receives the human objective and context
2. **Planner** breaks it into a sequence of actions
3. **Executor** runs each action through available tooling
4. **Intelligence** interprets observations and decides the next step
5. **Memory** stores what worked (and what didn't) for future runs
6. **Report** packages findings for the human

Each cycle can loop back to the Planner — the system **reasons dynamically**, it doesn't follow a fixed script.

---

## Intelligence Core vs. Domain Modules

```
            SECURITY INTELLIGENCE CORE
                       │
        ┌──────────────┼──────────────┐
        │              │              │
   Domain Module  Domain Module  Domain Module
  (Pentesting)    (Recon)        (Forensics)
        │              │              │
        └──────────────┼──────────────┘
                       │
              SECURITY CAPABILITIES
```

The core provides reasoning, memory, and orchestration. Domain modules plug in on top — so adding a new security capability doesn't require rewriting the engine.

---

## Evolution Infrastructure

The system is designed to **evolve over time** with:

- **Version awareness** — knows its own state across iterations
- **State awareness** — can recover from interruptions
- **Recovery capability** — resumes mid-task without losing context
- **Evolution tracking** — logs how its reasoning improves

---

## Key Design Decisions

- **Human approval gates every high-impact action** — autonomy serves the human, never the reverse
- **Observations are structured, not free-form** — the Intelligence layer consumes clean, typed data
- **Memory is experience-based** — the system learns from what actually succeeded, not from static rules
- **Tooling is abstracted** — the Executor speaks a common interface; tools can be swapped
