# Dhawal Shah

Graduate AI/ML engineer with **5+ years** of experience building and deploying **scalable ML systems**—especially for **document processing automation**, **NLP**, and **computer vision** on **AWS**.  
**Open to work anywhere in the USA.**

- M.S. in Computer Science (AI), **Iowa State University** (GPA: **3.9/4.0**, Aug 2024 – May 2026)
- Production ML + MLOps: training, evaluation, deployment, monitoring, cost/security optimization
- Cloud + infra: **AWS (S3, SageMaker, Comprehend, Textract, EKS, EC2, EMR)**, **Docker**, **Kubernetes**, **ClearML**

## Connect
- GitHub: https://github.com/dhawalshah48  
- LinkedIn: https://www.linkedin.com/in/dhawalshah04/  
- Email: dhawal04@iastate.edu

## Work Experience

### Hermamind Inc. — Software Engineer (AI/ML & Full-Stack) *(Jan 2026 – Aug 2026)*
Sole/primary engineer on the **Hermamind Pricing MVP** — a multi-tenant, AI-assisted B2B RFQ-to-quote platform for industrial/commodity sales (oilfield tubulars, inventory-backed pricing). Owned the product end-to-end: AI agent design, deterministic pricing engine, backend, frontend, data pipelines, and cloud infra. Core architecture principle: **deterministic pricing formulas in Python; LLMs used only for narration, conversation, and rationale — never for price math.**
- **AI / Agents:** Designed a **LangGraph** RFQ workflow (`customer_lookup → product_lookup → anchor pricing → quote generation`) with typed Pydantic state; built a multi-provider conversational agent (**OpenAI, Anthropic, Ollama, Qwen/DashScope**) with step-level model routing for cost/latency and human-in-the-loop approval checkpoints
- **AI / Explainability:** Built a user-preference learner that persists quote-adjustment patterns, and an insights layer generating auditable pricing rationale from structured signals (ATP, margins, history, customer relationship) rather than LLM-invented prices; added bilingual (EN/ZH) tool-explanation UX
- **Pricing domain logic:** Implemented multi-anchor pricing (historical market anchors + cost/WAC-based), policy-driven margin governance (target/floor/ceiling by customer tier), and an ATP (available-to-promise) calculator over inventory lots, reservations, and shortfalls
- **Backend:** Built a **FastAPI** surface (~20+ route modules: auth, RFQ, quotes, inventory/lots, inbound shipments, customers, vendors/POs, dashboard, audit trail) on **PostgreSQL** with **SQLAlchemy**/**Alembic**, JWT auth, and a repository + service layer with Pydantic contracts
- **Multi-tenancy:** Designed central-auth + per-tenant Postgres database isolation via a tenant registry/connection resolver, so customer data never crosses tenants
- **Data engineering:** Built an Excel/CSV → staging → PostgreSQL ETL pipeline (readers, transformers, validators, orchestrators) supporting FRESH (full replace) and UPSERT (incremental) modes, with SKU normalization and mapping configs
- **Frontend:** Built the **Next.js 14** (React, Tailwind) UI — auth, quote workspace/detail, operations and stock dashboards (Recharts), inbound-shipment tracking, and an admin data browser with inline editing
- **DevOps:** Provisioned AWS infra with **Terraform** (VPC, ALB, EC2, RDS, S3), containerized local/staging/prod environments with **Docker Compose**, added **GitHub Actions** CI against a live Postgres service container, and built encrypted S3 backups (boto3) with Celery/APScheduler task scheduling
- **Quality:** Authored a broad automated test suite (unit, integration, pipeline e2e, migration validation) with pytest and Jest/Playwright config to keep pilot-customer data trustworthy

### Digitenium — AI Engineer Intern *(Jun 2025 – Aug 2025)*
- Built a Python simulation framework (pandas) for a decentralized DeFi liquidity protocol to model asset allocation/redemption flows and engagement; projected **~20%** improvement in asset velocity

### Avalara Technologies Pvt. Ltd. — Senior Software Engineer (Machine Learning) *(Jul 2023 – Aug 2024)*
- Built custom document AI models (**Random Forest, Donut, LayoutXLM, LiLT, spaCy**) for document processing; reduced **AWS Comprehend cost by ~90%**
- Identified and upgraded vulnerable/outdated Python dependencies to improve **security** and **system stability**
- Led onboarding for **8** new hires in ML best practices and internal systems (**50+ hours**)

### Avalara Technologies Pvt. Ltd. — Software Engineer (Machine Learning) *(Jul 2020 – Jun 2023)*
- Evaluated **AWS Comprehend** on a **500-document** training set with **95%+ accuracy**, influencing adoption for an IDP platform impacting **100,000+ documents**
- Automated **30%** of manual document processing across teams; reduced processing time **10 min → 1 min** per document
- Streamlined ML workflows with **ClearML** (experiment tracking + dataset versioning); deployed on **AWS EKS** and ran distributed training on **AWS GPU EC2**, reducing training cost and improving utilization

## Featured Projects

### M.S. Thesis — Low-Rank KV Cache Compression in LLMs: A Second-Order Output Metric and Its Limits *(May 2026 – Aug 2026)*
Master's thesis, **Iowa State University** (advisor: Ali Jannesari). Built a second-order (Gauss-Newton/Fisher) theory of attention-aware low-rank KV cache compression to map both what existing training-free methods can achieve and where they hit a hard ceiling — code, figure sources, and raw result logs for every table/figure are public at [github.com/dhawalshah48/kv-cache-fisher-thesis](https://github.com/dhawalshah48/kv-cache-fisher-thesis).
- **Novel metric:** Derived a closed-form **output-Fisher metric** that scores each key direction by how much compressing it would change the attention *output* (not just the key or the attention logit) — extends the first-order KQ-SVD objective and shows it is a special case; yields the optimal rank-r key basis as a whitened generalized eigenproblem at **zero added inference cost**
- **Benchmarking:** Validated the metric against logit- and variance-based baselines on perplexity (**WikiText-2**) and downstream accuracy (**LongBench**) across **Llama-2-7B, Llama-2-13B**, and, under grouped-query attention, **Mistral-7B**
- **Theoretical framework:** Recast the metric as the diagonal of the true attention-output Hessian, then derived and measured its off-diagonal corrections in closed form (cross-token and cross-key/value "gates") — large as raw distortion, but shown to barely move the loss under aggressive compression
- **Rank allocation:** Uncovered a **~5,000×** spread in per-layer importance that uniform rank allocation ignores; designed a loss-Fisher **water-filling** allocation rule that extends the usable compression frontier to **~16×** and beats the published Swift-SVD allocator at matched budget, generalizing cleanly to grouped-query attention
- **Negative results reported honestly:** Identified and disclosed a failure mode (local-spectrum allocation "detonates") and a case where an architectural baseline (MLA) beats the proposed joint key+value codec — scoping every contribution's actual boundary rather than overselling it
- **Fundamental limit:** Measured the third-order softmax curvature — the error every second-order metric drops — growing from **31% to 60%** of the metric's own magnitude across the usable compression range, and proved it is irreducibly non-quadratic, establishing a hard ceiling on metric-based low-rank KV compression
- **Compute:** Ran large-scale experiments on **Delta** (NCSA, via an NSF ACCESS allocation)

### Mac Pruner *(Dec 2025 – Present)*
- Integrating **MaskLLM gradient-free pruning** into AgenticPruner’s multi-agent framework, targeting ~**50% MAC reduction** across ResNet / ConvNeXt / ViT on ImageNet-1K
- Implementing strict MAC-budget compliance (±1–5% tolerance) to ensure deployability on mobile/edge devices

### Image / Video Captioning *(Aug 2024 – Dec 2024)*
- Built two captioning models: **CNN–LSTM** (InceptionV3) and **ViT–GPT2**
- Trained on **Flickr8k**; ViT–GPT2 improved **BLEU-4 by 486%** (7.91 vs 1.35) and improved **BLEU-1 by 30.2%** (54.3 vs 41.7)

### PopperGame *(Computational Perception Project)*
- Interactive computer-vision game using **OpenCV**: track a real ball in-hand with a camera, detect throw motion, and trigger on-screen balloon collision + popping effect  
- Repo: https://github.com/dhawalshah48/PopperGame *(Python)*

## Technical Skills
- **Languages / Frameworks:** Python, MATLAB, FastAPI, Streamlit, Outsystems, Next.js, React, Tailwind
- **AI / ML:** PyTorch, Hugging Face, fastai, scikit-learn, spaCy, OpenCV, NLP, Deep Learning, Computer Vision, Databricks, ClearML, LangGraph, LangChain, SHAP, LIME
- **LLM Providers / Agents:** OpenAI, Anthropic, Ollama, Qwen/DashScope, multi-agent orchestration, human-in-the-loop workflows
- **Data:** pandas, NumPy, Matplotlib, Spark, Hadoop, PostgreSQL, MongoDB, MySQL, SQLAlchemy, Alembic
- **AWS:** S3, SageMaker, Comprehend, Lambda, Textract, EMR, EKS, EC2, RDS, VPC, ALB
- **DevOps / Tools:** Docker, Docker Compose, Kubernetes, Terraform, Redis, Celery, APScheduler, GitLab CI/CD, GitHub Actions, Git, JWT auth, pytest, Jest, Playwright
- **Research / ML Systems:** SLURM, HPC cluster orchestration (NCSA Delta / ACCESS), A100 GPU benchmarking, bootstrap significance testing, Holm-Bonferroni correction, ablation study design, LongBench, RULER, needle-in-a-haystack (NIAH) evaluation, WikiText-2, KV cache compression, model compression, quantization, low-rank approximation, PCA, Fisher information, Gauss-Newton approximation, spectral/eigen decomposition, RoPE, MHA/GQA/MLA attention variants
