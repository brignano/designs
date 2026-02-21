# brignano-io diagram context

## Diagram

- Diagram file: `brignano-io.drawio`
- Terraform Cloud organization: `brignano`
- Terraform Cloud workspace: `brignano-io`
- Terraform workspace URL: `https://app.terraform.io/app/brignano/workspaces/brignano-io`
- Source repository: `brignano/brignano.io`

## AWS verification context

- AWS account: `549188633263`
- Profile: `default`
- Region: `us-east-1`

## Expected scope hints

- Primarily Amplify resources from workspace state.
- Avoid adding non-workspace resources unless explicitly modeled as external dependencies.

## Source-of-truth policy

- Primary: Terraform workspace state/resource addresses.
- Secondary: live AWS runtime values when needed for readability/verification.
- If Terraform and AWS differ, use Terraform state as canonical inventory and treat AWS differences as potential runtime drift.
