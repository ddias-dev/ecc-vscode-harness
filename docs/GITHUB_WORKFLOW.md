# GITHUB_WORKFLOW.md

# ECC Harness Adapter for VS Code
## GitHub Workflow Standard

Version: 1.0

Status: Active

---

# Purpose

This document defines how work is managed within GitHub.

GitHub is the single source of truth for:

- milestones
- epics
- features
- issues
- pull requests
- delivery status

All agents must interact with GitHub according to this workflow.

---

# Guiding Principle

The roadmap drives all work.

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
    ↓
Pull Request
    ↓
Review
    ↓
Merge
```

Work must never skip levels.

---

# Repository Structure

Repository:

```text
ddias-dev/ecc-vscode-harness
```

GitHub is the authoritative system for:

```text
Task Management
Status Tracking
Work Prioritisation
Delivery Progress
```

---

# Delivery Hierarchy

## Milestone

Represents a release objective.

Examples:

```text
M1 - Repository Discovery

M2 - Explorer Experience

M3 - Context Engine

M4 - Prompt Assembly

M5 - Copilot Integration

M6 - Dynamic Skill Execution

M7 - Agent Tool Surface
```

Milestones define:

```text
Why work is being done.
```

---

## Epic

Groups related Features.

Example:

```text
EPIC-001 Repository Discovery
```

Epics define:

```text
What capability is being delivered.
```

---

## Feature

Groups implementation Issues.

Examples:

```text
FEATURE-001 Skill Discovery

FEATURE-002 Rule Discovery

FEATURE-003 Command Discovery

FEATURE-004 Asset Registry
```

Features define:

```text
What outcome must exist.
```

---

## Issue

Executable unit of work.

Examples:

```text
ISSUE-001 Create Skill Contract

ISSUE-005 Implement Skill Discovery Service

ISSUE-010 Create Asset Registry Tests
```

Issues define:

```text
What developers implement.
```

---

# Work Selection Rules

All agents must follow:

```text
Milestone
    ↓
Epic
    ↓
Feature
    ↓
Issue
```

Selection order:

```text
Early Milestone First

High Priority First

Ready Issues First
```

---

# Current Milestone Order

Work must be completed in this order:

```text
M1 Repository Discovery

M2 Explorer Experience

M3 Context Engine

M4 Prompt Assembly

M5 Copilot Integration

M6 Dynamic Skill Execution

M7 Agent Tool Surface
```

Later milestones must not be started while executable work remains in an earlier milestone.

---

# Project Workflow

All work items exist in one of the following states:

```text
Backlog
Ready
In Progress
Review
Testing
Done
```

---

## Backlog

Work is identified but not ready.

Characteristics:

```text
Incomplete
Needs planning
Needs refinement
```

---

## Ready

Work may be implemented.

Requirements:

```text
Objective defined
Scope defined
Acceptance criteria defined
Dependencies identified
Milestone assigned
```

---

## In Progress

Currently being implemented.

Only one active issue per Development Agent.

---

## Review

Implementation completed.

Awaiting Review Agent validation.

---

## Testing

Validation in progress.

Awaiting successful verification.

---

## Done

Complete.

Merged and accepted.

---

# GitHub Labels

Labels communicate work type.

---

## Planning Labels

```text
epic
feature
story
```

---

## Quality Labels

```text
architecture
documentation
testing
bug
```

---

## Status Labels

```text
ready
blocked
```

---

## Priority Labels

```text
priority-high
priority-medium
priority-low
```

---

## Milestone Labels

```text
m1
m2
m3
m4
m5
m6
m7
```

---

## Automation Labels

```text
agent-generated
```

---

# Product Agent Responsibilities

The Product Agent owns planning.

Responsibilities:

```text
Create Milestones

Create Epics

Create Features

Create Issues

Maintain Backlog

Refine Acceptance Criteria
```

---

## Product Agent Workflow

```text
Read Milestones
    ↓
Identify Next Work
    ↓
Create Feature
    ↓
Create Issues
    ↓
Assign Labels
    ↓
Move To Ready
```

---

# Development Agent Responsibilities

The Development Agent owns implementation.

Responsibilities:

```text
Select Ready Issue

Implement

Test

Document

Create Pull Request
```

---

## Development Agent Workflow

```text
Find Earliest Active Milestone
    ↓
Find Highest Priority Ready Issue
    ↓
Move To In Progress
    ↓
Implement
    ↓
Create Pull Request
    ↓
Move Issue To Review
```

---

# Review Agent Responsibilities

The Review Agent owns validation.

Responsibilities:

```text
Review Pull Request

Validate Requirements

Validate Architecture

Validate Tests

Validate Documentation
```

---

## Review Agent Workflow

```text
Review Pull Request
    ↓
Validate Acceptance Criteria
    ↓
PASS
or
CHANGES REQUIRED
```

---

# Pull Request Requirements

Each Pull Request must include:

## Summary

What was implemented.

---

## Linked Issue

Example:

```text
Closes #15
```

---

## Acceptance Criteria Status

Each criterion:

```text
PASS
or
FAIL
```

---

## Testing Performed

Examples:

```text
Unit Tests

Integration Tests

Manual Validation
```

---

## Documentation Updates

List all updated documents.

---

# GitHub CLI Standard

Preferred repository automation tool:

```bash
gh
```

Agents should use GitHub CLI whenever possible.

---

# Common Commands

## List Milestones

```bash
gh api repos/ddias-dev/ecc-vscode-harness/milestones
```

---

## List Issues

```bash
gh issue list
```

---

## Create Issue

```bash
gh issue create
```

---

## View Issue

```bash
gh issue view <issue-number>
```

---

## Edit Issue

```bash
gh issue edit <issue-number>
```

---

## Create Pull Request

```bash
gh pr create
```

---

## List Pull Requests

```bash
gh pr list
```

---

## View Pull Request

```bash
gh pr view <pr-number>
```

---

# Definition Of Ready

An Issue is Ready when:

```text
Objective defined

Scope defined

Acceptance criteria defined

Testing requirements defined

Dependencies identified

Milestone assigned
```

---

# Definition Of Done

An Issue is Done when:

```text
Implementation complete

Tests passing

Documentation updated

Review completed

Pull Request merged
```

---

# Blocker Management

Blocked work must:

```text
Receive blocked label

Document blocker

Identify dependency

Stop execution
```

Do not work around blockers by inventing requirements.

---

# Agent Escalation Rules

Stop and request guidance when:

```text
Architecture changes required

Contract changes required

New framework required

Roadmap conflict detected

Requirements unclear
```

Do not bypass governance.

---

# Repository Success Criteria

The workflow succeeds when:

```text
All work is traceable to a milestone

All features are traceable to epics

All issues are traceable to features

All pull requests are traceable to issues

Agents can operate autonomously using GitHub as the source of truth
```

GitHub is not documentation.

GitHub is the operational system used to execute the roadmap.
