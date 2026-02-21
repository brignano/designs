# designs

This repository is a personal collection of diagrams created with [draw.io](https://www.drawio.com/). It serves as a central place to store, organize, and version control various visual designs, architecture diagrams, workflows, and other graphical documentation.

## About

All files in this repository are in the `.drawio` format, which can be opened and edited using the draw.io web app or desktop application. Saving your diagrams in a GitHub repository like this allows you to:

- Keep a versioned history of your diagrams
- Collaborate or share diagrams easily
- Access your diagrams from anywhere
- Back up your work securely

## Usage

1. **Viewing/Editing Diagrams:**
	- Download any `.drawio` file and open it in [draw.io](https://app.diagrams.net/) or the desktop app.
	- You can also use the [draw.io VS Code extension](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio) to view and edit diagrams directly in VS Code.

2. **Adding New Diagrams:**
	- Create a new diagram in draw.io and save it as a `.drawio` file.
	- Commit and push the file to this repository.

3. **Version Control:**
	- Use Git to track changes, revert to previous versions, and collaborate with others if desired.

## Files

- `aws-config.drawio` — DNS + email-forwarding architecture and Terraform/AWS mapping
- `brignano-io.drawio` — Amplify app/branch workspace architecture

## Plain-English Workspace Summaries

### aws-config workspace

- **What it deploys:** DNS zones/records (Route53), inbound email handling (SES receipt rules), email archive storage (S3), forwarding logic (Lambda), permissions (IAM), and logs (CloudWatch).
- **How it works together:** DNS sends website traffic to Vercel and email traffic to SES. SES stores incoming email in S3 and triggers Lambda. Lambda reads content, forwards it to Gmail, and writes logs to CloudWatch.
- **Why this workspace exists:** It centralizes domain routing and mail-processing infrastructure.

### brignano-io workspace

- **What it deploys:** Only two resources: `aws_amplify_app.brignano_io` and `aws_amplify_branch.main`.
- **How it works together:** The Amplify app is the container for the frontend deployment, and the `main` branch resource tells Amplify which branch/environment to build and serve.
- **Why only two resources:** This workspace is intentionally scoped to application hosting setup. DNS/email/security supporting services are managed in `aws-config`, not duplicated here.

Feel free to explore, clone, or contribute new diagrams!
