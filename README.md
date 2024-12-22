# Terraform Composite GitHub Actions

This repository contains two composite GitHub Actions for running Terraform
commands in your GitHub Workflows. These actions encapsulate commonly used
steps for planning and applying Terraform configurations.


## Overview

1. **Terraform Plan**  
   This composite action runs `terraform init`, `terraform fmt` and `terraform
plan`, ensuring your Terraform configuration is properly initialized and
validated. It also comments the plan in the PR if it exists.  Use this action
to see what changes would be made to your infrastructure without actually
applying them.

2. **Terraform Apply**  
   This composite action runs `terraform init` (to ensure initialization if not
already done) and `terraform apply`, actually creating, modifying, or deleting
resources in your infrastructure based on the plan.

Both actions are designed to be used within GitHub Actions workflows and rely
on a few key inputs, such as the path to your Terraform configuration folder
(`chdir`) and your GitHub token (`github-token`).

---

## Usage

Below are examples of how to use each composite action in your GitHub workflow:

### Plan Terraform

```yaml
- name: Plan terraform
  uses: blackbook-ai-technologies/github-actions/terraform-plan@main
  with:
    chdir: ${{ env.TERRAFORM_FOLDER }}
    github-token: ${{ secrets.GITHUB_TOKEN }}
```

### Apply Terraform

```yaml
- name: Apply terraform
  uses: blackbook-ai-technologies/github-actions/terraform-apply@main
  with:
    chdir: ${{ env.TERRAFORM_FOLDER }}
    github-token: ${{ secrets.GITHUB_TOKEN }}
```
