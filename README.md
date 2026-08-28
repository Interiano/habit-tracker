# Habit Tracker

A mobile-first serverless habit tracker on AWS. Sign in, create habits,
track daily completions. Built as a portfolio project by Julio Interiano.

## Architecture

![V1 architecture](docs/architecture.svg)

React PWA (S3 + CloudFront) → Cognito auth → API Gateway (HTTP API)
→ Lambda (Python) → DynamoDB. Infrastructure as code in Terraform,
deployed via GitHub Actions using OIDC.

## Tech stack

| Layer    | Service                     |
|----------|-----------------------------|
| Frontend | React (Vite) PWA            |
| Hosting  | S3 + CloudFront             |
| Auth     | Amazon Cognito              |
| API      | API Gateway HTTP API        |
| Compute  | AWS Lambda (Python 3.12)    |
| Data     | DynamoDB (single table)     |
| IaC      | Terraform                   |
| CI/CD    | GitHub Actions (OIDC)       |

## Prerequisites

- AWS CLI v2, configured with an IAM user (not root)
- Terraform >= 1.9
- Node.js >= 20

## Setup

> One-time bootstrap (Terraform state backend) is documented in docs/.
> Do not commit account IDs, ARNs, or emails to this repo.

```bash
cd infra
terraform init
terraform apply
```

## Project structure

    infra/       Terraform (all AWS resources)
    backend/     Lambda handler (Python)
    frontend/    React PWA
    docs/        architecture diagram, build plan

## Status

- [x] Sprint 0 — account setup, Terraform backend, budget alarm
- [ ] Sprint 1 — DynamoDB single-table
- [ ] Sprint 2 — Lambda CRUD + HTTP API
- [ ] Sprint 3 — Cognito auth
- [ ] Sprint 4 — React frontend
- [ ] Sprint 5 — hosting + CI/CD
- [ ] Sprint 6 — observability + hardening

## License

MIT