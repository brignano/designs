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

### Latest runtime snapshot (for diagram inventory/mapping)

- Amplify runtime app listing currently blocked with `AccessDenied` for `amplify:ListApps`.
- Terraform state remains the canonical source for app/branch scope until Amplify read permissions are granted.

## Expected scope hints

- Primarily Amplify resources from workspace state.
- Avoid adding non-workspace resources unless explicitly modeled as external dependencies.

## Plain-language summary

- What this workspace deploys: only two Terraform resources — `aws_amplify_app.brignano_io` and `aws_amplify_branch.main`.
- How those two resources work together: the Amplify app is the hosting/application object, and the branch resource binds your `main` branch to that app so builds/deployments run for that branch.
- Why there are only two resources: this workspace is intentionally minimal and focused on frontend hosting setup; DNS, email routing/processing, and related infrastructure are managed by the separate `aws-config` workspace.

## Source-of-truth policy

- Primary: Terraform workspace state/resource addresses.
- Secondary: live AWS runtime values when needed for readability/verification.
- If Terraform and AWS differ, use Terraform state as canonical inventory and treat AWS differences as potential runtime drift.
