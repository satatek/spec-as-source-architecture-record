# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]
**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`

**Note**: This template is filled in by the `/speckit.plan` command. See `.specify/templates/plan-template.md` for the execution workflow.

## Summary

[Extract from feature spec: primary requirement + technical approach from research]

## Technical Context

<!--
  ACTION REQUIRED: Replace the content in this section with the technical details
  for the project. The structure here is presented in advisory capacity to guide
  the iteration process.
-->

**Artifact Format**: [e.g., Markdown ADRs, Markdown RFP, Mermaid, PlantUML or NEEDS CLARIFICATION]  
**Primary Dependencies**: [e.g., markdownlint, Vale, Mermaid CLI, link checker or NEEDS CLARIFICATION]  
**Storage**: [e.g., Git-tracked files in repository or NEEDS CLARIFICATION]  
**Validation**: [e.g., markdown lint, link check, diagram validation, peer review or NEEDS CLARIFICATION]  
**Target Platform**: [e.g., GitHub readers, static docs preview, CI validation or NEEDS CLARIFICATION]
**Project Type**: [e.g., ADR set, RFP package, architecture record repository or NEEDS CLARIFICATION]  
**Performance Goals**: [e.g., diagrams render in CI, links validate in one run or NEEDS CLARIFICATION]  
**Constraints**: [e.g., open-source tools only, cloud-agnostic wording, no source code in repo]  
**Scale/Scope**: [e.g., number of records, decision areas, reviewers, linked documents]

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- Documentation-only scope preserved; no runtime code or build artifacts are introduced.
- Proposed workflow uses open-source authoring and validation tools only.
- The document set favors the simplest viable structure and explains rejected complexity.
- Responsibilities, interfaces, validation approach, and modular boundaries are explicit.
- Deliverables remain maintainable, cloud-agnostic, and consistent with existing ADR/RFP patterns.

## Project Structure

### Documentation (this feature)

```text
specs/[###-feature]/
├── plan.md              # This file (/speckit.plan command output)
├── research.md          # Phase 0 output (/speckit.plan command)
├── data-model.md        # Phase 1 output (/speckit.plan command)
├── quickstart.md        # Phase 1 output (/speckit.plan command)
├── contracts/           # Phase 1 output (/speckit.plan command)
└── tasks.md             # Phase 2 output (/speckit.tasks command - NOT created by /speckit.plan)
```

### Repository Artifacts (repository root)
<!--
  ACTION REQUIRED: Replace the placeholder tree below with the concrete layout
  for this documentation effort. Delete unused options and expand the chosen
  structure with real paths (e.g., adr/, rfp/, diagrams/, templates/). The
  delivered plan must not include Option labels.
-->

```text
# [REMOVE IF UNUSED] Option 1: ADR-focused change
adr/
├── templates/
├── records/
└── diagrams/

reviews/
└── adr/

# [REMOVE IF UNUSED] Option 2: RFP-focused change
rfp/
├── templates/
├── deliverables/
└── diagrams/

reviews/
└── rfp/

# [REMOVE IF UNUSED] Option 3: Shared architecture knowledge base
docs/
├── decisions/
├── proposals/
├── diagrams/
└── glossary/

templates/
└── architecture/
```

**Structure Decision**: [Document the selected structure and reference the real
directories captured above]

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| [e.g., provider-specific terminology] | [documented business constraint] | [why cloud-agnostic wording is inaccurate] |
| [e.g., proprietary validation service] | [temporary migration need] | [why open-source alternative cannot satisfy current gate] |
