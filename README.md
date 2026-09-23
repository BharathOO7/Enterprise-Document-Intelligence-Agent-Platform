# AegisDoc AI

### Enterprise Document Intelligence, Workflow Automation & Agent Orchestration

> Turn unstructured documents and business tasks into traceable, reviewable, production-ready AI workflows.

AegisDoc AI is a production-oriented platform for building **document-centric AI agents** with LangGraph.

Instead of treating document intelligence as a simple “ask questions about a PDF” problem, the platform models the full lifecycle:

**Ingest → Index → Retrieve → Author → Review → Release**

The system is designed around explicit contracts, persistent state, evidence tracking, human review, asynchronous execution, and integration boundaries suitable for real applications.

---

## Why AegisDoc AI?

Most document AI prototypes stop at:

```text
PDF → Embeddings → LLM → Answer
```

AegisDoc AI treats the problem differently:

```text
                        ┌──────────────────────┐
                        │      Client Apps     │
                        └──────────┬───────────┘
                                   │
                          API / MCP Contracts
                                   │
                                   ▼
                    ┌────────────────────────────┐
                    │     LangGraph Runtime      │
                    │                            │
                    │ Retrieval                  │
                    │ Authoring                  │
                    │ Review / HITL              │
                    │ Workflow State             │
                    └────────────┬───────────────┘
                                 │
                                 ▼
                    ┌────────────────────────────┐
                    │     Application Layer      │
                    │                            │
                    │ Indexing                   │
                    │ Evidence                   │
                    │ Artifacts                  │
                    │ Task Lifecycle             │
                    └────────────┬───────────────┘
                                 │
                                 ▼
                    ┌────────────────────────────┐
                    │ Persistence & Adapters     │
                    │                            │
                    │ PostgreSQL                 │
                    │ pgvector                   │
                    │ External Model Gateways    │
                    └────────────────────────────┘
```

The result is an AI system that is designed to be **observable, auditable, extensible, and reviewable** rather than a single prompt wrapped in an API.

---

# Core Capabilities

## 01 — Retrieval Intelligence

Build retrieval-first workflows that transform indexed organizational knowledge into structured evidence.

The platform supports:

* canonical knowledge indexing
* retrieval workflows
* evidence packs
* source-aware results
* unresolved knowledge gaps

Example workflow:

```text
Documents
   ↓
Indexing
   ↓
Retrieval
   ↓
Evidence Pack
   ↓
Agent Context
```

---

## 02 — Agentic Authoring

AegisDoc AI supports multi-step authoring workflows rather than one-shot generation.

An authoring workflow can:

```text
Task
 ↓
Retrieve relevant knowledge
 ↓
Generate draft
 ↓
Evaluate / review
 ↓
Request changes
 ↓
Approve
 ↓
Produce artifact
```

This enables document agents that operate as **workflow systems**, not merely chat interfaces.

---

## 03 — Human-in-the-Loop Review

AI output can move through explicit human review stages.

The platform provides patterns for:

* review actions
* iterative approval
* task events
* HITL decision flows
* auditable review timelines

Example:

```text
AI Draft
   ↓
Human Review
   ├── Needs Changes ──→ Regenerate / Revise
   │
   └── Approve ────────→ Release
```

---

## 04 — Evidence & Provenance

Generated output should not exist in isolation.

AegisDoc AI models evidence and task state so that workflows can retain information about:

* source documents
* versions
* evidence blocks
* task lifecycle
* review actions
* artifacts
* observability events

This creates a foundation for **traceable AI workflows**.

---

## 05 — MCP Integration

The platform exposes documented MCP boundaries for document-oriented services.

Current patterns include integrations around:

* retrieval
* repositories
* artifacts
* templates
* review
* configuration

This allows AI workflows to interact with external tools through explicit service boundaries instead of embedding every capability directly into the agent.

---

# Architecture

AegisDoc AI separates the system into distinct layers.

```text
┌────────────────────────────────────────────────────┐
│                Clients / Integrators               │
└─────────────────────────┬──────────────────────────┘
                          │
                          ▼
┌────────────────────────────────────────────────────┐
│                API + MCP Boundaries                │
│                    FastAPI / MCP                   │
└─────────────────────────┬──────────────────────────┘
                          │
                          ▼
┌────────────────────────────────────────────────────┐
│              LangGraph Workflow Layer              │
│                                                    │
│ Retrieval • Authoring • HITL • State Machines     │
└─────────────────────────┬──────────────────────────┘
                          │
                          ▼
┌────────────────────────────────────────────────────┐
│                 Application Services               │
│                                                    │
│ Indexing • Retrieval • Evidence • Artifacts       │
└─────────────────────────┬──────────────────────────┘
                          │
                          ▼
┌────────────────────────────────────────────────────┐
│              Persistence + Adapters                │
│                                                    │
│ PostgreSQL • pgvector • Model Gateways             │
└────────────────────────────────────────────────────┘
```

The documented production runtime also includes an asynchronous execution plane based on **Celery and Redis**, alongside PostgreSQL and pgvector persistence.

---

# Workflow Patterns

AegisDoc AI currently demonstrates several reusable workflow patterns.

### Retrieval First

```text
Query
 ↓
Knowledge Retrieval
 ↓
Evidence Pack
 ↓
Grounded Response
```

### Authoring First

```text
Task
 ↓
Retrieve Context
 ↓
Generate Draft
 ↓
Review
 ↓
Finalize Artifact
```

### HITL Gate

```text
Agent Output
```

