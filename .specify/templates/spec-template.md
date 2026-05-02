# Architecture Work Specification: [FEATURE NAME]

**Feature Branch**: `[###-feature-name]`  
**Created**: [DATE]  
**Status**: Draft  
**Input**: User description: "$ARGUMENTS"

## User Scenarios & Testing *(mandatory)*

<!--
  IMPORTANT: User stories should be PRIORITIZED as user journeys ordered by importance.
  Each user story/journey must be INDEPENDENTLY TESTABLE - meaning if you implement just ONE of them,
  you should still have a viable MVP (Minimum Viable Product) that delivers value.
  
  Assign priorities (P1, P2, P3, etc.) to each story, where P1 is the most critical.
  Think of each story as a standalone documentation outcome that can be:
  - Authored independently
  - Reviewed independently
  - Validated independently
  - Published independently
-->

### User Story 1 - [Brief Title] (Priority: P1)

[Describe this documentation journey in plain language]

**Why this priority**: [Explain the value and why it has this priority level]

**Independent Test**: [Describe how this can be validated independently - e.g., "Can be reviewed by [specific action] and delivers [specific value]"]

**Acceptance Scenarios**:

1. **Given** [initial state], **When** [action], **Then** [expected outcome]
2. **Given** [initial state], **When** [action], **Then** [expected outcome]

---

### User Story 2 - [Brief Title] (Priority: P2)

[Describe this user journey in plain language]

**Why this priority**: [Explain the value and why it has this priority level]

**Independent Test**: [Describe how this can be tested independently]

**Acceptance Scenarios**:

1. **Given** [initial state], **When** [action], **Then** [expected outcome]

---

### User Story 3 - [Brief Title] (Priority: P3)

[Describe this user journey in plain language]

**Why this priority**: [Explain the value and why it has this priority level]

**Independent Test**: [Describe how this can be tested independently]

**Acceptance Scenarios**:

1. **Given** [initial state], **When** [action], **Then** [expected outcome]

---

[Add more user stories as needed, each with an assigned priority]

### Edge Cases

<!--
  ACTION REQUIRED: The content in this section represents placeholders.
  Fill them out with the right edge cases.
-->

- What happens when [boundary condition]?
- How are broken references, stale diagrams, or missing validation evidence handled?

## Requirements *(mandatory)*

<!--
  ACTION REQUIRED: The content in this section represents placeholders.
  Fill them out with the right functional requirements.
-->

### Functional Requirements

- **FR-001**: The repository MUST produce [specific architecture artifact, e.g., "an ADR that records the chosen integration pattern"]
- **FR-002**: The work item MUST document [specific constraint, e.g., "alternatives considered and rejection rationale"]  
- **FR-003**: Reviewers MUST be able to [key interaction, e.g., "trace an RFP requirement to supporting architecture evidence"]
- **FR-004**: The repository MUST maintain [documentation requirement, e.g., "stable links, diagrams, and template compliance"]
- **FR-005**: The workflow MUST capture [validation behavior, e.g., "review, lint, and approval evidence for changed records"]

*Example of marking unclear requirements:*

- **FR-006**: The document set MUST target [NEEDS CLARIFICATION: primary deliverable not specified - ADR, RFP, or mixed package?]
- **FR-007**: The work item MUST define validation evidence for [NEEDS CLARIFICATION: review standard not specified]

### Key Entities *(include if feature involves data)*

- **[Entity 1]**: [What it represents, key attributes without implementation]
- **[Entity 2]**: [What it represents, relationships to other entities]

## Success Criteria *(mandatory)*

<!--
  ACTION REQUIRED: Define measurable success criteria.
  These must be technology-agnostic and measurable.
-->

### Measurable Outcomes

- **SC-001**: [Measurable metric, e.g., "Reviewers can identify the decision, alternatives, and consequences in under 5 minutes"]
- **SC-002**: [Measurable metric, e.g., "100% of referenced diagrams and links validate successfully in review"]
- **SC-003**: [Quality metric, e.g., "All required sections are present with no unresolved placeholders"]
- **SC-004**: [Portfolio metric, e.g., "A new contributor can trace the rationale for the change without external explanation"]

## Assumptions

<!--
  ACTION REQUIRED: The content in this section represents placeholders.
  Fill them out with the right assumptions based on reasonable defaults
  chosen when the feature description did not specify certain details.
-->

- [Assumption about authors or reviewers, e.g., "Contributors are writing Markdown-based architecture records"]
- [Assumption about scope boundaries, e.g., "Implementation code remains out of scope for this work item"]
- [Assumption about repository context, e.g., "Existing ADR and RFP patterns are the baseline for structure and terminology"]
- [Dependency on existing artifact or process, e.g., "Requires access to current architecture diagrams or decision history"]
