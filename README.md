# Hi, I'm Dhawal Shah 👋

**AI / ML Engineer · MLOps & LLMOps · 5+ years shipping production ML and agentic systems**

M.S. in Computer Science (AI specialization), Iowa State University — GPA 3.9/4.0 (Aug 2024 – Aug 2026)
Thesis: *Low-Rank KV Cache Compression in LLMs: A Second-Order Output Metric and Its Limits*
Open to AI Engineer / ML Engineer / MLOps / LLMOps roles, anywhere in the USA.

📄 [Resume](https://github.com/dhawalshah48/dhawalshah48/blob/main/Dhawal_Shah_ML_Resume_generic.pdf) · 💼 [LinkedIn](https://www.linkedin.com/in/dhawalshah04/) · ✉️ dhawal04@iastate.edu · ✉️ dhawalshah48@gmail.com

## What I do

I build the layer between LLM agents and the deterministic systems they have to work with reliably — typed agent orchestration, model routing, tool-calling frameworks, and the MLOps/LLMOps infrastructure (CI/CD, observability, multi-tenant data isolation) that makes agentic systems safe to ship. Before that, I spent four years building and operating production ML systems (document classification, entity extraction, NLP) in a regulated enterprise environment.

---

## Experience

### Hermamind Inc. — Founding AI Engineer *(Jan 2026 – Aug 2026)*
Friend's startup; worked directly with the CEO/co-founder on an AI-assisted B2B RFQ-to-quote platform (Hermamind Pricing). Core architecture principle: deterministic pricing logic in Python, LLMs used only for narration/rationale — never for price math.

- Built an agent execution/orchestration layer on **LangGraph** with typed Pydantic state, deterministic transitions, tool invocation, and human-approval checkpoints
- Designed a typed tool-execution framework for registering, validating, and invoking SQL-backed tools across customer, product, and pricing systems, grounding model outputs in authoritative backend data
- Built a provider-agnostic model routing layer across **OpenAI, Anthropic, Ollama, and Qwen**, with per-step routing on latency/cost/quality — cut inference cost materially while holding task success flat in internal evals
- Architected multi-tenant persistence (**PostgreSQL, FastAPI, Alembic**) with central identity metadata separated from tenant-isolated application databases
- Instrumented the agent workflow with **OpenTelemetry** (traces/metrics/logs) for run-level visibility without logging prompts or pricing payloads
- Shipped a GitHub Actions CI/CD pipeline with a 200+ test pytest/Playwright suite as a PR merge gate
- Built async background job execution (FastAPI + Redis) for long-running model training/data jobs
- Shipped product features directly with the CEO, including a Slack webhook alerting system for CloudWatch-detected outages
- *(Has a standing offer to return in a remote engineering role after this engagement.)*

### Digitenium — AI Engineer Intern *(Jun 2025 – Aug 2025)*
- Built a Python simulation framework (pandas) modeling asset allocation/redemption flows for a decentralized liquidity protocol; projected ~20% improvement in asset velocity

### Avalara Technologies — Senior Software Engineer, Machine Learning *(Jul 2023 – Aug 2024)*
- Built and deployed production document-AI models (Random Forest, Donut, LayoutXLM, LiLT, spaCy) for document classification and entity extraction
- Replaced a third-party API with in-house models, cutting inference cost ~90% (benchmarked against AWS Comprehend on a 500-document evaluation set)
- Identified and upgraded vulnerable/outdated Python dependencies to improve security posture
- Led onboarding for 8 new engineers — 50+ hours of mentoring, code review, and knowledge-sharing

### Avalara Technologies — Software Engineer, Machine Learning *(Jul 2020 – Jun 2023)*
- Automated 30% of 100,000+ manual document-processing decisions across 4 teams, cutting per-document processing time from 10 minutes to 1 minute
- Built a model abstraction layer that trained multiple candidate models per task and auto-served the best one, so downstream consumers never needed to know which model served a request
- Deployed and operated services on AWS (SageMaker, EKS, EC2); used ClearML for experiment tracking and model versioning, Label Studio for human-in-the-loop annotation
- Built a Scala/Akka Streams + PySpark/Hadoop pipeline for large-scale structured/unstructured data ingestion
- Added OAuth/SSO authentication to an internal dashboard used across other teams

---

## Featured Projects

### 🎓 [M.S. Thesis — Low-Rank KV Cache Compression in LLMs](https://github.com/dhawalshah48/kv-cache-fisher-thesis)
Derived a closed-form output-Fisher metric for attention-aware low-rank KV cache compression — showing where existing training-free methods top out and *why*. Validated against logit- and variance-based baselines on WikiText-2 perplexity and LongBench across Llama-2-7B/13B and Mistral-7B (GQA). Found a ~5,000× spread in per-layer importance and designed a water-filling rank-allocation rule that extends the usable compression frontier ~16×. Also measured and disclosed the method's own failure modes and hard ceiling (third-order softmax curvature). Code, figures, and raw logs are public. Compute: NCSA Delta via an NSF ACCESS allocation.

### 🧠 Agentic Pruner
Five-agent **LangGraph** framework (Sensitivity, Hardware-Aware Validation, NM Assigner, Cross-Revision Memory, Adaptive Fine-Tuning Strategy agents) automating hardware-aware N:M structured sparsity pruning for Vision Transformers — replacing a single fixed pattern with per-block, hardware- and importance-aware selection. Cleanly separated deterministic algorithms (Wanda-style scoring, greedy assignment) from the two steps where LLM judgment actually helps. On DeiT-Tiny/CIFAR-10, iterative refinement lifted accuracy from 93.8% to 95.5% across revisions at a matched MAC budget; ran controlled ablations (SLURM array jobs, 3 seeds/condition) across 40+ logged runs on an A100 cluster.

### 🔧 jobsearch-mcp
Personal **MCP server** (Python, `mcp` SDK) exposing 16 tools to Claude for job-fit scoring, resume-tailoring briefs, and outreach drafting. Integrates 5 public ATS APIs (Greenhouse, Lever, Ashby, SmartRecruiters, Recruitee) with SQLite dedup — deliberately draft-only, it never sends email or submits applications on its own.

### 🖼️ Image/Video Captioning
Compared CNN–LSTM (InceptionV3 encoder) and ViT–GPT2 on Flickr8k; ViT–GPT2 improved BLEU-4 by 486% and BLEU-1 by 30% over the CNN–LSTM baseline.

### 🎈 [PopperGame](https://github.com/dhawalshah48/PopperGame)
Interactive OpenCV game: tracks a real ball in-hand via webcam, detects a throw motion, and triggers an on-screen balloon-pop effect.

---

## Technical Skills

**Agentic AI / LLM:** LangGraph, LangChain, Model Context Protocol (MCP), agent orchestration, tool/function calling, typed state management, model routing, RAG, prompt engineering, human-in-the-loop workflows, OpenAI / Anthropic / Ollama / Qwen APIs

**ML & Research:** PyTorch, Hugging Face (Datasets, TRL), RLHF (PPO/DPO/GRPO), model fine-tuning & evaluation, ablation design, statistical significance testing (bootstrap, Holm-Bonferroni), reproducibility engineering

**Backend & Data:** Python, FastAPI, PostgreSQL, SQLite, Redis, Pydantic, Alembic, SQL, pandas, NumPy, JWT/OAuth/SSO, RBAC

**Cloud & DevOps:** AWS (EC2, EKS, SageMaker, S3, Comprehend), Docker, Kubernetes, Terraform, GitHub Actions, CI/CD, pytest, Playwright, OpenTelemetry

**Limited/academic exposure:** Scala, Akka Streams, PySpark, Hadoop, Node.js/Express/MongoDB (2019 capstone), Java (coursework)

---

📫 Reach me at **dhawalshah48@gmail.com** or **dhawal04@iastate.edu** or on [LinkedIn](https://www.linkedin.com/in/dhawalshah04/).
