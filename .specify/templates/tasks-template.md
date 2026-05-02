---

description: "Task list template for feature implementation"
---

# Tasks: [FEATURE NAME]

**Input**: Design documents from `/specs/[###-feature-name]/`
**Prerequisites**: plan.md (required), spec.md (required for user stories), research.md, data-model.md, contracts/

**Tests**: The examples below include validation tasks. Validation is OPTIONAL - only include it when explicitly requested in the feature specification or required by the constitution.

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

## Path Conventions

- **ADR repository**: `adr/`, `reviews/`, `diagrams/`, `templates/`
- **RFP repository**: `rfp/`, `reviews/`, `diagrams/`, `templates/`
- **Shared docs repository**: `docs/`, `templates/`, `glossary/`
- Paths shown below assume a documentation repository - adjust based on plan.md structure

<!-- 
  ============================================================================
  IMPORTANT: The tasks below are SAMPLE TASKS for illustration purposes only.
  
  The /speckit.tasks command MUST replace these with actual tasks based on:
  - User stories from spec.md (with their priorities P1, P2, P3...)
  - Feature requirements from plan.md
  - Entities from data-model.md
  - Endpoints from contracts/
  
  Tasks MUST be organized by user story so each story can be:
  - Implemented independently
  - Tested independently
  - Delivered as an MVP increment
  
  DO NOT keep these sample tasks in the generated tasks.md file.
  ============================================================================
-->

## Phase 1: Setup (Shared Documentation Infrastructure)

**Purpose**: Repository structure, templates, and validation setup

- [ ] T001 Create document structure per implementation plan
- [ ] T002 Initialize architecture templates and reference files
- [ ] T003 [P] Configure linting, link checking, and diagram validation tools

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure that MUST be complete before ANY user story can be implemented

**⚠️ CRITICAL**: No user story work can begin until this phase is complete

Examples of foundational tasks (adjust based on your project):

- [ ] T004 Establish document taxonomy, naming, and status conventions
- [ ] T005 [P] Define review workflow and approval checklist
- [ ] T006 [P] Create shared glossary, cross-reference rules, and diagram conventions
- [ ] T007 Create base templates and reusable sections that all stories depend on
- [ ] T008 Configure validation workflow for markdown, links, and diagrams
- [ ] T009 Capture repository constraints, assumptions, and contribution guidance

**Checkpoint**: Foundation ready - user story implementation can now begin in parallel

---

## Phase 3: User Story 1 - [Title] (Priority: P1) 🎯 MVP

**Goal**: [Brief description of what this story delivers]

**Independent Test**: [How to verify this story works on its own]

### Validation for User Story 1 (OPTIONAL - only if validation requested) ⚠️

> **NOTE: Define these checks FIRST and ensure they fail before drafting the final artifact**

- [ ] T010 [P] [US1] Add validation criteria for [artifact] in reviews/[artifact]/[name].md
- [ ] T011 [P] [US1] Add review scenario for [user journey] in reviews/[artifact]/[name].md

### Implementation for User Story 1

- [ ] T012 [P] [US1] Draft [artifact 1] in [path/to/artifact].md
- [ ] T013 [P] [US1] Draft supporting diagram or appendix in [path/to/diagram-or-appendix]
- [ ] T014 [US1] Add rationale, alternatives, and consequences in [path/to/artifact].md (depends on T012, T013)
- [ ] T015 [US1] Add cross-references and traceability links in [path/to/artifact].md
- [ ] T016 [US1] Run validation and resolve findings for [path/to/artifact].md
- [ ] T017 [US1] Record review evidence and status update in reviews/[artifact]/[name].md

**Checkpoint**: At this point, User Story 1 should be fully functional and testable independently

---

## Phase 4: User Story 2 - [Title] (Priority: P2)

**Goal**: [Brief description of what this story delivers]

**Independent Test**: [How to verify this story works on its own]

### Validation for User Story 2 (OPTIONAL - only if validation requested) ⚠️

- [ ] T018 [P] [US2] Add validation criteria for [artifact] in reviews/[artifact]/[name].md
- [ ] T019 [P] [US2] Add review scenario for [user journey] in reviews/[artifact]/[name].md

### Implementation for User Story 2

- [ ] T020 [P] [US2] Draft [artifact] in [path/to/artifact].md
- [ ] T021 [US2] Add supporting analysis or comparison matrix in [path/to/supporting-doc].md
- [ ] T022 [US2] Link User Story 2 artifacts to shared glossary, diagrams, and prior decisions
- [ ] T023 [US2] Reconcile terminology and dependencies with User Story 1 artifacts (if needed)

**Checkpoint**: At this point, User Stories 1 AND 2 should both work independently

---

## Phase 5: User Story 3 - [Title] (Priority: P3)

**Goal**: [Brief description of what this story delivers]

**Independent Test**: [How to verify this story works on its own]

### Validation for User Story 3 (OPTIONAL - only if validation requested) ⚠️

- [ ] T024 [P] [US3] Add validation criteria for [artifact] in reviews/[artifact]/[name].md
- [ ] T025 [P] [US3] Add review scenario for [user journey] in reviews/[artifact]/[name].md

### Implementation for User Story 3

- [ ] T026 [P] [US3] Draft [artifact] in [path/to/artifact].md
- [ ] T027 [US3] Add final rationale, risks, and acceptance evidence in [path/to/artifact].md
- [ ] T028 [US3] Publish review-ready package with links to all dependent artifacts

**Checkpoint**: All user stories should now be independently functional

---

[Add more user story phases as needed, following the same pattern]

---

## Phase N: Polish & Cross-Cutting Concerns

**Purpose**: Improvements that affect multiple user stories

- [ ] TXXX [P] Documentation updates in docs/ or reviews/
- [ ] TXXX Cross-record cleanup and terminology normalization
- [ ] TXXX Performance and scalability expectations review across all stories
- [ ] TXXX [P] Additional validation checks (if requested) in reviews/
- [ ] TXXX Cloud-agnostic and open-source compliance review
- [ ] TXXX Run quickstart.md validation

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies - can start immediately
- **Foundational (Phase 2)**: Depends on Setup completion - BLOCKS all user stories
- **User Stories (Phase 3+)**: All depend on Foundational phase completion
  - User stories can then proceed in parallel (if staffed)
  - Or sequentially in priority order (P1 → P2 → P3)
- **Polish (Final Phase)**: Depends on all desired user stories being complete

### User Story Dependencies

- **User Story 1 (P1)**: Can start after Foundational (Phase 2) - No dependencies on other stories
- **User Story 2 (P2)**: Can start after Foundational (Phase 2) - May integrate with US1 but should be independently testable
- **User Story 3 (P3)**: Can start after Foundational (Phase 2) - May integrate with US1/US2 but should be independently testable

### Within Each User Story

- Validation criteria (if included) MUST be written and FAIL before final authoring
- Core artifact draft before supporting references
- Supporting references before final review evidence
- Core authoring before cross-document integration
- Story complete before moving to next priority

### Parallel Opportunities

- All Setup tasks marked [P] can run in parallel
- All Foundational tasks marked [P] can run in parallel (within Phase 2)
- Once Foundational phase completes, all user stories can start in parallel (if team capacity allows)
- All validation tasks for a user story marked [P] can run in parallel
- Draft artifacts within a story marked [P] can run in parallel
- Different user stories can be worked on in parallel by different team members

---

## Parallel Example: User Story 1

```bash
# Launch all validation tasks for User Story 1 together (if validation requested):
Task: "Add validation criteria for [artifact] in reviews/[artifact]/[name].md"
Task: "Add review scenario for [user journey] in reviews/[artifact]/[name].md"

# Launch all document drafts for User Story 1 together:
Task: "Draft [artifact 1] in [path/to/artifact].md"
Task: "Draft supporting diagram or appendix in [path/to/diagram-or-appendix]"
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup
2. Complete Phase 2: Foundational (CRITICAL - blocks all stories)
3. Complete Phase 3: User Story 1
4. **STOP and VALIDATE**: Review User Story 1 artifacts independently
5. Publish or circulate for approval if ready

### Incremental Delivery

1. Complete Setup + Foundational → Foundation ready
2. Add User Story 1 → Review independently → Publish/Demo (MVP!)
3. Add User Story 2 → Review independently → Publish/Demo
4. Add User Story 3 → Review independently → Publish/Demo
5. Each story adds value without breaking previous stories

### Parallel Team Strategy

With multiple developers:

1. Team completes Setup + Foundational together
2. Once Foundational is done:
   - Developer A: User Story 1
   - Developer B: User Story 2
   - Developer C: User Story 3
3. Stories complete and integrate independently

---

## Notes

- [P] tasks = different files, no dependencies
- [Story] label maps task to specific user story for traceability
- Each user story should be independently completable and reviewable
- Verify validation checks fail before finalizing artifacts
- Commit after each task or logical group
- Stop at any checkpoint to validate story independently
- Avoid: vague tasks, same file conflicts, cross-story dependencies that break independence
