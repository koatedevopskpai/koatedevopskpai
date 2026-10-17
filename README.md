# Koate Kpai — Platform & AI Engineer (AWS · Azure · GCP)

I design, build and operate **cloud platforms**: Terraform infrastructure-as-code,
Kubernetes (GKE / EKS / AKS + Helm), CI/CD (Cloud Build / GitHub Actions), and
cost-aware **FinOps**. I build these for AI/ML workloads — RAG, agentic systems,
evaluation pipelines — and I care that they are reliable, observable and stay
within budget.

My engineering philosophy:

> **Deterministic-first, AI-on-top.** The platform and core logic must be correct, reproducible,
> observable and cost-controlled — AI enriches it, it never undermines it.

**Two kinds of experience, kept separate.** Eight years of commercial enterprise
data and platform engineering in regulated rail and utilities. Alongside that,
self-funded **public reference builds** that demonstrate implementation and
testing. The reference builds are not commercial delivery, and I do not describe
them as such.

---

## Reference builds — evidence first

Each of these has a documented strongest result and a documented limit. If a
number appears below, there is a command behind it.

### Retrieval and evaluation — `enterprise-rag-pipeline`
Azure AI Search hybrid retrieval: parent-child chunking, four interchangeable
strategies (BM25, vector, hybrid, LLM-rerank), reciprocal rank fusion, and a
citation-prompted answer path.

- Four strategies compared on the same 20-query set with the results **committed**
  to the repository (`eval/comparison.json`).
- A saved 16-question quality report: relevance 4.75, groundedness 5.00,
  coherence 4.06, fluency 3.06.
- A live run against Azure AI Search ingested 11 documents into 41 chunks, scored a
  three-question baseline 5/5, and **blocked a deliberately unsupported answer**
  without changing thresholds.
- Limits: the quality report is a saved run, not a fresh one; the semantic ranker
  is unconfirmed on the tier used. Start at
  **[EVIDENCE.md](https://github.com/koatedevopskpai/enterprise-rag-pipeline/blob/main/EVIDENCE.md)**.

### Agentic systems — `gem-agentic-ai`
A tool-calling agent in two implementations (a manual ReAct loop and a LangGraph
graph), with bounded execution and durable memory.

- Tool schema validation, allowlists, deadlines, call/token limits, idempotency and
  an explicit approval state.
- Durable, user-scoped conversation memory over SQLite that survives a restart.
- 148 tests, 94% coverage, CI green with **no credentials** in the job.
- Limits: a timed-out tool is not killed (Python cannot interrupt a thread); memory
  is one unencrypted SQLite file on one host; tools without a stable action key are
  at-least-once; the execution guard is **not** a sandbox.

### Evaluation design — `llm-evals-demo`
A harness for scoring **generated** answers, not reference answers.

- Found and removed a measurement bug where the harness scored the reference answer,
  guaranteeing a pass. A wrong answer now fails against a real judge.
- A calibrated, fail-closed gate with a per-case floor that cannot be diluted by a
  mean.
- A quality, latency and cost comparison across model configurations.
- Limits: live samples are small and thresholds are provisional.

### Deterministic engineering — `multi-agent-optimizer`
A unit-tested critical-path engine with an optional LangGraph layer and resilience
controls (retry, circuit breaker, schema-validated fallback).

- An evaluation gate expanded from 2 to 11 golden cases covering cycles,
  disconnected activities, invalid durations and multiple critical paths.
- 80% coverage floor enforced in CI.

### Graph retrieval — `agentic-rag-hybrid`
Neo4j-ready graph retrieval with BM25, deterministic signature vectors, reciprocal
rank fusion and entity-seeded expansion.

- **15/15 live parity probes** against a real Neo4j instance, after fixing a query
  that duplicated nodes.
- A supernode benchmark showing that a result `LIMIT` leaves database work
  unchanged (9210 hits) while a hop bound reduces it to 11 — measured, not asserted.
- Limits: "dense" means deterministic signature vectors, **not** learned embeddings.

### Measured trade-offs — `lexisum`
Contract clause extraction and summarisation.

- TF-IDF MAP 0.727 at 0.005 s versus Sentence-BERT 0.735 at 1.501 s — ~0.008 MAP
  for roughly 300× the latency.
- A source-text auditor whose exact matching semantics are documented.
- Limits: published, not independently reproduced; the judge comparison sampled 15
  outputs per model.

### Platform and cloud
- **`gcp-proof-platform`** — cross-language reference platform: TypeScript gateway,
  Python RAG, .NET 8, pgvector, with Terraform, Helm and Cloud Build configuration.
  *Status: services and configuration are implemented; Cloud Build run receipts have
  not been independently inspected, so this is not claimed as a verified live
  platform.*
- **`ai-platform-proof`** — AWS deployment path. A low-cost EC2/Docker Compose
  release with a gateway health check is the **supported** path. *Status: EKS is
  design-only and never deployed; the budget action stops the database instance, not
  every resource.*
- **Cloud IaC (Terraform)** — GCP / AWS / Azure landing zones, container platforms
  (GKE / EKS / AKS) and premium-workload architectures. *Status: infrastructure
  examples, not operated clusters on three clouds.*
- **`azure-ai-soc-triage`** — AI-assisted SOC automation (Sentinel, Logic Apps,
  Functions). *Status: cost target, not a verified monthly figure.*

---

## How I work

I develop these with multiple coding agents, and I document the process because the
interesting part is not that it works — it is the discipline that stops an agent's
confident "done" from becoming an unsupported claim:
**[AGENT_WORKFLOW.md](AGENT_WORKFLOW.md)**.

---

## Core skills
- **GCP:** GKE · Cloud Run · BigQuery · Cloud Build · Compute Engine · Artifact Registry · Cloud Scheduler
- **AWS:** EKS · ECR · RDS (pgvector) · VPC · Budgets · IAM
- **Cross-platform:** Terraform IaC · Kubernetes + Helm · CI/CD (Cloud Build, GitHub Actions)
- **FinOps:** cost-allocation tagging, budget alerts, auto-stop guardrails, cost analysis
- **Languages:** Python · TypeScript · .NET 8 (C#) · SQL
- **AI/ML:** RAG (Azure AI Search, pgvector) · agentic workflows (LangGraph) · evaluation design (RAGAS, LLM-as-judge, calibrated gates) · bounded tool execution
- **Delivery:** requirements analysis · stakeholder & risk management · consulting

---

## Certifications
PMP · PRINCE2 · Lean Six Sigma Green Belt · Certified Scrum Master · Azure Fundamentals (AZ-900) ·
Claude Certified Developer – Foundations (CCDV-F) — *in progress* · Azure AI Apps and Agents Developer (AI-103) — *in progress*

---

## Connect
**LinkedIn:** https://www.linkedin.com/in/koate-kpai-772a22432/
**Email:** koatekpai@outlook.com