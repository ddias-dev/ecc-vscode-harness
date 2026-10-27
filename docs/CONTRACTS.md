# ECC Harness Adapter for VS Code - Contracts

## Domain Contracts

Version: 1.0

Status: Approved

---

# Purpose

This document defines the canonical domain contracts used throughout the ECC Harness Adapter.

These contracts represent the shared language of the system.

All implementations MUST conform to these contracts unless superseded by an approved ADR.

The contracts defined here are the source of truth for:

- Discovery Layer
- Registry Layer
- Context Layer
- Prompt Layer
- Dispatch Layer

---

# Design Principles

## Contract First

All implementation work must begin with a defined contract.

Agents must not invent new structures during implementation.

---

## Stable Interfaces

Contracts should remain stable across milestones whenever possible.

Breaking changes require an ADR.

---

## Layer Independence

Contracts define communication between layers.

Layers may not access internal implementation details of other layers.

---

# Asset Model

ECC assets discovered within a repository are represented through a common asset hierarchy.

---

# Skill

Represents a reusable ECC workflow.

```typescript
export interface Skill {
  id: string;
  name: string;
  description: string;
  instructions: string;
  sourcePath: string;
}
```

## Field Definitions

| Field | Description |
|---------|---------|
| id | Unique identifier |
| name | Human-readable name |
| description | Short skill summary |
| instructions | Skill content |
| sourcePath | Repository path |

## Example

```json
{
  "id": "security-review",
  "name": "Security Review",
  "description": "Review selected code for security issues.",
  "instructions": "Analyse code for vulnerabilities.",
  "sourcePath": ".ecc/skills/security-review.md"
}
```

---

# Rule

Represents repository guidance or constraints.

```typescript
export interface Rule {
  id: string;
  title: string;
  content: string;
  sourcePath: string;
}
```

## Field Definitions

| Field | Description |
|---------|---------|
| id | Unique identifier |
| title | Rule title |
| content | Rule content |
| sourcePath | Repository path |

---

# Command

Represents an ECC command exposed to the harness.

```typescript
export interface Command {
  id: string;
  name: string;
  description: string;
  sourcePath: string;
}
```

## Field Definitions

| Field | Description |
|---------|---------|
| id | Unique identifier |
| name | Command name |
| description | Command summary |
| sourcePath | Repository path |

---

# Asset Registry

Central catalogue of discovered ECC assets.

```typescript
export interface AssetRegistry {
  skills: Skill[];
  rules: Rule[];
  commands: Command[];
}
```

## Purpose

Provides a single source of truth for all discovered assets.

The registry should be populated only by discovery services.

---

# Discovery Contracts

---

# Skill Discovery Result

```typescript
export interface SkillDiscoveryResult {
  skills: Skill[];
  scannedPaths: string[];
  warnings: string[];
}
```

---

# Rule Discovery Result

```typescript
export interface RuleDiscoveryResult {
  rules: Rule[];
  scannedPaths: string[];
  warnings: string[];
}
```

---

# Command Discovery Result

```typescript
export interface CommandDiscoveryResult {
  commands: Command[];
  scannedPaths: string[];
  warnings: string[];
}
```

---

# Context Contracts

Execution context represents information captured at runtime.

---

# Execution Context

```typescript
export interface ExecutionContext {
  workspaceName: string;
  gitBranch?: string;
  filePath?: string;
  language?: string;
  selectedText?: string;
}
```

## Field Definitions

| Field | Description |
|---------|---------|
| workspaceName | Active workspace |
| gitBranch | Current Git branch |
| filePath | Current file |
| language | File language |
| selectedText | Selected editor content |

---

# Editor Context

```typescript
export interface EditorContext {
  filePath?: string;
  language?: string;
  selectedText?: string;
}
```

---

# Git Context

```typescript
export interface GitContext {
  branch?: string;
}
```

---

# Workspace Context

```typescript
export interface WorkspaceContext {
  workspaceName: string;
}
```

---

# Prompt Contracts

Prompt contracts define the payload passed into the dispatch layer.

---

# Prompt Payload

```typescript
export interface PromptPayload {
  skill: Skill;
  rules: Rule[];
  context: ExecutionContext;
  userRequest?: string;
}
```

---

# Generated Prompt

```typescript
export interface GeneratedPrompt {
  content: string;
}
```

## Example Structure

```text
ECC Skill
Repository Rules
Execution Context
User Request
```

---

# Dispatch Contracts

Dispatch contracts define communication with execution surfaces.

---

# Dispatch Request

```typescript
export interface DispatchRequest {
  prompt: GeneratedPrompt;
}
```

---

# Dispatch Result

```typescript
export interface DispatchResult {
  success: boolean;
  message?: string;
}
```

---

# Service Contracts

---

# Skill Discovery Service

```typescript
export interface SkillDiscoveryService {
  discover(): Promise<SkillDiscoveryResult>;
}
```

---

# Rule Discovery Service

```typescript
export interface RuleDiscoveryService {
  discover(): Promise<RuleDiscoveryResult>;
}
```

---

# Command Discovery Service

```typescript
export interface CommandDiscoveryService {
  discover(): Promise<CommandDiscoveryResult>;
}
```

---

# Context Builder

```typescript
export interface ExecutionContextBuilder {
  build(): Promise<ExecutionContext>;
}
```

---

# Prompt Builder

```typescript
export interface PromptBuilder {
  build(
    payload: PromptPayload
  ): Promise<GeneratedPrompt>;
}
```

---

# Dispatcher

```typescript
export interface Dispatcher {
  dispatch(
    request: DispatchRequest
  ): Promise<DispatchResult>;
}
```

---

# Registry Contract

```typescript
export interface Registry {
  getSkills(): Skill[];

  getRules(): Rule[];

  getCommands(): Command[];

  refresh(): Promise<void>;
}
```

---

# Error Contracts

Standard error structure for business-layer operations.

```typescript
export interface DomainError {
  code: string;
  message: string;
}
```

## Example

```typescript
{
  code: "SKILL_NOT_FOUND",
  message: "Requested skill does not exist."
}
```

---

# Versioning

Contract changes are classified as:

## Non-Breaking

Examples:

- Optional fields
- Documentation updates

Allowed through normal pull requests.

---

## Breaking

Examples:

- Required field changes
- Interface signature changes
- Removed properties

Require:

```text
ADR
Review
Approval
```

before implementation.

---

# Compliance

All agents and contributors must adhere to these contracts.

When implementation and contracts disagree:

```text
Contracts win.
```

Implementation must be updated or an ADR must be proposed.

These contracts are the authoritative domain model for the ECC Harness Adapter.
