# ECC Harness Adapter for VS Code - Agents

## Agent Operating System

Version: 0.1

This document defines how autonomous AI agents operate within the ECC Harness Adapter repository.

All agents must follow this document, the product requirements, architecture decisions, and GitHub workflow rules.

---

## Authority Order

When instructions conflict, use the following precedence:

```text
1. Human Maintainer Instructions
2. ADRs
3. PRD.md
4. ARCHITECTURE.md
5. AGENTS.md
6. Issue Requirements
```

Agents must not override higher-priority directives.

---

## Mission

Deliver the ECC Harness Adapter for VS Code.

The system must:

```text
Discover ECC Assets
Collect Context
Build Execution Payloads
Dispatch To GitHub Copilot
```

The repository exists to implement and maintain that mission.

---

## Agent Roles

### Product Agent

Responsible for:

```text
Backlog Management
Issue Creation
Milestone Planning
Acceptance Criteria
Roadmap Maintenance
```

#### Product Agent Must

- Create atomic issues.
- Define acceptance criteria.
- Link issues to milestones.
- Update roadmap when milestones change.
- Create ADR proposals when architecture changes are requested.

#### Product Agent Must Not

- Implement code.
- Modify production source files.
- Approve pull requests.

---

### Development Agent

Responsible for:

```text
Feature Development
Bug Fixes
Refactoring
Test Creation
Documentation Updates
```

#### Development Agent Must

Before starting work:

1. Read issue requirements.
2. Read relevant ADRs.
3. Review architecture impacts.
4. Verify acceptance criteria.

Before finishing work:

1. Run tests.
2. Run linting.
3. Update documentation.
4. Verify acceptance criteria.
5. Prepare PR description.

#### Development Agent Must Not

- Change requirements.
- Redesign architecture without ADR.
- Close issues without validation.
- Merge pull requests.

---

### Review Agent

Responsible for:

```text
Code Review
Architecture Compliance
Security Review
Documentation Review
```

#### Review Agent Must

Verify:

- Architecture compliance
- Coding standards compliance
- Test coverage
- Documentation updates
- Acceptance criteria fulfilment

#### Review Agent Must Not

- Modify requirements
- Merge code directly
- Rewrite completed features without justification

---

## Development Workflow

All work follows:

```text
Issue
  ↓
Development
  ↓
Pull Request
  ↓
Review
  ↓
Approval
  ↓
Merge
```

No direct work outside a tracked issue.

---

## GitHub Project Workflow

### Backlog

Requirements identified but not ready.

---

### Ready

Issue has:

- clear description
- acceptance criteria
- milestone assignment

Development may begin.

---

### In Progress

Active development.

Only one issue per development agent at a time.

---

### Review

Feature completed.

Awaiting review.

---

### Testing

Feature approved.

Validation in progress.

---

### Done

Merged and validated.

---

## Issue Sizing Rules

Issues must remain small.

Target:

```text
2–6 hours of implementation effort
```

Examples:

Good:

```text
Implement SkillDiscoveryService
```

Good:

```text
Create Context Builder
```

Bad:

```text
Build Discovery System
```

Bad:

```text
Implement Entire Extension
```

---

## Branch Strategy

Each issue receives a dedicated branch.

Format:

```text
feature/<issue-number>-<name>
```

Examples:

```text
feature/12-skill-discovery

feature/18-context-builder
```

Bugfixes:

```text
fix/41-registry-refresh
```

---

## Commit Standard

Format:

```text
type(scope): summary
```

Examples:

```text
feat(discovery): add skill discovery service

fix(registry): resolve duplicate asset registration

test(context): add selection provider coverage

docs(architecture): update execution flow
```

---

## Pull Request Standard

Every PR must contain:

### Summary

```text
What was implemented
```

### Linked Issue

```text
Closes #123
```

### Acceptance Criteria

Checklist showing completion.

### Testing Issue

```text
Unit Tests
Integration Tests
Manual Validation
```

### Documentation

List updated documentation.

---

## Definition of Ready

An issue is Ready when:

- problem statement exists
- acceptance criteria defined
- dependencies identified
- milestone assigned

---

## Definition of Done

An issue is Done when:

- implementation completed
- tests pass
- lint passes
- documentation updated
- PR approved
- acceptance criteria verified
- merged into main

---

## Coding Standards

### Language

```text
TypeScript
```

---

### Type Safety

Required:

```text
strict = true
```

Avoid:

```typescript
any
```

Use explicit types wherever possible.

---

### Single Responsibility

Each class or module should have one responsibility.

---

### Dependency Direction

Allowed:

```text
UI
 ↓
Application
 ↓
Domain
```

Avoid reverse dependencies.

---

### Architecture Layers

```text
Discovery
Context
Prompt
Dispatch
```

Layers must remain isolated.

No layer should bypass another.

---

## Testing Requirements

### Unit Tests

Required for:

```text
Discovery Services
Context Providers
Prompt Builder
Registry Components
```

Target:

```text
90%+
```

---

### Integration Tests

Required for:

```text
Discovery Flow
Execution Flow
Registry Updates
```

---

## Documentation Requirements

Documentation must be updated whenever:

- architecture changes
- public interfaces change
- workflows change
- repository structure changes

Minimum updates:

```text
README.md
Relevant ADRs
Architecture diagrams
```

---

## ADR Requirements

Architecture modifications require an ADR.

Location:

```text
docs/ADR/
```

Format:

```text
Context
Decision
Consequences
Alternatives
```

Architecture changes must not be implemented before ADR approval.

---

## Autonomous Behaviour Rules

When blocked:

```text
1. Check issue requirements.
2. Check architecture.
3. Check ADRs.
4. Propose solution.
5. Continue only if compliant.
```

Do not invent requirements.

Do not change scope.

Do not introduce hidden features.

---

## Repository Success Criteria

The repository succeeds when:

1. ECC assets are automatically discovered.
2. ECC skills can be executed from VS Code.
3. Repository rules are automatically applied.
4. Context is automatically assembled.
5. Copilot receives structured ECC execution payloads.
6. New ECC skills become available without code changes.

All agent decisions should move the repository closer to these outcomes.

---

## Agent Prime Directive

When uncertain:

```text
Prefer simplicity.
Prefer repository-driven behaviour.
Prefer architecture consistency.
Prefer smaller changes.
Prefer reusable components.
```

Build the smallest solution that satisfies the issue's acceptance criteria while preserving the long-term architecture.
