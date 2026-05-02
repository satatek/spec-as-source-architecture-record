# Repository Structure Template

Use this template when setting up or reviewing a documentation-only repository for
ADR and RFP artifacts.

## Recommended Layout

```text
adr/
├── records/                  # Canonical ADR documents
├── diagrams/                 # Diagrams referenced by ADRs
└── templates/                # Optional ADR-specific helpers

rfp/
├── deliverables/             # Canonical RFP documents
├── diagrams/                 # Diagrams referenced by RFPs
└── templates/                # Optional RFP-specific helpers

releases/
├── manifests/                # Release records linking ADRs and RFPs
└── changelogs/               # Release summaries for changed document sets

reviews/
├── adr/                      # ADR review notes and approvals
├── rfp/                      # RFP review notes and approvals
└── releases/                 # Release-level validation and approval evidence

templates/
├── adr-template.md
├── rfp-template.md
└── release-manifest-template.md

docs/
└── glossary/                 # Shared terminology and repository conventions
```

## Directory Rules

- `adr/records/` is the single source of truth for ADR files.
- `rfp/deliverables/` is the single source of truth for RFP files.
- `releases/manifests/` links a release to the ADRs and RFPs governed by that release.
- `reviews/` stores validation evidence and approval notes rather than mixing them into source artifacts.
- `templates/` holds reusable authoring templates shared across contributors.
- `docs/glossary/` keeps terminology and conventions centralized.

## Suggested File Naming

- ADR: `adr-0001-short-title.md`
- RFP: `rfp-0001-short-title.md`
- Release manifest: `v0.1.0.md`
- Release changelog: `v0.1.0.md`

## Optional Metadata To Standardize

For both ADRs and RFPs, consider using the same metadata block:

```md
- ID:
- Title:
- Status: draft
- Owner:
- Reviewers:
- Release References:
- Related Artifacts:
```

## Lifecycle States

Use a small, fixed vocabulary to keep reviews predictable:

- `draft`
- `approved`
- `superseded`
- `archived`

## Review Checklist Starter

- Is the file in the correct directory?
- Does it use the standard naming convention?
- Does it link related ADRs, RFPs, or release manifests?
- Is status explicit and valid?
- Is review or validation evidence recorded separately in `reviews/`?

## Notes

- Keep this repository documentation-only. Do not mix runtime code or deployment assets into this structure.
- Prefer canonical documents plus release manifests over copying ADRs or RFPs into release folders.