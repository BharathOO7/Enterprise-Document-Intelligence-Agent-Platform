```markdown
# ⚡ Avanzimer Document Intelligence Platform

**Enterprise-Grade LangGraph Orchestration for Document AI**

![Python 3.12+](https://img.shields.io/badge/Python-3.12%2B-blue?style=flat-square)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-pgvector-336791?style=flat-square&logo=postgresql)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=flat-square&logo=docker)

The **Avanzimer Document Intelligence Platform** provides a production-ready runtime for building, deploying, and scaling document-centric AI agents. Built on top of LangGraph, this backend infrastructure bridges the gap between raw unstructured data and auditable, human-in-the-loop (HITL) business workflows.

```

---

## 🏗️ Platform Capabilities

Unlike simple single-document chatbots, the Avanzimer platform is engineered for complex, multi-step enterprise reasoning:

* **Advanced Retrieval (RAG):** Canonical knowledge indexing with persistent evidence packs and provenance mapping.
* **Agentic Authoring:** Multi-step copilot drafting flows that synthesize retrieved data into structured artifacts.
* **Human-In-The-Loop (HITL):** Built-in release gates and iterative review loops for compliance and quality assurance.
* **MCP Integration:** Strict, typed contracts across API and Model Context Protocol (MCP) boundaries.
* **Auditable Lifecycle:** Complete telemetry of task history, state mutations, and observability summaries.

---

## 📐 Architecture Topology

The system operates across a secure, asynchronous execution plane backed by scalable vector storage.

```text
[ Client Applications / UI ] 
          │
          ▼
[ FastAPI + MCP Service Gateways ] 
          │
          ▼
[ Avanzimer Framework Layer (LangGraph Workflows) ]
          │
          ▼
[ Application Services (Retrieval, Indexing, Authoring, HITL) ]
          │
          ▼
[ Infrastructure: PostgreSQL + pgvector + Redis/Celery ]

```

---

## 🚀 Local Development Setup

Set up your isolated execution environment to run workflows entirely in-process without spinning up the full container stack.

### 1. Environment Initialization

```bash
# Clone and navigate to the directory
git clone [https://github.com/BharathOO7/Enterprise-Document-Intelligence-Agent-Platform.git](https://github.com/BharathOO7/Enterprise-Document-Intelligence-Agent-Platform.git)
cd Enterprise-Document-Intelligence-Agent-Platform

# Create and activate the virtual environment
python -m venv .venv
.\.venv\Scripts\Activate.ps1

# Install the core framework dependencies
pip install -e ./backend/packages

```

### 2. Run the Execution Plane (Dry-Run)

Verify your local framework routing without external dependencies:

```bash
python agent_examples/run_example.py --pattern retrieval_first --dry-run

```

---

## 🐳 Production Infrastructure Deployment

To run the complete data persistence and API layers, boot up the native Docker stack. This initializes the PostgreSQL database, applies vector extensions, and launches the FastAPI service.

```bash
# 1. Spin up the PostgreSQL + pgvector container
bash backend/scripts/postgres_up.sh

# 2. Apply database schemas and LangGraph state tables
bash backend/scripts/postgres_migrate.sh

# 3. Launch the REST API backend
bash backend/scripts/smoke_retrieval_api.sh --port 8010

```

*API Documentation & Swagger UI will be available at `http://localhost:8010/docs`.*

---

## 🧠 Workflow Pattern Library

The platform includes several pre-configured agent patterns located in `agent_examples/`.

| Pattern | Execution Command | Description |
| --- | --- | --- |
| **Retrieval First** | `python agent_examples/run_example.py --pattern retrieval_first` | Standard RAG pipeline with confidence scoring and evidence blocking. |
| **Authoring First** | `python agent_examples/run_example.py --pattern authoring_first` | Generative pipeline for synthesizing drafts from indexed context. |
| **HITL Gate** | `python agent_examples/run_example.py --pattern hitl_gate` | Pauses execution for human approval or revision injection. |
| **Async Batch** | `python agent_examples/run_example.py --pattern async_batch` | Processes high-volume background document jobs. |

---

## 🛡️ Governance & Security

All interactions within the Avanzimer platform maintain strict data provenance. Outputs from the authoring workflows are continuously linked back to the `doc_id` and `block_id` in the vector store, ensuring zero-hallucination compliance for enterprise environments.

© 2026 Avanzimer. All Rights Reserved.

```

```
