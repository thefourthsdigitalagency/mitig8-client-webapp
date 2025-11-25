# Mitig8_11 Runner Spec (NEW repo version – v6)

This file explains how to drive `mitig8_11/orchestrator.json`.

## Structure

- `global_prompt` – Shared rules and guardrails.
- `milestones[]` – Ordered list of milestones (M0–M7).
- Each milestone:
  - `id`, `name`, `description`, `engagement`.
  - `tasks[]` – Ordered tasks:
    - `id`, `name`, `role`, `environment`, `description`, `auto_next`, `prompt`.

## How to Run in TRAE

1. Create or clone the NEW Mitig8 repo, for example into:
   - `/Users/dominicnel/mitig8_client_webapp`
2. Ensure the repo root contains:
   - `mitig8_11/` (this folder).
   - Eventually: `client/`, `api/`, `infrastructure/terraform/`, etc.
3. Open the **repo root folder** (not the `mitig8_11` folder) in TRAE.
4. Load `mitig8_11/orchestrator.json`.

### Prompt Execution

For each task:
- Construct the final prompt as:

  `final_prompt = global_prompt + "\n\n" + task.prompt`

- Send `final_prompt` to the ChatGPT/OpenAI bot with `TRAEBOT_SYSTEM_INSTRUCTIONS` as system instructions.

### Task Ordering

- Start at M0 → task `M0-T0` (Git & GitHub bootstrap).
- Within a milestone:
  - Execute tasks in array order.
  - If `auto_next` is `true`:
    - Move to the next task automatically after completion.
  - If `auto_next` is `false`:
    - STOP and wait for human approval to continue.

- After each milestone's final task (QA + archive), a human must:
  - Review:
    - The milestone summary in `mitig8_11/milestones-Mx*.md`.
    - The zip in `artifacts/mitig8-Mx-*.zip`.
  - Explicitly instruct TRAE to move to the next milestone (e.g., “Start M2 now”).

### Archives

Milestone QA tasks instruct the agent to create an archive using a command such as:

- `mkdir -p artifacts && zip -r artifacts/mitig8-Mx-<name>.zip . -x 'artifacts/*'`

This must be run from the repo root; no absolute paths are required.

### Behaviour Enforcement

Where possible, the runner should:

- Fail-fast if the agent reports failing tests or unrecoverable errors.
- Avoid skipping tasks or milestones.
- Optionally verify that:
  - No Terraform files are modified by tasks.
  - Only known directories are touched.

The runner should not attempt to interpret or modify application logic; that is the bot’s responsibility under the global prompt and system instructions.