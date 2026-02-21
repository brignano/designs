# designs

This repository stores architecture and workflow diagrams as code using [Mermaid](https://mermaid.js.org/), with legacy `.drawio` files kept for reference during migration.

## System Requirements

You do **not** need to install anything to use this repository on GitHub:

- Mermaid diagrams render directly in Markdown on GitHub.
- The source diagrams are plain text `.mmd` files.

Optional local tooling:

- **VS Code Mermaid preview**: install a Mermaid extension for live preview/editing.
- **Export to PNG/SVG/PDF**: install Mermaid CLI via Node.js:
  - `npm install -g @mermaid-js/mermaid-cli`
  - Example: `mmdc -i diagrams/aws-codespaces.mmd -o diagrams/aws-codespaces.svg`

## Diagram Workflow

1. Edit or add diagram source files in `diagrams/*.mmd`.
2. Embed Mermaid blocks in Markdown docs for rendered output on GitHub.
3. Commit the `.mmd` source so diagram changes are cleanly diffable in pull requests.

## Files

### Mermaid (diagram-as-code)

- `diagrams/aws-codespaces.mmd` — AWS Codespaces architecture flow (starter conversion)
- `diagrams/brignano-io.mmd` — brignano.io hosted zone/domain flow (starter conversion)

### Legacy Draw.io

- `aws-codespaces.drawio` — original Draw.io diagram
- `brignano-io.drawio` — original Draw.io diagram

## Notes

- The Mermaid files are initial conversions intended to be refined over time.
- Keep legacy `.drawio` files until you are fully satisfied with Mermaid parity.
