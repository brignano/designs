# Diagram Context Index

Use this folder for diagram-specific deployment context so `.github/copilot-instructions.md` can stay concise.

## Mapping

- `aws-config.drawio` → `.github/context/aws-config.md`
- `brignano-io.drawio` → `.github/context/brignano-io.md`

## Usage

When editing a diagram:

1. Read `.github/copilot-instructions.md` for global formatting, readability, and verification rules.
2. Read the matching file in this folder for workspace/repo/account specifics.
3. Validate against literal sources (Terraform state + AWS APIs) when diagram reflects deployed infra.
