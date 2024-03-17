# Github Reusable workflows
## Terraform reusable workflow

### Full example 
```yaml
jobs:
  plan-ephemeral:
    uses: carlosgit2016/reusable-workflows/.github/workflows/terraform.yaml@main
    with:
      validate: true
      pr: true # Will comment in the PR
      fmt-check: true # Will check the .tf files format and fail in case of any format issues
      workspace: default # Workspace to be used, it will create in case do not exists 
      working-dir: infrastructure # Workdir where the resources are in 
      role-to-assume: somerole # AWS Role to be assumed
```

### Basic example
```yaml
jobs:
  plan-ephemeral:
    uses: carlosgit2016/reusable-workflows/.github/workflows/terraform.yaml@main
    with:
      working-dir: ./
```

### Parameters
`validate`: Whether to perform terraform validate to check the configuration for errors.


`plan`: Whether to execute terraform plan to show changes required to reach the desired state of the configuration.


`apply`: Determines if terraform apply should be executed to apply the changes specified by the plan.


`destroy`: Indicates if terraform destroy should be run to remove all resources defined in the Terraform configuration.


`fmt-check`: Enables a check for the correct formatting of the Terraform files using terraform fmt.


`workspace`: The Terraform workspace to use for the operation. Workspaces support managing different states of the infrastructure according to the environment.


`working-dir`: The working directory where Terraform commands are run. This should contain your .tf files.


`role-to-assume`: Specifies the AWS IAM role that the GitHub Actions workflow should assume before executing Terraform commands. This is necessary for AWS provider authentication.


`pr`: Whether or not to comment on the pull request with the plan's outcome.
