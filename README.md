# Koate Kpai — Platform & DevOps Engineer (AWS · Azure · GCP) · kdb+/q & Market Data

I design, build and operate **production cloud platforms**: Terraform infrastructure-as-code,
Kubernetes (GKE / EKS / AKS + Helm), CI/CD (Cloud Build / GitHub Actions), and cost-aware **FinOps**
with hard budget enforcement. I build these platforms for AI/ML workloads — RAG, agentic systems,
evaluation pipelines — and I make sure they are reliable, observable, and stay within budget.

More recently I've been specialising in **kdb+/q** and **low-latency market-data engineering** —
the data layer investment banks and hedge funds run on — bringing the same platform discipline
(testing, observability, cost-awareness) to capital-markets data systems.

My engineering philosophy:

> **Deterministic-first, AI-on-top.** The platform and core logic must be correct, reproducible,
> observable and cost-controlled — AI enriches it, it never undermines it.

---

## Featured — kdb+ Data Platform (q · C++ · Java · C#)
**tickerplant · RDB · partitioned HDB · C++ feed handler · Java REST service · C# subscriber**

A bank-style market-data platform built across the languages a trading stack is actually
written in:

- **q** — tickerplant (sequence numbers, disk log, fan-out), RDB, date-partitioned splayed
  HDB, end-of-day flush and historical queries
- **C++** — a feed handler that speaks the **kdb+ IPC wire protocol directly** (no KX
  library), validated byte-for-byte against q's `-8!`
- **Java** — a Spring Boot **REST service** over the HDB using the KX Java client
  (connection pooling, input validation)
- **C#** — a .NET 8 **subscriber** to the tickerplant with live per-symbol aggregation and
  automatic reconnect

Rigour: **~800k msg/s** C++ serialization · **~417k rows/s** end-to-end ingestion ·
**~91 µs** IPC round-trip · byte-exact + end-to-end **tests** · **benchmarks** · architecture
diagrams and **ADRs**.

Repo: **github.com/koatedevopskpai/kdb-portfolio**

---

## Featured — GCP Platform Proof (GCP DevOps / Platform Engineer)
**GKE · Cloud Run · BigQuery · Cloud Build · Terraform · Helm · FinOps**

A production-grade, **live** GCP platform demonstrating the full platform-engineering stack:
- **Compute Engine** VM running a multi-service stack (TypeScript gateway, Python RAG, .NET 8, pgvector) — verified live end-to-end
- **Cloud Run** job + **Cloud Scheduler**: scheduled MLOps evaluation pipeline
- **BigQuery**: `eval_reports` analytics table loaded by the pipeline
- **Cloud Build** CI/CD: build → push to Artifact Registry → **evaluation gate** → unit tests (Python/Node/.NET)
- **GKE + Helm** (optional, on-demand) for Kubernetes demo workloads
- **Terraform** IaC with a **FinOps label taxonomy** on every resource
- **Hard monthly budget** with 80%/100% alerts — the entire always-on stack fits under it

Repo: **github.com/koatedevopskpai/gcp-proof-platform**

---

## Featured — AI Platform Proof (AWS MLOps/GenAI)
**Python · .NET 8 · TypeScript · pgvector · Terraform/Helm · CI eval gates**

The AWS companion: a production-grade MLOps/GenAI platform — cross-language RAG stack
(TypeScript gateway, Python RAG service, .NET 8 ingestion, pgvector), CI **evaluation gates**
that fail builds on quality regression, Terraform/Helm for EKS, and FinOps tagging with an
enforced monthly budget. Same deterministic-first discipline, same cost-consciousness.

Repo: **github.com/koatedevopskpai/ai-platform-proof**

---

## Other highlights
- **Cloud IaC (Terraform):** GCP / AWS / Azure landing zones, container platforms (GKE / EKS / AKS), and premium-workload architectures
- **azure-ai-soc-triage:** AI-assisted SOC automation (Sentinel, Logic Apps, Functions) — **cost-optimized to <$20/month**
- **Agent / AI:** agentic RAG platform with HITL approval, guardrails, RAGAS evals, and deterministic fallbacks

---

## Core Skills
- **kdb+/q & market data:** tick architecture (tickerplant / RDB / HDB) · kdb+ IPC · partitioned time-series · qSQL · C++/Java/C# clients and services
- **GCP:** GKE · Cloud Run · BigQuery · Cloud Build · Compute Engine · Artifact Registry · Cloud Scheduler
- **AWS:** EKS · ECR · RDS (pgvector) · VPC · Budgets · IAM
- **Cross-platform:** Terraform IaC · Kubernetes + Helm · CI/CD (Cloud Build, GitHub Actions)
- **FinOps:** cost-allocation tagging, hard budgets, auto-stop guardrails, cost forecasting
- **Languages:** C++ · Java · q (kdb+) · Python · TypeScript · .NET 8 (C#) · SQL
- **AI/ML:** RAG (pgvector) · agentic workflows · evaluation frameworks (RAGAS, LLM-as-judge) · guardrails
- **Delivery:** Agile/Scrum · stakeholder & risk management · consulting

---

## Certifications
PMP · PRINCE2 · Lean Six Sigma Green Belt · Certified Scrum Master · Azure Fundamentals (AZ-900) ·
Claude Certified Developer – Foundations (CCDV-F) — *in progress* · Azure AI Apps and Agents Developer (AI-103) — *in progress*

---

## Connect
**LinkedIn:** https://www.linkedin.com/in/koate-kpai-772a22432/
**Email:** koatekpai@outlook.com
