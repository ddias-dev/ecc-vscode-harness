# ECC Harness Adapter for VS Code - Bootstrap

## Agent Bootstrap Guide

Version: 1.0

Status: Active

---

# Purpose

This document is the primary entry point for autonomous agents operating within this repository.

Every agent must begin here.

The goal of this document is to provide a consistent startup procedure and eliminate ambiguity before work begins.

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

without requiring manual prompt construction.

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
Understand the project.
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
users,
requirements,
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
Understand milestone sequence
and delivery priorities.
```

---

## Step 4

Read:

```text
docs/ARCHITECTURE.md
```

Purpose:

```text
Understand system structure
and architectural boundaries.
```

---

## Step 5

Read:

```text
docs/TECHNICAL_DECISIONS.md
```

Purpose:

```text
Understand approved technical standards
and implementation constraints.
```

---

## Step 6

Read:

```text
docs/CONTRACTS.md
```

Purpose:

```text
Understand system interfaces
and domain models.
```

---

## Step 7

Read:

```text
AGENTS.md
```

Purpose:

```text
Understand repository governance
and development workflow.
```

---

## Step 8

Read your role-specific instructions.

### Development Agent

```text
.agents/dev-agent.md
```

### Review Agent

```text
.agents/review-agent.md
```

### Product Agent

```text
.agents/product-agent.md
```

---

# Agent Startup Checklist

Before performing any work, verify:

```text
□ README reviewed
□ PRD reviewed
□ Roadmap reviewed
□ Architecture reviewed
□ Technical decisions reviewed
□ Contracts reviewed
□ AGENTS reviewed
□ Role instructions reviewed
```

Do not proceed until all items are complete.

---

# Product Agent Workflow

## Mission

Generate and maintain executable work.

### Process

```text
Roadmap
    ↓
Milestone
    ↓
Epic
    ↓
Feature
    ↓
Issue
```

### Product Agent Responsibilities

- create milestones
- create epics
- create features
- create issues
- maintain backlog
- maintain acceptance criteria

### Product Agent Deliverables

```text
Executable Issues
Milestone Plans
Backlog Refinement
```

---

# Development Agent Workflow

## Mission

Implement a single issue.

### Process

```text
Select Ready Issue
        ↓
Review Requirements
        ↓
Implement
        ↓
Test
        ↓
Update Documentation
        ↓
Prepare Pull Request
        ↓
Move To Review
```

### Development Agent Responsibilities

- implementation
- testing
- documentation updates

### Development Agent Constraints

- do not modify architecture
- do not modify roadmap
- do not modify requirements
- do not bypass approvals

---

# Review Agent Workflow

## Mission

Protect repository quality.

### Process

```text
Review Pull Request
        ↓
Verify Acceptance Criteria
        ↓
Verify Architecture Compliance
        ↓
Verify Tests
        ↓
Verify Documentation
        ↓
Approve Or Reject
```

### Review Agent Responsibilities

- quality validation
- architecture validation
- testing validation
- documentation validation

---

# GitHub Workflow

## Project States

```text
Backlog
Ready
In Progress
Review
Testing
Done
```

---

## Ready

Issue can be implemented.

Requirements:

```text
Objective defined
Scope defined
Acceptance criteria defined
Dependencies identified
```

---

## In Progress

Issue currently being implemented.

Only one active issue per development agent.

---

## Review

Implementation complete.

Awaiting review.

---

## Testing

Validation in progress.

---

## Done

Merged and accepted.

---

# Milestone Workflow

All work must belong to a milestone.

Current milestone order:

```text
M1 Repository Discovery

M2 Explorer Experience

M3 Context Engine

M4 Prompt Assembly

M5 Copilot Integration

M6 Dynamic Skill Execution

M7 Agent Tool Surface
```

Agents should always prioritise earlier milestones unless directed otherwise.

---

# Development Rules

## Rule 1

Implement the smallest solution that satisfies acceptance criteria.

---

## Rule 2

Prefer existing architecture.

Avoid introducing new abstractions.

---

## Rule 3

Keep changes isolated.

One issue.

One purpose.

---

## Rule 4

Add tests.

Implementation without tests is incomplete.

---

## Rule 5

Update documentation when behaviour changes.

---

# Architecture Rules

Respect the approved architecture.

Allowed flow:

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

# Contracts Rule

Contracts are authoritative.

When implementation conflicts with contracts:

```text
Contracts win.
```

Implementation must be corrected or an ADR proposed.

---

# ADR Rule

If a task requires:

```text
Architecture changes
Interface changes
Breaking changes
New framework introduction
```

Stop.

Create an ADR proposal.

Do not proceed until approved.

---

# Definition Of Done

A task is complete only when:

```text
Implementation complete
Tests passing
Documentation updated
Acceptance criteria satisfied
Review completed
```

---

# If You Become Blocked

Follow this process:

```text
1. Re-read issue.
2. Re-read architecture.
3. Re-read contracts.
4. Re-read technical decisions.
5. Identify blocker.
6. Produce recommendation.
7. Stop.
```

Do not invent requirements.

Do not expand scope.

Do not bypass governance.

---

# Autonomous Execution Directive

Always prefer:

```text
Simple over complex
Clear over clever
Maintainable over optimised
Documented over implicit
Contract-driven over assumption-driven
```

The objective is not maximum code generation.

The objective is predictable, sustainable progress toward the current milestone.

---

# Current Priority

Unless otherwise directed:

```text
Current Focus:
M1 - Repository Discovery
```

Agents should prioritise work that advances:

```text
Skill Discovery
Rule Discovery
Command Discovery
Asset Registry
```

before moving to later milestones.
