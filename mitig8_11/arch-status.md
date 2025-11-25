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

## Local Development Environment

### Docker Status
- Docker Version: 28.5.2
- Docker Compose Version: v2.40.3-desktop.1
- Status: Installed and ready
- Dockerfile: Not yet created
- docker-compose.yml: Not yet created

### Node.js Status
- Node.js Version: v20.19.4
- npm Version: 10.8.2
- pnpm Version: 9.15.4
- Status: All installed and ready
- package.json: Not yet created

### Development Commands
- Frontend: To be determined (expected: pnpm -C client install|dev|build|lint|test)
- Backend: To be determined (expected: pnpm -C api install|start|test)
- Docker: To be determined (expected: docker-compose up/down)

## Application Architecture

### Frontend (client/)
- Technology: Park UI + Panda CSS
- Framework: To be determined
- Status: Not yet created
- Expected Modules: Survey, Quotes, Valuations, Risk, Reports, Documents, Notifications, Admin Console

### Backend (api/)
- Technology: AWS Lambda functions
- Database: PostgreSQL via RDS Proxy
- Status: Not yet created
- Expected Modules: Authentication, Survey Management, Quote Generation, Risk Assessment, Report Generation, Document Management, Notifications

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

## CloudWatch Log Groups (Existing UAT Environment)

### API Gateway
- `/aws/apigateway/mitig8-uat` - API Gateway logs

### ECS Services
- `/aws/ecs/containerinsights/mitig8-ecs-cluster/performance` - ECS performance metrics
- `/aws/ecs/containerinsights/mitig8-uat-cluster/performance` - UAT ECS performance metrics
- `/ecs/mitig8-api` - API service logs
- `/ecs/mitig8-uat` - UAT service logs
- `ecs-mitig8-api` - API service logs (alternative)

### Lambda Functions
- `/aws/lambda/mitig8-uat-api-v1` - API v1 Lambda
- `/aws/lambda/mitig8-uat-check-password-expiry` - Password expiry check
- `/aws/lambda/mitig8-uat-check-session-timeouts` - Session timeout check
- `/aws/lambda/mitig8-uat-check-sla-breaches` - SLA breach check
- `/aws/lambda/mitig8-uat-geocode-address` - Address geocoding
- `/aws/lambda/mitig8-uat-lambda-health` - Health check
- `/aws/lambda/mitig8-uat-migration-runner` - Database migrations
- `/aws/lambda/mitig8-uat-send-pi-reminders` - Professional indemnity reminders
- `/aws/lambda/mitig8-uat-send-query-notification` - Query notifications
- `/aws/lambda/mitig8-uat-survey-ai-review` - Survey AI review

### Database
- `/aws/rds/proxy/mitig8-uat-rds-proxy` - RDS Proxy logs

### Notes
- Existing UAT environment shows comprehensive Lambda-based architecture
- Multiple specialized Lambda functions for different business operations
- ECS clusters for containerized services
- RDS Proxy for database connectivity
- All log groups have retention policies (1-30 days)

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