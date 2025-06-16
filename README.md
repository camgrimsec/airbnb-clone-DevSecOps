# DevSecOps Pipeline for Airbnb Clone

This repository combines the application code and infrastructure required to deploy the Airbnb clone.
The `.github/workflows/main.yml` workflow performs automated security checks, tests and deployment to AWS.

## Workflow Overview
- **pre-build** – initializes CodeQL and runs basic linting and formatting checks.
- **code-analysis** – caches dependencies and runs ESLint and SonarQube scanning.
- **security-scan** – uses Snyk and OWASP Dependency Check.
- **build-test** – builds the API and executes unit tests.
- **container-scan** – builds Docker images and pushes them to Amazon ECR after scanning.
- **aws-deploy** – deploys the containers to ECS and uploads the frontend to S3.
- **infrastructure** – applies Terraform configuration under `infra/terraform`.
- **deploy** – deploys Kubernetes manifests as an example.
- **post-build** – publishes images to Docker Hub and collects basic metrics.

Secrets such as AWS credentials or SonarQube tokens must be configured in the repository settings for the workflow to succeed.
