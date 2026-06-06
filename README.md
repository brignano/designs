# designs

Architecture and workflow diagrams as code using [Mermaid](https://mermaid.js.org/). Legacy `.drawio` files are kept for reference.

## Diagrams

| File | What it covers |
|------|----------------|
| [`diagrams/aws-config.mmd`](diagrams/aws-config.mmd) | DNS routing + inbound email pipeline (Route53, SES, S3, Lambda, IAM) |
| [`diagrams/brignano-io.mmd`](diagrams/brignano-io.mmd) | Frontend hosting (Amplify app + branch) |

## Workflow

1. Edit or add diagram source files in `diagrams/*.mmd`.
2. Mermaid renders directly in GitHub Markdown — no tooling required to view.
3. Commit `.mmd` source so diagram changes are diffable in pull requests.

### Optional local tooling

- **VS Code**: install a Mermaid extension for live preview.
- **Export PNG/SVG**: `npm install -g @mermaid-js/mermaid-cli` then `mmdc -i diagrams/aws-config.mmd -o diagrams/aws-config.svg`

## Context

Per-diagram environment and Terraform workspace context lives in [`.github/context/`](.github/context/).

## Legacy Draw.io files

- `aws-config.drawio` — original draw.io diagram for aws-config workspace
- `brignano-io.drawio` — original draw.io diagram for brignano-io workspace
