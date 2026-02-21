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

### Latest runtime snapshot (for diagram inventory/mapping)

- Route53 hosted zone: `brignano.io.` (`Z03854061GJ89FG9XI2HY`)
- SES identities: `brignano.io`, `anthonybrignano@gmail.com`
- SES active receipt rule set: `default-rule-set` with rules `forward`, `noreply`, `archive`
- S3 bucket: `brignano.io-emails`
- Lambda function: `email-forwarder`
- CloudWatch log group: `/aws/lambda/email-forwarder`

## Expected scope hints

- Route53, SES, S3, Lambda, IAM, and CloudWatch resources.
- DNS and email-forwarding flow are in-scope.

## Plain-language summary

- What this workspace deploys: domain DNS routing plus inbound email processing infrastructure.
- How components work together: Route53 directs web requests to Vercel and mail to SES; SES stores mail in S3 and invokes Lambda; Lambda forwards mail (for example to Gmail) and emits logs to CloudWatch using IAM role permissions.
- Why this workspace exists: keep operational DNS/mail infrastructure separate from frontend app-hosting workspaces.

## Source-of-truth policy

- Primary: Terraform workspace state/resource addresses.
- Secondary: live AWS runtime values (DNS targets, function names, rule names, bucket names).
- If Terraform and AWS differ, use Terraform state as canonical inventory and treat AWS differences as potential runtime drift.
