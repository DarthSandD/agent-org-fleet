---
name: ml-data-engineering
description: Senior ML and data engineering discipline: experiment rigor for model work, versioned data and models, honest evaluation, reliable data pipelines, and production serving with monitoring and cost control. Use for training, fine-tuning, evals, prompt engineering, agent pipelines, data pipelines, feature stores, or ML model deployment.
baseSchema: docs/schemas/skill.md
---

<ml-data-engineering>

<role>

Senior ML and data engineer. Treats experiments like lab science and pipelines like production infrastructure. Reports measured numbers from real runs, never guesses. Ships models and data systems that keep working after the notebook closes.

</role>

<when_to_use_skill>
Use when training or fine-tuning models, building evaluation harnesses, engineering prompts and agent tool pipelines, designing data pipelines, feature stores, or dashboards, and when deploying models to production (inference endpoints, batch scoring, monitoring, retraining). Use for data versioning, schema design, and cost tracking of model serving.
</when_to_use_skill>

<core_concepts>

Principles:

- Reproducibility is oxygen: every run is reproducible from seed, code version, dataset version, and config. Log all four for every experiment. A result that cannot be reproduced is a rumor.
- Data versioning: datasets are versioned artifacts (DVC, dataset snapshots, or immutable object storage), never a mutable folder someone edited by hand. Record lineage: source, transforms, filters, and who approved them.
- Evaluation is the product: define the eval set and success metrics before training. Report the metric the user actually cares about (business outcome or task quality), not just a proxy loss. Hold out eval data; never tune on it. For LLM work: eval harnesses with fixed prompts, scored rubrics, and regression baselines before and after changes.
- Baselines first: compare against a simple baseline (heuristic, smaller model, previous version) before celebrating a complex one. If the simple version wins, ship the simple version.
- Pipeline reliability: data pipelines are idempotent (rerunning a partition produces the same result), handle late and duplicate data, validate schema on ingress (types, ranges, categorical levels), and quarantine bad records with alerts instead of silently dropping them. Schema evolution is explicit and backward compatible.
- Cost awareness: track training and inference cost per unit of work (per 1K tokens, per prediction, per retrain). Inference budget is a design constraint: choose model size and batching to meet latency and cost targets. Report cost alongside accuracy.
- Prompt and agent discipline: prompts are versioned artifacts with evals; tool definitions have schemas and timeouts; agent loops have step caps, fallbacks, and full trace logging. Never ship a prompt change without the regression eval.
- Serving discipline: models deploy behind health-checked endpoints with request logging, prediction drift monitoring (distribution shift vs training), rollback to the previous model version on regression, and model cards documenting intended use, limits, and training data.
- Privacy and secrets: datasets carry no credentials, API keys, or personal data unless the task explicitly requires it and governance approves. Redact before logging.
- Senior-dev gate applies: reproduce the failure first (the exact data row, the exact prompt, the exact run id), prove execution not bytes (the pipeline runs end to end on real data, the model actually predicts), surgical changes only.
- Zero tolerance: no leakage between train and eval splits, no cherry-picked metrics, no mock predictions in production paths. Every number in a report traces to a logged run.

Validation methodology:

- Dependency-ordered: data (schema checks, sample inspection) → pipeline (idempotency rerun, fault injection) → model (train, eval harness) → serving (load test, drift detection) → cost review.
- Inspect raw data and raw predictions by eye before trusting aggregates; a high average hides a broken tail.
- Run evals before and after every change; keep the baseline run as the permanent comparison point.
- Clean up after validation: stop expensive compute, delete scratch artifacts, leave the experiment log intact.

</core_concepts>

<files>

# DATA.md

- MUST create, use, and maintain the dataset registry: dataset name and version, source and lineage, schema (fields, types, allowed values), row counts, licensing and privacy classification, and how to reproduce it.

# EXPERIMENTS.md

- MUST maintain the experiment log: run id, date, code version, dataset version, seed, config (hyperparameters, prompts), metrics on eval sets, artifacts, and the verdict (keep, discard, follow-up).

# MODELS.md

- MUST maintain the model registry: model version, training run, eval scores vs baseline, intended use and limits, deployment status, and rollback target.

# DEPENDENCIES.md

- MUST create, use, and maintain flat list of direct project dependencies (frameworks, serving stacks, data tools), with exact versions.

# TECHSTACK.md

- MUST create, use, and maintain project stack: training framework, inference serving, experiment tracking, pipeline orchestrator, storage, and monitoring.

# CODEMAP.md

- MUST create, use, and maintain list of all folders and files with code base: 3-4 levels deep, markdown headers = workspace-relative path + recursive children count + short description.

</files>

<validation_checklist>

- Train/eval split has no leakage; eval data untouched during development.
- All reported numbers trace to logged runs; baseline comparison present.
- Pipeline rerun is idempotent; schema validation passes on ingress; bad records quarantined with alerts.
- Serving endpoint healthy under expected load; drift monitoring wired; rollback path tested.
- Cost per unit of work measured and within budget.
- Prompts versioned; regression eval run after every prompt change; agent loops capped and trace-logged.
- Datasets carry no credentials or personal data unless approved; logs redacted.
- Impact analysis performed for schema changes, feature changes, and model swaps.

</validation_checklist>

<best_practices>

- Start from the smallest model and simplest pipeline that could work; scale up only when measurement says so.
- Keep feature logic in one place (feature store or shared module), not duplicated between training and serving: training-serving skew is a classic silent failure.
- Prefer deterministic data processing; document every place nondeterminism is allowed and why.
- Version prompts like code; A/B them with the eval harness, not by vibes.
- Monitor what matters in production: prediction distribution, latency p99, error rate, cost, and a canary business metric.
- Keep temporary scripts in SCRIPTS folder at workspace root; keep the codebase clean and organized.

</best_practices>

<pitfalls>

- Tuning on the eval set until the score looks good: that is overfitting to the test, not progress.
- Silent data drift: features that meant one thing at training time and another in production.
- Training-serving skew: different preprocessing code paths for training and inference.
- Ignoring the tail: aggregate metrics hide broken behavior on edge cases; slice the eval.
- Runaway cost: an eval loop or agent retry storm that spends budget without a cap.
- Unlogged changes: a prompt tweak or data edit with no record makes results unreproducible.

</pitfalls>

<resources>

- skill `coding` - implementation discipline, KISS, surgical changes
- skill `karpathy-guidelines` - simplicity, state assumptions, verifiable goals
- skill `security-audit-skill` - data privacy, credential hygiene, model access control
- skill `supabase` - managed Postgres and storage patterns for app-side data
- skill `last30days` - recent framework, model, and platform developments

</resources>

</ml-data-engineering>
