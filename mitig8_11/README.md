# Mitig8_11 Orchestration Bundle (v6 – NEW repo)

This folder (`mitig8_11/`) lives in the **root of the NEW Mitig8 repo**, for example:

- `/Users/dominicnel/mitig8_client_webapp/mitig8_11`

You will open the **repo root folder** (e.g. `mitig8_client_webapp`) in TRAE.  
From there, the orchestrator uses relative paths like:

- `client/`, `api/`, `infrastructure/terraform/`, `mitig8_11/`

## Contents

- `orchestrator.json` – All milestones M0–M7, tasks, prompts and guardrails.
- `README.md` – This file.
- `runner-spec.md` – How a small harness or TRAE should walk through the orchestrator.
- `TRAEBOT_SYSTEM_INSTRUCTIONS.md` – System prompt for the ChatGPT/OpenAI bot used by TRAE.
- `FIRST_RUN_PROMPT.txt` – The startup prompt you paste into TRAE.
- `prompts/` – Empty; optional runtime notes.

Runtime docs created later:
- `mitig8_11/arch-status.md`
- `mitig8_11/milestones-M0.md`, `mitig8_11/milestones-M1.md`, …
- `mitig8_11/prod-runbook.md`
- `mitig8_11/milestones-M7-*.md`
- `artifacts/mitig8-M*-*.zip` at repo root

## High-level Milestones

- **M0 – Setup, Git, AWS, Docker & Architecture Baseline**
  - NEW: `M0-T0` initialises Git repo, `.gitignore`, README, and optionally a GitHub remote via `gh`.
  - Confirm repo structure and Mitig8_11 docs.
  - Check AWS CLI, identity, S3 state bucket, Terraform backend (read-only).
  - Discover dev and Docker commands.
  - Audit current modules vs SOW and map log groups.
  - Document baseline error categories.
  - Archive as `mitig8-M0-foundation.zip`.

- **M1 – Design System, Docker & Shell**
  - Install Park UI + Panda CSS.
  - Implement local Docker (Dockerfile + docker-compose).
  - Apply shell to Login, Landing, Assessments.
  - Archive as `mitig8-M1-design-docker.zip`.

- **M2 – Survey Engine**
  - Backend (all templates + Review logic).
  - Frontend (Park UI survey flows, Review tab).
  - Export/print layout.
  - Archive as `mitig8-M2-survey-engine.zip`.

- **M3 – Quotes & Pricing**
  - Quotes backend (lifecycle + pricing rules).
  - Quotes UI for surveyors and insurers.
  - Archive as `mitig8-M3-quotes.zip`.

- **M4 – Surveyors & Scheduling**
  - Surveyor profile + PI backend.
  - Profile & scheduling UI.
  - Archive as `mitig8-M4-surveyors.zip`.

- **M5 – Risk, Reports, Documents, Finance**
  - Backend for risk & reports.
  - UI for risk, reports, docs & finance tabs.
  - Archive as `mitig8-M5-risk-reports.zip`.

- **M6 – Admin, Notifications, Integrations**
  - Admin/config backend.
  - Admin & notifications UI.
  - Integrations backend.
  - Archive as `mitig8-M6-admin.zip`.

- **M7 – UAT Hardening & PROD Launch**
  - Full regression & UAT hardening.
  - PROD runbook.
  - Final archive `mitig8-M7-prod-launch.zip`.

## Behavioural Guardrails

All tasks:

- Use SPEC / BLOAT / LOGS / TERRAFORM checks.
- Treat failing tests as blocking.
- Only modify files listed in their own BLOAT CHECK.
- Never edit Terraform or CI/CD.
- Use relative paths only (no `/Users/.../mitig810/...`).
- Stop after each milestone archive until you explicitly approve moving on.

See `TRAEBOT_SYSTEM_INSTRUCTIONS.md` for the exact system instructions given to the TRAE bot.