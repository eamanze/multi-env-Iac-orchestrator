# Execution Guide

This guide explains how to run the project locally to provision AWS infrastructure with Terraform and configure instances with Ansible.

## Prerequisites
- AWS account and credentials configured in your environment
- Terraform installed
- Ansible installed
- SSH key pair for EC2 access

## 1) Configure AWS Credentials
Ensure your AWS credentials are available in your shell environment (for example via `aws configure` or environment variables).

## 2) Generate SSH Keys (Optional if you already have one)
From the project root:

```bash
ssh-keygen -t rsa -b 2048 -f devops-key -N ""
```

## 3) Provision Infrastructure with Terraform
From the project root:

```bash
cd terraform
terraform init
terraform plan
terraform apply
```

## 4) Update Ansible Inventories from Terraform Outputs
From the project root:

```bash
cd ansible
chmod +x update_inventories.sh
./update_inventories.sh
```

## 5) Configure Servers with Ansible (Nginx)
From the project root:

```bash
cd ansible
ansible-playbook -i inventories/dev playbooks/install_nginx_playbook.yml
ansible-playbook -i inventories/stg playbooks/install_nginx_playbook.yml
ansible-playbook -i inventories/prod playbooks/install_nginx_playbook.yml
```

## 6) Verify
Open each EC2 public IP in a browser to confirm the Nginx page loads.

## 7) Tear Down (When Finished)
From the project root:

```bash
cd terraform
terraform destroy --auto-approve
```

## Notes
- Ensure your security group allows SSH (22) and HTTP (80) access from your IP.
- If you use a different SSH key name, update references accordingly in Terraform and Ansible inventory generation.
