# aws-config diagram context

## Diagram

- Diagram file: `aws-config.drawio`
- Terraform Cloud organization: `brignano`
- Terraform Cloud workspace: `aws-config`
- Terraform workspace URL: `https://app.terraform.io/app/brignano/workspaces/aws-config`
- Source repository: `brignano/aws`

## AWS verification context

- AWS account: `549188633263`
- Profile: `default`
- Region: `us-east-1`

## Expected scope hints

- Route53, SES, S3, Lambda, IAM, and CloudWatch resources.
- DNS and email-forwarding flow are in-scope.

## Source-of-truth policy

- Primary: Terraform workspace state/resource addresses.
- Secondary: live AWS runtime values (DNS targets, function names, rule names, bucket names).
- If Terraform and AWS differ, use Terraform state as canonical inventory and treat AWS differences as potential runtime drift.
