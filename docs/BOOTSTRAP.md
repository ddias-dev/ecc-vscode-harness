# ECC Harness Adapter for VS Code - Bootstrap

## Agent Bootstrap Guide

Version: 1.0

Status: Active

---

# Purpose

This document is the mandatory starting point for all autonomous agents operating in this repository.

Every agent must begin here before performing any planning, implementation, review, or backlog management activities.

The purpose of this document is to:

- establish a consistent startup sequence
- define work selection rules
- enforce roadmap alignment
- eliminate ambiguity
- support autonomous Agentic-Agile execution

---

# Project Mission

Build a native VS Code execution surface for ECC.

The system shall:

```text
Discover ECC Assets
        ↓
Build Execution Context
        ↓
Assemble ECC Payloads
        ↓
Dispatch To GitHub Copilot
```

without requiring manual prompt construction by developers.

---

# Repository Reading Order

All agents must read repository documents in the following order.

## Step 1

Read:

```text
README.md
```

Purpose:

```text
Understand project purpose
and user value.
```

---

## Step 2

Read:

```text
docs/PRD.md
```

Purpose:

```text
Understand product goals,
user stories,
functional requirements,
and acceptance criteria.
```

---

## Step 3

Read:

```text
docs/ROADMAP.md
```

Purpose:

```text
Understand milestone sequence,
delivery order,
and roadmap priorities.
```

---

## Step 4

Read:

```text
docs/ARCHITECTURE.md
```

Purpose:

```text
Understand system structure,
architectural boundaries,
allowed dependencies,
and execution flows.
```

---

## Step 5

Read:

```text
docs/TECHNICAL_DECISIONS.md
```

Purpose:

```text
Understand approved technologies,
patterns,
implementation constraints,
and development standards.
```

---

## Step 6

Read:

```text
docs/CONTRACTS.md
```

Purpose:

```text
Understand canonical interfaces,
domain models,
and cross-layer contracts.
```

---

## Step 7

Read:

```text
AGENTS.md
```

Purpose:

```text
Understand governance,
workflow,
responsibilities,
and repository rules.
```

---

## Step 8

Read role-specific instructions.

### Development Agent

```text
.agents/dev-agent.md
```

### Product Agent

```text
.agents/product-agent.md
```

### Review Agent

```text
.agents/review-agent.md
```

---

# Mandatory Startup Checklist

Before taking any action, verify:

```text
□ README reviewed
□ PRD reviewed
□ ROADMAP reviewed
□ ARCHITECTURE reviewed
□ TECHNICAL_DECISIONS reviewed
□ CONTRACTS reviewed
□ AGENTS reviewed
□ Role instructions reviewed
```

Do not proceed until all items are complete.

---

# Agent Responsibilities

## Product Agent

Responsible for:

```text
Roadmap execution
Epic management
Feature management
Issue generation
Backlog refinement
Milestone planning
```

Produces:

```text
Epics
Features
Issues
Acceptance Criteria
```

---

## Development Agent

Responsible for:

```text
Implementation
Testing
Documentation updates
Pull Request preparation
```

Produces:

```text
Source Code
Tests
Documentation Updates
```

---

## Review Agent

Responsible for:

```text
Code quality
Architecture compliance
Testing validation
Documentation validation
```

Produces:

```text
PASS
or
CHANGES REQUIRED
```

---

# GitHub Workflow

Project workflow:

```text
Backlog
    ↓
Ready
    ↓
In Progress
    ↓
Review
    ↓
Testing
    ↓
Done
```

---

## Backlog

Ideas and future work.

Not implementation-ready.

---

## Ready

May be worked on immediately.

Requirements:

```text
Objective defined
Scope defined
Acceptance criteria defined
Milestone assigned
Dependencies identified
```

---

## In Progress

Active implementation.

One issue at a time.

---

## Review

Implementation complete.

Awaiting Review Agent validation.

---

## Testing

Validation in progress.

---

## Done

Merged and accepted.

---

# Work Prioritisation Policy

All work selection must follow the roadmap hierarchy.

```text
Milestone
    ↓
Epic
    ↓
Feature
    ↓
Issue
```

---

## Rule 1: Earliest Milestone First

Always work on the earliest milestone that contains Ready issues.

Example:

```text
M1 Repository Discovery
    before
M2 Explorer Experience
    before
M3 Context Engine
```

Agents must not begin a later milestone while Ready work exists in an earlier milestone unless explicitly instructed by a human maintainer.

---

## Rule 2: Highest Priority Epic

Within a milestone:

```text
priority-high
    before
priority-medium
    before
priority-low
```

---

## Rule 3: Highest Priority Feature

Within an Epic:

Select the highest-priority incomplete Feature.

---

## Rule 4: Ready Issues Only

Development Agents may only select Issues that:

```text
Have Ready status
Are not blocked
Belong to the active milestone
```

---

## Rule 5: Single Issue Execution

Development Agents must:

```text
Select one issue
Implement one issue
Create one pull request
Move issue to Review
Stop
```

Do not implement multiple issues simultaneously.

---

## Rule 6: Milestone Completion

A milestone is complete only when:

```text
All issues closed
All reviews complete
All acceptance criteria satisfied
```

Only then may work begin on the next milestone.

---

# Current Roadmap Priority

Unless otherwise directed:

```text
M1 Repository Discovery
M2 Explorer Experience
M3 Context Engine
M4 Prompt Assembly
M5 Copilot Integration
M6 Dynamic Skill Execution
M7 Agent Tool Surface
```

---

# Current Active Milestone

```text
M1 - Repository Discovery
```

Current implementation focus:

```text
FEATURE-001 Skill Discovery
FEATURE-002 Rule Discovery
FEATURE-003 Command Discovery
FEATURE-004 Asset Registry
```

---

# Development Rules

## Rule 1

Implement the smallest solution that satisfies the acceptance criteria.

---

## Rule 2

Prefer existing architecture.

Do not introduce new abstractions unless necessary.

---

## Rule 3

Respect established contracts.

Do not invent alternative domain models.

---

## Rule 4

Every change must be tested.

Implementation without tests is incomplete.

---

## Rule 5

Documentation must remain accurate.

Update documentation whenever behaviour changes.

---

# Architecture Rules

Respect approved architecture.

Allowed dependency flow:

```text
UI
 ↓
Application
 ↓
Domain
 ↓
Infrastructure
```

Do not introduce reverse dependencies.

---

# Contract Rules

Contracts are authoritative.

When implementation and contracts disagree:

```text
Contracts win.
```

Required action:

```text
Update implementation
or
Propose ADR
```

---

# ADR Escalation Rules

Stop implementation immediately if a task requires:

```text
Architecture changes
Contract changes
Breaking interface changes
New framework adoption
New execution model
```

Required process:

```text
Create ADR
Review ADR
Approve ADR
Resume Work
```

---

# Definition Of Done

An issue is complete only when:

```text
Implementation complete
Tests added
Tests passing
Documentation updated
Acceptance criteria satisfied
Pull request prepared
Review completed
```

---

# Blocker Protocol

If blocked:

```text
1. Re-read issue
2. Re-read architecture
3. Re-read contracts
4. Re-read technical decisions
5. Identify blocker
6. Document recommendation
7. Stop
```

Do not:

```text
Invent requirements
Expand scope
Change architecture
Create undocumented behaviour
```

---

# Autonomous Execution Directive

Prefer:

```text
Simple over complex
Explicit over implicit
Maintainable over clever
Documented over assumed
Contract-driven over implementation-driven
```

Repository success is measured by predictable execution and roadmap progress, not by volume of generated code.

---

# First Action After Bootstrap

After completing startup:

## Product Agent

```text
Select earliest milestone
Refine backlog
Create executable issues
```

---

## Development Agent

```text
Select highest-priority Ready issue
Implement
Test
Create pull request
Move issue to Review
```

---

## Review Agent

```text
Review pull request
Validate acceptance criteria
Validate architecture
Approve or reject
```

---

# Repository North Star

The project succeeds when a developer can:

```text
Open an ECC-enabled repository
        ↓
Install the ECC Harness Adapter
        ↓
Execute an ECC Skill
        ↓
Automatically apply repository rules
        ↓
Use GitHub Copilot with enriched ECC context
```

without manually loading skills, rules, commands, or execution context.
