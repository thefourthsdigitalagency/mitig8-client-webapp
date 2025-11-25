# Mitig8 Architecture Status (M0)

## Current Repository Structure

```
Mitig8_Client_WebApp/
├── .git/
├── .gitignore
├── README.md
└── mitig8_11/
    ├── FIRST_RUN_PROMPT.txt
    ├── README.md
    ├── TRAEBOT_SYSTEM_INSTRUCTIONS.md
    ├── orchestrator.json
    └── runner-spec.md
```

## Expected vs. Actual Structure

### Expected (per orchestrator):
- `client/` - Frontend SPA using Park UI + Panda CSS
- `api/` - Backend Lambdas talking to Postgres
- `infrastructure/terraform/` - AWS infrastructure managed by Terraform
- `mitig8_11/` - Orchestration bundle ✓

### Actual:
- `mitig8_11/` - Orchestration bundle ✓
- Missing: `client/`, `api/`, `infrastructure/terraform/`

## AWS Infrastructure (Terraform)

Not yet confirmed - will be verified in M0-T2.

## Application Architecture

### Frontend (client/)
- Technology: Park UI + Panda CSS
- Framework: To be determined
- Status: Not yet created

### Backend (api/)
- Technology: AWS Lambda functions
- Database: PostgreSQL via RDS Proxy
- Status: Not yet created

### Infrastructure (infrastructure/terraform/)
- Cloud Provider: AWS
- Services:
  - API Gateway HTTP API
  - Lambda functions
  - RDS Proxy → PostgreSQL
  - EventBridge rules
  - SSM Parameter Store
  - CloudWatch Logs
  - IAM Roles
  - S3 backend for Terraform state
  - CI/CD bound to UAT/PROD branches
- Status: Not yet created

## Milestone Progress

- M0-T0: Git & GitHub bootstrap - ✓ Completed
- M0-T1: Create Mitig8_11 docs & confirm repo - In Progress
- M0-T2: AWS CLI & Terraform connectivity - Pending
- M0-T3: Local dev & Docker baseline - Pending
- M0-T4: Architecture audit & log mapping - Pending
- M0-T5: Baseline error categories - Pending
- M0-T6: Archive M0 snapshot - Pending

## Notes

- This is a NEW repository setup with the Mitig8_11 orchestration bundle
- The repository is connected to GitHub: https://github.com/thefourthsdigitalagency/mitig8-client-webapp
- The actual application code (client/, api/, infrastructure/) is expected to be added in future milestones