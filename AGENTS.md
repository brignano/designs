# designs — AI Context

## What this repo is

Architecture and workflow diagrams as code using [Mermaid](https://mermaid.js.org/). Diagrams represent deployed Terraform-managed AWS infrastructure. Legacy `.drawio` files are kept for reference.

## Diagrams

| File | Terraform workspace | What it covers |
|------|--------------------|-|
| [`diagrams/aws-config.mmd`](diagrams/aws-config.mmd) | `aws-config` | DNS routing + inbound email pipeline (Route53, SES, S3, Lambda, IAM) |
| [`diagrams/brignano-io.mmd`](diagrams/brignano-io.mmd) | `brignano-io` | Frontend hosting (Amplify app + branch) |

Per-diagram Terraform workspace and AWS runtime context lives in [`.github/context/`](.github/context/).

## How to help

- Read the relevant `.github/context/*.md` file before creating or editing a diagram — it has the Terraform workspace, AWS account, resource identifiers, and scope rules.
- Update context files when workspace mappings, resource names, account context, or scope assumptions change.

## Creating or editing diagrams

- Use `flowchart LR` as the default layout.
- Label nodes with Terraform resource addresses as the primary identifier (e.g. `aws_lambda_function.email_forwarder`).
- Include the AWS runtime name as secondary text on the node when it aids readability.
- Show all Terraform-managed resources for the scoped workspace — do not omit resources.
- Show external dependencies (e.g. Vercel, GitHub, Gmail) as plain nodes outside subgraphs.
- Use subgraphs to group resources by AWS service or logical layer.
- Use solid arrows for data/traffic flow and dotted arrows for permissions/assumed roles.
- Label every edge that carries meaningful semantic content.
- Keep diagrams scoped to the Terraform workspace being modeled — do not duplicate resources from other workspaces.

## Verification

- For deployed infrastructure, verify resource addresses against Terraform Cloud workspace state before finalizing.
- Cross-check live AWS resources against the runtime snapshot in the context file.
- If Terraform state and AWS differ, use Terraform state as canonical and note the drift.
- For early drafts or conceptual diagrams not yet deployed, verification is optional.

## Token usage

- Read only the relevant context file and diagram source before making changes — do not scan the full repo.
- Targeted grep is preferred over broad file reads for lookups.
