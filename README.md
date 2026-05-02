# spec-as-source-architecture-record

This repository exists to record architecture artifacts only. Its scope is ADRs,
RFP deliverables, diagrams, review notes, templates, and related traceability
material. It is not intended to contain application source code, runtime assets,
or deployment automation.

The governing rules live in `.specify/memory/constitution.md`. In practice, that
means contributions here must favor simplicity, use open-source authoring and
validation tools, preserve clean separation of responsibilities, and keep every
deliverable maintainable, testable, and cloud-agnostic.

When adding or updating artifacts in this repository:

- keep work inside documentation-oriented paths and templates
- justify unnecessary complexity directly in the affected ADR or RFP
- record alternatives, consequences, and validation evidence
- preserve modular structure, reusable patterns, and consistent terminology
- validate links, diagrams, and formatting before review
