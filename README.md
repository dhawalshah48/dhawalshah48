# Hi, I'm Dhawal Shah 👋

**AI / ML Engineer · MLOps & LLMOps · 5+ years shipping production ML and agentic systems**

M.S. in Computer Science (AI specialization), Iowa State University — GPA 3.9/4.0 (Aug 2024 – Aug 2026)
Thesis: *Low-Rank KV Cache Compression in LLMs: A Second-Order Output Metric and Its Limits*
Open to AI Engineer / ML Engineer / MLOps / LLMOps roles, anywhere in the USA.

📄 [Resume](https://github.com/dhawalshah48/dhawalshah48/blob/main/Dhawal_Shah_ML_Resume_generic.pdf) · 💼 [LinkedIn](https://www.linkedin.com/in/dhawalshah04/) · ✉️ dhawal04@iastate.edu · ✉️ dhawalshah48@gmail.com · 📱 +1 (515) 686-0507

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
- Generated 3M simulated transactions to assess the profitability of the business logic, which showed the swap logic needed overflow and underflow guardrails

### Avalara Technologies — Senior Software Engineer, Machine Learning *(Jul 2023 – Aug 2024)*
- Built and deployed production document-AI models (Random Forest, Donut, LayoutXLM, LiLT, spaCy) for document classification and entity extraction
- Replaced a third-party API with in-house models, cutting inference cost ~90% (benchmarked against AWS Comprehend on a 500-document evaluation set)
- Identified and upgraded vulnerable/outdated Python dependencies to improve security posture
- Led onboarding for 8 new engineers — 50+ hours of mentoring, code review, and knowledge-sharing

### Avalara Technologies — Software Engineer, Machine Learning *(Jul 2020 – Jun 2023)*
- Automated 30% of 100,000+ manual document-processing decisions across 4 teams, cutting per-document processing time from 10 minutes to 1 minute
- Built a model abstraction layer that trained multiple candidate models per task and auto-served the best one, so downstream consumers never needed to know which model served a request
- Built an asynchronous model-training job service with FastAPI and Redis: generated job IDs for long-running training runs, ran them in the background, and updated/polled job status in the database
- Built the UI for an Intelligent Document Processing platform in OutSystems, with AWS Textract for document extraction
- Built the team's initial Streamlit demo app
- Deployed and operated services on AWS (SageMaker, EKS, EC2); used ClearML for experiment tracking and model versioning, Label Studio for human-in-the-loop annotation
- Built a Scala/Akka Streams + PySpark/Hadoop pipeline for large-scale structured/unstructured data ingestion
- Added OAuth/SSO authentication to an internal dashboard used across other teams

---

## Featured Projects

### 🎓 [M.S. Thesis — Low-Rank KV Cache Compression in LLMs](https://github.com/dhawalshah48/kv-cache-fisher-thesis)
Derived a closed-form output-Fisher metric for attention-aware low-rank KV cache compression — showing where existing training-free methods top out and *why*. Validated against logit- and variance-based baselines on WikiText-2 perplexity and LongBench across Llama-2-7B/13B and Mistral-7B (GQA). Found a ~5,000× spread in per-layer importance and designed a water-filling rank-allocation rule that extends the usable compression frontier ~16×. Also measured and disclosed the method's own failure modes and hard ceiling (third-order softmax curvature). Code, figures, and raw logs are public. Compute: NCSA Delta via an NSF ACCESS allocation.

### 📊 [VarRate: Variable-Rate KV Cache Compression](https://arxiv.org/abs/2607.15498)
*Co-author, arXiv preprint; advised by Dr. Ali Jannesari, with Shahrzad Esmat.*
Designed and ran 14 ablation studies with credible baselines and paired bootstrap significance testing (Holm-Bonferroni correction) for a training-free LLM compression method — catching and correcting 2 unverified claims before peer review. Built negative-control experiments to separate a claimed model capability from measurement artifact, backed by controlled A100 latency benchmarking. Root-caused a silent cross-environment reproducibility failure and authored an audit-trail protocol so results reproduce exactly across runs.

### 🧠 Agentic Pruner
Five-agent **LangGraph** framework (Sensitivity, Hardware-Aware Validation, NM Assigner, Cross-Revision Memory, Adaptive Fine-Tuning Strategy agents) automating hardware-aware N:M structured sparsity pruning for Vision Transformers — replacing a single fixed pattern with per-block, hardware- and importance-aware selection. Cleanly separated deterministic algorithms (Wanda-style scoring, greedy assignment) from the two steps where LLM judgment actually helps. On DeiT-Tiny/CIFAR-10, iterative refinement lifted accuracy from 93.8% to 95.5% across revisions at a matched MAC budget; ran controlled ablations (SLURM array jobs, 3 seeds/condition) across 40+ logged runs on an A100 cluster.

### 🏦 SEC Financial Intelligence Agent *(ongoing)*
Agentic research assistant over SEC 10-K filings and live news, with an LLM query classifier and cited answers. RAG pipeline on `bge-base` embeddings and a Qdrant vector database, fed by Redis Streams ingestion with consumer-group backpressure, crash reclaim, and idempotent writes. Evaluated with RAGAS Faithfulness and Context Precision against an internal golden question set.

### ⚙️ Compression-Aware LLM Serving Platform *(in progress)*
Serving Llama 3.1 8B with vLLM on a GCP spot NVIDIA L4 GPU, benchmarking the fp16 baseline against compression variants (quantization, structured pruning, and the training-free low-rank KV cache method from my thesis — in progress). Built an open-loop async load-testing harness (`asyncio`/`httpx`, SSE streaming) measuring TTFT, TPOT, inter-token latency, p50/p95/p99 end-to-end latency, throughput, and SLO-based goodput, with 11 pytest tests guarding against latency/goodput accounting bugs. Baseline sweep: single-user decode at 61 ms/token (~88% of the L4's 300 GB/s memory bandwidth), and every request met a 1s-TTFT/100ms-TPOT SLO at 0.96 req/s against a raw throughput ceiling of ~2.3 req/s — showing per-token latency, not time-to-first-token, is the binding constraint. Survived two spot-VM preemptions via a documented recovery runbook and pinned dependency versions.

### 🔧 jobsearch-mcp
Personal **MCP server** (Python, `mcp` SDK) exposing 16 tools to Claude for job-fit scoring, resume-tailoring briefs, and outreach drafting. Integrates 5 public ATS APIs (Greenhouse, Lever, Ashby, SmartRecruiters, Recruitee) with SQLite dedup — deliberately draft-only, it never sends email or submits applications on its own.

### 🧪 RLHF Alignment Method Comparison
*Course project, COMS 6730 — 5-person team; responsible for the GRPO implementation.*
Compared PPO, DPO, and GRPO fine-tuning against an SFT baseline on LLaMA-3.2-8B (LoRA, 2×A100 80GB) using the Anthropic HH-RLHF dataset. GRPO reached a 72.8% preference win rate at under 60% of PPO's compute cost (812s vs. 1407s per epoch, 74.2% win rate); DPO was the most compute-efficient at 69.6% win rate in 373s/epoch.

### 🔬 Microscopy Cell Counting
*Course project, COMS 5710X (Responsible AI).*
Implemented data augmentation and a custom ground-truth coordinate-transform script to mitigate class imbalance from limited labeled data, upsampling underrepresented medium/high cell-count images. Contributed to model robustness and uncertainty-quantification analysis (conformalized quantile regression).

### 🖼️ Image/Video Captioning
Compared CNN–LSTM (InceptionV3 encoder) and ViT–GPT2 on Flickr8k; ViT–GPT2 improved BLEU-4 by 486% and BLEU-1 by 30% over the CNN–LSTM baseline.

### 🎈 [PopperGame](https://github.com/dhawalshah48/PopperGame)
Interactive OpenCV game: tracks a real ball in-hand via webcam, detects a throw motion, and triggers an on-screen balloon-pop effect.

---

## Publications

**[Low-Rank KV Cache Compression in LLMs: A Second-Order Output Metric and Its Limits](https://www.proquest.com/dissertations-theses/low-rank-kv-cache-compression-llms-second-order/docview/3380554573/se-2?accountid=10906)**
Dhawal Shah — M.S. Thesis, Iowa State University — Aug 2026 · [code](https://github.com/dhawalshah48/kv-cache-fisher-thesis)

**[VarRate: Training-Free Variable-Rate KV Cache Compression for Long-Context LLMs](https://arxiv.org/abs/2607.15498)**
Esmat, S.; Shah, D.; Jannesari, A. — arXiv preprint, not peer-reviewed — Jul 2026

**[An Analysis on Use of Big Data in Cloud Computing Environment](https://zenodo.org/records/1288453)**
Shah, D.; Kumbhkar, M. — Zenodo — Jun 2018

---

## Technical Skills

**Agentic AI / LLM:** LangGraph, LangChain, Model Context Protocol (MCP), agent orchestration, tool/function calling, typed state management, model routing, RAG, prompt engineering, human-in-the-loop workflows, OpenAI / Anthropic / Ollama / Qwen APIs, vLLM / LLM inference serving

**ML & Research:** PyTorch, Hugging Face (Datasets, TRL), RLHF (PPO/DPO/GRPO), model fine-tuning & evaluation, ablation design, statistical significance testing (bootstrap, Holm-Bonferroni), reproducibility engineering

**Backend & Data:** Python, FastAPI, PostgreSQL, SQLite, Redis, Pydantic, Alembic, SQL, pandas, NumPy, JWT/OAuth/SSO, RBAC

**Cloud & DevOps:** AWS (EC2, EKS, SageMaker, S3, Comprehend, Textract), Docker, Kubernetes, Terraform, GitHub Actions, CI/CD, pytest, Playwright, OpenTelemetry, GCP (Compute Engine, spot VMs)

**Limited/academic exposure:** Scala, Akka Streams, PySpark, Hadoop, Node.js/Express/MongoDB (2019 capstone), Java (coursework)

---

📫 Reach me at **dhawalshah48@gmail.com** or **dhawal04@iastate.edu**, by phone at **+1 (515) 686-0507**, or on [LinkedIn](https://www.linkedin.com/in/dhawalshah04/).
