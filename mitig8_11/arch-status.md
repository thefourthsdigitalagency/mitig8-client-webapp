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

### AWS CLI Status
- AWS CLI Version: 2.30.7
- Authentication: Configured and working
- AWS Account: 879937386092
- IAM Identity: root

### Terraform Status
- Terraform Version: 1.5.7 (out of date - latest is 1.14.0)
- Infrastructure Directory: Not yet created (expected at infrastructure/terraform/)
- Terraform Backend: Not yet configured
- S3 State Bucket: Not yet confirmed

### Notes
- AWS CLI is properly installed and authenticated
- Terraform is installed but should be updated to latest version
- Infrastructure directory and Terraform backend will be created in future milestones

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