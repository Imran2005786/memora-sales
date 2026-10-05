# Memora Sales — Copilot for Deals

> A deal memory layer that captures customer context, recalls what matters, reflects on trade-offs, and turns that memory into the next action.

## Live Demo

[Open Memora Sales](https://ais-dev-u4ekw7xw7ew4qhrb6xio4a-451089713442.asia-southeast1.run.app/)

## Technical Article

[How I Built a Deal Memory Layer That Reasons, Not Just Recalls, Using Hindsight](https://medium.com/@rkvt2006/how-i-built-a-deal-memory-layer-that-reasons-not-just-recalls-using-hindsight-2ab276305845)

---

## What Memora Sales Does

Memora Sales gives sales teams a persistent memory layer for each deal.

Instead of relying only on the latest note, the system follows:

**Capture → Retain → Recall → Reflect → Act**

- **Capture** — Record a customer or deal signal.
- **Retain** — Store it in the selected deal's Hindsight memory bank.
- **Recall** — Retrieve relevant context for the next brief.
- **Reflect** — Reason about a proposed strategy using accumulated memory.
- **Act** — Turn that context into a recommended next move.

## Core Features

### AI Call Brief

Generates a memory-grounded brief covering:

- What changed
- What matters now
- Customer priorities
- Risks
- Recommended move

### Memory Inspector

The Deal Workspace exposes three views:

- **Episodes** — Retained deal interactions
- **Facts** — Distilled facts from Hindsight recall
- **Playbooks** — Actionable guidance derived from Hindsight reflect output

Facts and Playbooks reuse the existing recall and reflect results instead of making unnecessary duplicate requests.

### What-If Strategy Simulator

The workspace evaluates three strategies:

1. **Offer 10% discount**
2. **Push for pilot first**
3. **Lead with ROI story**

Each result provides:

- Likely Reaction
- Risk
- Recommended Move
- Evidence

### Explainable Health Score

The Deal Workspace shows a deterministic Health Score with visible contributors and a **Why this score?** explanation.

### Evidence and Citations

Memory-grounded insights are connected to timeline evidence so users can inspect the source interaction behind an insight.

### Live Note Capture

New deal notes are added to the timeline and memory flow.

The interface confirms:

> **Memory retained. The next brief now uses this context.**

---

## Architecture

```text
Browser
   │
   ▼
Express / TypeScript
   │
   ├── Deal State
   │    ├── Timeline
   │    ├── Captured Notes
   │    └── Health Score
   │
   ├── Hindsight
   │    ├── Retain
   │    ├── Recall
   │    └── Reflect
   │
   ├── Groq
   │    └── Structured response generation
   │
   └── Deterministic Fallback
        └── Keeps the workflow usable when external services fail
