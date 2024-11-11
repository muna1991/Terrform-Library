# Terrform-Library
1. Reusable Workflows and Workflow Invocation (workflow_call)

reusable workflow leverages workflow_call, allowing other workflows to call it with specified inputs and secrets.

Reusable Workflows: Documentation for calling a reusable workflow with workflow_call trigger.

GitHub Docs: https://docs.github.com/en/actions/using-workflows/reusing-workflows#calling-a-reusable-workflow

Workflow Inputs: The inputs section allows specifying parameters like bucket_name (required) and region (optional with a default value).

GitHub Docs: [GitHub](https://github.com)

Workflow Secrets: The secrets section defines required secrets for the AWS credentials used by Terraform.

GitHub Docs: Workflow Secrets
2. Job Configuration and Runner Types
Your workflow has two jobs, terraform-plan and terraform-apply, which each run on a self-hosted runner.

Self-Hosted Runners: Allows you to run jobs on custom hardware or cloud environments that you manage.

GitHub Docs: Self-Hosted Runners
Job Conditionals: Uses the if key to control when jobs run based on events like pull_request or push on specific branches.

GitHub Docs: Job Conditionals
3. Using Environment Variables in Jobs
Your workflow sets AWS credentials as environment variables using env.

Environment Variables: The env key in GitHub Actions lets you set environment variables for the entire job.
GitHub Docs: Environment Variables
4. Checkout Action
The actions/checkout@v3 action pulls the repository’s code so that the Terraform commands can access the necessary files.

Checkout Action: Documentation for the checkout action, a common first step in workflows that need repository files.
GitHub Docs: actions/checkout
5. Terraform Commands in GitHub Actions
Both terraform-plan and terraform-apply jobs run Terraform commands, which are customized using inputs passed from the calling workflow.

Terraform Init: Initializes the working directory containing Terraform configuration files.

Terraform CLI Docs: terraform init
Terraform Plan: Creates an execution plan, showing changes that will be made without applying them.

Terraform CLI Docs: terraform plan
Terraform Apply: Applies the changes required to reach the desired state of the configuration.

Terraform CLI Docs: terraform apply
Terraform CLI Input Variables: Your Terraform commands use -var flags to pass bucket_name and region as variables.

Terraform CLI Docs: Input Variables
6. Calling the Reusable Workflow from Another Workflow
An example of invoking this reusable workflow is provided below, where it’s called from another workflow file.

yaml
Copy code
# File: .github/workflows/deploy-s3.yml

name: "Deploy S3 Bucket"

on:
  pull_request:
    branches:
      - main
  push:
    branches:
      - main

jobs:
  deploy:
    uses: your-org/your-repo/.github/workflows/terraform_s3_bucket.yml@main
    with:
      bucket_name: "example-bucket-name"
      region: "us-west-2"
    secrets:
      aws_access_key_id: ${{ secrets.AWS_ACCESS_KEY_ID }}
      aws_secret_access_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
This file calls terraform_s3_bucket.yml with specified inputs and secrets, showing how to trigger the reusable workflow on specific events.

Calling Reusable Workflows: Documentation for calling a reusable workflow from another workflow.
GitHub Docs: Calling Reusable Workflows
Summary
Each part of your GitHub Actions workflow aligns with specific documentation sections. Following these links will help you understand and customize reusable workflows with Terraform, including parameter passing, job configuration, and runner setup.
