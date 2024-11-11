# Terrform-Library
## 1. Reusable Workflows and Workflow Invocation (workflow_call)

      reusable workflow leverages workflow_call, allowing other workflows to call it with specified inputs and secrets.

      Reusable Workflows: Documentation for a reusable workflow.

GitHub Docs: [GitHub Docs: Reusable Workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows#calling-a-reusable-workflow)

Workflow Inputs: The inputs section allows specifying parameters like bucket_name (required) and region (optional with a default value).

GitHub Docs: [GitHub Docs: Workflow Inputs](https://docs.github.com/en/actions/using-workflows/reusing-workflows#defining-inputs)

Workflow Secrets: The secrets section defines required secrets for the AWS credentials used by Terraform.
GitHub Docs: [Workflow Secrets](https://docs.github.com/en/actions/using-workflows/reusing-workflows#defining-required-secrets)

2. Job Configuration and Runner Types
This workflow has two jobs, terraform-plan and terraform-apply, which each run on a self-hosted runner.

Self-Hosted Runners: Allows you to run jobs on custom hardware or cloud environments that you manage.

GitHub Docs: [Self-Hosted Runners](https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners)

Job Conditionals: We Uses the if keyword to control when jobs run based on events like pull_request or push on specific branches.

GitHub Docs: [Job Conditionals](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idif)
3. Using Environment Variables in Jobs
This workflow sets AWS credentials as environment variables using env.

Environment Variables: The env key in GitHub Actions lets you set environment variables for the entire job.
GitHub Docs: [Environment Variables](https://docs.github.com/en/actions/learn-github-actions/environment-variables)
4. Checkout Action
The actions/checkout@v3 action pulls the repository’s code so that the Terraform commands can access the necessary files.

Checkout Action: Documentation for the checkout action, a common first step in workflows that need repository files.
GitHub Docs: [actions/checkout](https://github.com/actions/checkout)

5. Terraform Commands in GitHub Actions
Both terraform-plan and terraform-apply jobs run Terraform commands, which are customized using inputs passed from the calling workflow.

Terraform Init: Initializes the working directory containing Terraform configuration files.

Terraform Plan: Creates an execution plan, showing changes that will be made without applying them.

Terraform Apply: Applies the changes required to reach the desired state of the configuration.

Terraform CLI Input Variables: Your Terraform commands use -var flags to pass bucket_name and region as variables.

6. We can call this Reusable Workflow from Another Workflow

Calling Reusable Workflows: Documentation for calling a reusable workflow from another workflow.

GitHub Docs: [Calling Reusable Workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows#calling-a-reusable-workflow)

Summary
Each part of your GitHub Actions workflow aligns with specific documentation sections. Following these links will help you understand and customize reusable workflows with Terraform, including parameter passing, job configuration, and runner setup.
