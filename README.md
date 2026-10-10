# Koate Kpai — AI Implementation Engineer & Cloud Platform Builder

I build **AI that runs on production infrastructure**. My background is production cloud
platforms — Terraform infrastructure-as-code, Kubernetes (GKE / EKS / AKS + Helm),
CI/CD (Cloud Build / GitHub Actions), and cost-aware FinOps with hard budget
enforcement — and I now apply that discipline to the AI layer: **RAG, retrieval
evaluation, agents, and ML pipelines** on Azure AI, AWS, and GCP.

I'm currently deep in the **Microsoft AI-103 path** (Azure AI Apps and Agents Developer),
shipping a hands-on retrieval project on **Azure AI Foundry** — the evaluation harness,
the metrics, and the lessons documented in a public engineering series.

My engineering philosophy:

> **Deterministic-first, AI-on-top.** The platform and core logic must be correct,
> reproducible, observable and cost-controlled — AI enriches it, it never undermines it.

---

## Featured — Enterprise RAG Pipeline (Azure AI Foundry)

**Repo: github.com/koatedevopskpai/enterprise-rag-pipeline**
**Series: gcp-architect-blog.web.app (foundry-rag-pipeline)**

An end-to-end RAG pipeline experiment, built the way I run everything — measurable and
cost-aware:

- **Four retrieval modes** — keyword (BM25), semantic (vectors), hybrid, and reranked
  hybrid — implemented against Azure AI Search-style candidate retrieval
- **Evaluation harness** in CI: ranking quality (**H@1, H@5, MRR, nDCG**) plus p50/p95
  latency, with results committed to version control so every change is traceable
- **Adversarial eval corpora**: *code*, *semantic* (paraphrase/trap), and *crowded*
  (near-duplicate) query sets — because easy benchmarks flatter systems
- Findings published end-to-end in blog posts: retrieval-mode gotchas, the four-mode
  benchmark, and why **reranking wins on semantic queries — and nothing rescues a
  crowded, ambiguous corpus**

---

## Featured — kdb+ Market Data Platform (q • C++ • Java • C#)

**tickerplant → RDB → partitioned HDB → C++ feed handler → Java REST service → C# subscriber**

A bank-style market-data platform built across the languages a trading stack is actually
written in; **github.com/koatedevopskpai/kdb-portfolio**.

- **q** — tickerplant (sequence numbers, disk log, fan-out), RDB, date-partitioned splayed
  HDB, end-of-day flush and historical queries
- **C++** — a feed handler that speaks the **kdb+ IPC wire protocol directly** (no KX
  library), validated byte-for-byte against q's `-8!`
- **Java** — a Spring Boot **REST service** over the HDB using the KX Java client
- **C#** — a .NET 8 **subscriber** to the tickerplant with live per-symbol aggregation

Rigour: ~800k msg/s C++ serialization • ~417k rows/s end-to-end ingestion • ~91 µs IPC
round-trip • byte-exact + end-to-end tests • benchmarks • ADRs.

---

## Featured — Platform proofs

- **GCP Platform Proof** — live GKE/Cloud Run/BigQuery platform (TypeScript gateway, Python
  RAG, .NET 8, pgvector), Cloud Build CI/CD with evaluation gates, Terraform FinOps label
  taxonomy, hard monthly budget. **github.com/koatedevopskpai/gcp-proof-platform**
- **AWS AI Platform Proof** — the cross-language MLOps/GenAI companion (EKS, Terraform/Helm,
  pgvector, CI eval gates, enforced budget). **github.com/koatedevopskpai/ai-platform-proof**

---

## Repo highlights

- **RAG / retrieval:** `enterprise-rag-pipeline`, `azure-ai-rag-pipeline`, `financial-research-rag`
- **Agents:** `agentic-ai-platform`, `gem-agentic-ai`, `gem-enterprise-rag-agent-with-ui`,
  `agentic-platform-aws`, `bedrock-agentic-demo`, `rag-pipeline-backend`
- **Vector search & evals:** `gem-langchain-rag`, `gem-vector-search`, `llm-evals-demo`
- **Data / MLOps:** `insightflow`, `gcp-data-pipeline`, `data-pipeline-engine`, `pipeline-dashboard`
- **Platform / DevOps:** `pulsenotify-platform`, `gcp-microservices-cloud-portfolioP1`, `gcp-data-engineer-course`
- **Security labs:** `azure-security-lab`, `aws-security-lab`, `gcp-security-lab`
- **Quant:** `quant-research-ig`

---

## Blog

**gcp-architect-blog.web.app** — multi-cloud (AWS • GCP • Azure) engineering + AI blog.
Active series: *foundry-rag-pipeline* on running RAG in Azure AI Foundry; plus GCP/AWS/Azure
landing-zone and platform-engineering deep dives.

---

## Core Skills

- **AI / ML:** Azure AI Foundry (AI-103) • RAG & hybrid retrieval • reranking •
  evaluation (H@k, MRR, nDCG) • agents (LangGraph, Azure AI Agents, Bedrock) •
  embeddings & vector search • guardrails
- **kdb+/q & market data:** tick architecture (tickerplant / RDB / HDB) • kdb+ IPC •
  partitioned time-series • qSQL • C++/Java/C# clients and services
- **GCP:** GKE • Cloud Run • BigQuery • Cloud Build • Compute Engine • Artifact Registry
- **AWS:** EKS • ECR • RDS (pgvector) • VPC • Budgets • IAM
- **Azure:** AI Foundry • AI Search • OpenAI • Functions • Sentinel
- **Cross-platform:** Terraform IaC • Kubernetes + Helm • CI/CD (GitHub Actions, Cloud Build)
- **FinOps:** cost-allocation tagging, hard budgets, auto-stop guardrails, cost forecasting
- **Languages:** Python • TypeScript • .NET 8 (C#) • C++ • Java • q (kdb+) • SQL

---

## Certifications

**Technical — AI & Cloud:**
- **Azure AI Apps and Agents Developer (AI-103)** — *in progress*
- **Claude Certified Developer — Foundations (CCDV-F)** — *in progress*
- **AWS Certified Solutions Architect – Professional** — *in progress*
- **Google Cloud Professional Cloud Architect**
- **Azure Fundamentals (AZ-900)**

**Delivery & consulting:** PMP • PRINCE2 • Lean Six Sigma Green Belt • Certified Scrum Master

---

## Connect

**LinkedIn:** https://www.linkedin.com/in/koate-kpai-772a22432/
**Email:** koatekpai@outlook.com
**Blog:** https://gcp-architect-blog.web.app