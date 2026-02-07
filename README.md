# Multi-Environment IaC Orchestrator (Terraform + Ansible)

## Summary
Designed and implemented an end‑to‑end Infrastructure‑as‑Code workflow that provisions multi‑environment AWS infrastructure with Terraform and configures instances with Ansible. The project demonstrates modular IaC, environment separation (dev/stage/prod), automated configuration, and repeatable teardown.

## What I Built
- Terraform modules to provision EC2, S3, and DynamoDB with environment‑specific inputs.
- Remote state and state locking with S3 + DynamoDB.
- Ansible playbooks and roles to install/configure Nginx across all environments.
- Dynamic inventory generation by pulling Terraform outputs into Ansible inventory files.
- Automated workflows for init/plan/apply and destroy.

## Skills Demonstrated
- Terraform modules, variables, outputs, and backend configuration
- AWS infrastructure provisioning (EC2, S3, DynamoDB)
- Ansible roles, playbooks, and inventory management
- Environment isolation and repeatable automation

## Project Structure (High‑Level)
- `terraform/` — IaC modules, providers, backend, and environment instantiation
- `ansible/` — inventories, playbooks, and `nginx-role`

## How It Runs (High‑Level)
1. Provision infra per environment with Terraform (dev/stage/prod).
2. Generate dynamic Ansible inventories from Terraform outputs.
3. Apply Nginx configuration consistently across environments.
4. Tear down with Terraform destroy when finished.

## Outcomes
- Repeatable, modular deployment pipeline for three isolated environments
- Automated configuration management with consistent server setup
- Clear separation of provisioning vs. configuration concerns

## Notes
This is a portfolio project focused on clean, reproducible infrastructure automation rather than production hardening.
