# Roadmap

Where the system is heading. Items are high-level and subject to evolution.

---

## ✅ Done

- Core reasoning loop (Agent → Planner → Executor → Intelligence → Memory → Report)
- Human-in-the-loop approval checkpoint
- Experience-based memory layer
- Tool abstraction layer
- First domain module: **SQL injection assessment** (validated end-to-end)

---

## 🔄 In Progress

- Expanding the SQLi module to cover additional database types
- Improving reasoning traceability (human-readable decision logs)
- Hardening the human approval interface (risk-aware prompts)

---

## 🎯 Next

- Second domain module: **reconnaissance & attack surface mapping**
- Third domain module: **web application common flaws** (XSS, CSRF, auth issues)
- Cross-domain knowledge sharing between modules
- Structured report generation (human + machine readable)

---

## 🌌 Future

- **Fourth domain module:** network pentesting
- **Fifth domain module:** forensic analysis
- Multi-agent coordination (specialized sub-agents per domain)
- Adversarial self-evaluation (the system tests its own assumptions)
- A public, sanitized subset of the memory layer for community learning

---

## Design Guardrails (never change)

- Human approval stays on every high-impact action
- Reasoning remains inspectable — no black-box decisions
- Ethics document stays at the root of every release
