# Copilot Instructions for draw.io diagrams

Context files (diagram-specific):

- Keep per-diagram environment/deployment context in `.github/context/`.
- Read `.github/context/README.md` to map diagram file → context file.
- Before making updates, ask concise clarifying questions whenever any requirement or scope detail is uncertain.
- Before editing a diagram, read its matching context file (for example, `.github/context/aws-config.md` or `.github/context/brignano-io.md`).
- Update context files when workspace mappings, source repos, account context, or scope assumptions change.
- Keep a plain-language summary in each diagram context file describing what the workspace deploys, how the parts work together, and why the scope is separated from other workspaces.
- Keep instructions and context current: after meaningful diagram changes or newly discovered best practices, update `.github/copilot-instructions.md` and/or the relevant `.github/context/*` file in the same change.

When creating or editing `.drawio` files in this repository:

- Treat readability as a hard requirement.
- Any edge label or free text that can overlap connector lines must include a `labelBackgroundColor` that matches its local background (canvas or container) so text remains readable without a visible mismatch.
- For any panel/container text (inventories, summaries, mappings), set `labelBackgroundColor` to match the panel `fillColor` unless the panel uses the default page background.
- Default to an architecture diagram (not an inventory-only text board): include service/resource icons, entities, and relationship edges.
- Show connections and flow explicitly with connectors and edge labels for important interactions (DNS resolution, routing, triggers, permissions, data flow).
- Enforce connector z-order: keep connector/edge `mxCell` elements immediately above the background container cell(s) and below all icon/text vertex cells, so lines never render over icons or node labels.
- Enforce edge-on-edge z-order for readability: when connectors overlap/cross, order overlapping edge `mxCell` elements so the connector whose label sits on/near the overlap is later in XML (foreground) and remains readable above the other connector.
- Prevent visual collisions: lines, edge labels, and node icons/text must not overlap in ways that reduce readability.
- Prefer connectors entering/exiting icon nodes from centered anchors (`entryY=0.5` / `exitY=0.5`) when it preserves readability; use non-centered anchors only when needed to avoid overlap.
- Include all known Terraform-managed resources for the targeted workspace, either as nodes or in a clearly linked inventory panel in the same diagram.
- Include a full Terraform Resource Inventory panel in every deployed-workspace diagram (not optional).
- Include an AWS Runtime Inventory panel in every deployed-workspace diagram (not optional), listing the live AWS resource identifiers for the scoped workspace (for example: hosted zone names/IDs, bucket names, function names, log group names, IAM role names) plus account and region when known.
- Include a Terraform-to-AWS mapping view (table or linked panel) in every deployed-workspace diagram so each Terraform resource address maps to its concrete AWS runtime resource.
- Include a Behavior Summary panel in every deployed-workspace diagram with numbered steps describing order of operations (`1, 2, 3...`) and the what/why/how at each step.
- Add matching numbered markers in the architecture view so each Behavior Summary step maps to a specific point in the diagram flow.
- Place numbered markers adjacent to the related connector segment with a small offset (do not center marker text directly on top of connector lines) to preserve line readability.
- Prefer simple, clean layouts with grouped sections and consistent spacing.
- Keep diagrams scoped to the Terraform workspace being modeled.
- Derive resource lists from Terraform source/state; do not invent resources.
- Use AWS icon shapes when possible and keep naming aligned with Terraform resource names.
- Naming convention: prefer Terraform resource addresses (for example, `aws_route53_zone.default`) as the primary labels for Terraform-managed nodes.
- If useful for readability, include the runtime AWS name (for example, hosted zone or function name) as secondary text, but do not replace the Terraform resource address as the canonical label.
- When creating or updating diagrams, use Terraform Cloud/HCP Terraform data (workspace/state) and AWS data as authoritative sources.
- You may use the Terraform MCP server and AWS MCP server to gather and verify resource details before editing diagrams.
- Keep edits minimal and avoid unnecessary reformatting of unrelated XML.

Verification checklist (for efficiency and correctness):

- If the diagram represents deployed infrastructure in AWS and/or HCP Terraform, verify resources against real state before finalizing.
- For HCP Terraform-managed infrastructure, validate resource addresses against workspace state.
- For AWS-deployed infrastructure, validate relevant live resources in AWS.
- Diagrams must match literal deployed resources for the scoped workspace; do not keep stale or inferred resources.
- For early drafts or conceptual diagrams that are not yet deployed, AWS/Terraform verification is optional.
- Before finalizing, do a visual QA pass: labeled edges must have `labelBackgroundColor` matching local background, and connectors must terminate at node edges without running through icons.
- Before finalizing, do a layering QA pass: connectors must render behind all icons/node labels (only the background container should be behind connector lines).
- Before finalizing, do an edge-overlap QA pass: where two connectors overlap/cross, the connector with the overlapping label must render in front of the other connector.
- Before finalizing, do a mapping QA pass: Behavior Summary step numbers must be unique, sequential, and present in both the summary panel and the corresponding architecture markers.
- Before finalizing, do an inventory QA pass: Terraform inventory, AWS runtime inventory, and Terraform→AWS mapping must be mutually consistent for the scoped workspace.

For edge labels specifically:

- Include `fontColor=#000000` unless an existing style requires something else.
- Set `labelBackgroundColor` to the surrounding background color where the label appears.
- Use `labelBackgroundColor=default` only when the surrounding background is the default page background.
- If the label sits inside a colored container/panel, match that panel’s `fillColor` for the label background.
- Route connectors with waypoints as needed so edge labels remain clear and do not sit on top of icons or other labels.

For summary panels (for example Behavior Summary / Plain-language Summary):

- Set text/label background to match the panel container fill color (do not leave summary text background at `default` inside colored summary containers).

For node labels near connectors:

- If connectors run near a node’s label text, ensure the node label has a matching background (for example `labelBackgroundColor` and/or `fontBackgroundColor`) so node text is visually distinct from edge labels.

For Behavior Summary durability (future you / long-term recall):

- Each numbered step should include: trigger/input, key resource(s) involved (Terraform addresses and/or AWS runtime names), action taken, output/result, and where to observe/debug failures (for example CloudWatch log group or delivery destination).
- Prefer explicit nouns over shorthand (for example `aws_ses_receipt_rule.forward invokes aws_lambda_function.email`) so the flow remains understandable after long gaps.
