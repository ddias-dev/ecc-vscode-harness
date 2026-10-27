# ECC Harness Adapter for VS Code - Roadmap

## Product Roadmap

Version: 0.1  
Status: Active

---

## Purpose

This roadmap defines the planned evolution of the ECC Harness Adapter for VS Code.

The roadmap is organised into milestone-driven deliveries designed for autonomous execution through the repository's Agentic Agile workflow.

Each milestone represents a releasable increment.

---

## Product Vision

Provide a native VS Code execution surface for ECC.

Developers should be able to:

```text
Open Repository
      ↓
Discover ECC Assets
      ↓
Execute ECC Skills
      ↓
Automatically Apply Rules
      ↓
Use GitHub Copilot
```

without manually constructing prompts or navigating ECC internals.

---

## Strategic Outcomes

### Outcome 1

ECC assets become discoverable within VS Code.

---

### Outcome 2

ECC skills become executable through a native editor experience.

---

### Outcome 3

Repository context becomes automatically available to Copilot.

---

### Outcome 4

ECC becomes a first-class workflow layer within VS Code.

---

## Milestone Overview

| Milestone | Name | Target Outcome |
| ------------ | -------- | ---------------- |
| M1 | Repository Discovery | Detect ECC assets |
| M2 | Explorer Experience | Visualise ECC assets |
| M3 | Context Engine | Build execution context |
| M4 | Prompt Assembly | Generate ECC payloads |
| M5 | Copilot Integration | Execute ECC skills |
| M6 | Dynamic Skill Execution | Support repository-defined skills |
| M7 | Agent Tool Surface | Expose ECC as a Copilot capability |

---

## M1 - Repository Discovery

### M1 - Objective

Discover ECC assets automatically.

---

## M1 - Features

### Skill Discovery

Discover:

```text
skills/
.ecc/skills/
```

---

### Rule Discovery

Discover:

```text
rules/
.ecc/rules/
```

---

### Command Discovery

Discover:

```text
commands/
.ecc/commands/
```

---

## M1 - Deliverables

### Asset Registry

```typescript
AssetRegistry
```

Central repository of discovered ECC assets.

---

### Discovery Services

```typescript
SkillDiscoveryService
RuleDiscoveryService
CommandDiscoveryService
```

---

## M1 - Success Criteria

The extension can detect ECC assets from a repository without user configuration.

---

## M2 - Explorer Experience

### M2 - Objective

Provide visibility of ECC assets.

---

### M2 - Features

### ECC Explorer

VS Code sidebar:

```text
ECC

Skills
Rules
Commands
```

---

### Asset Navigation

Users can:

```text
Browse
Inspect
Refresh
```

repository ECC assets.

---

### M2 - Deliverables

```typescript
EccTreeProvider
```

Explorer implementation.

---

### M2 - Success Criteria

Users can see discovered ECC assets inside VS Code.

---

## M3 - Context Engine

### M3 - Objective

Create an execution-ready context model.

---

### M3 - Features

#### Editor Context

Capture:

```text
Selected Text
Current File
Language
```

---

#### Git Context

Capture:

```text
Repository
Branch
```

---

#### Workspace Context

Capture:

```text
Workspace Metadata
Relative Paths
```

---

### M3 - Deliverables

```typescript
ExecutionContextBuilder
```

---

### M3 - Success Criteria

Context can be generated independently of execution.

---

## M4 - Prompt Assembly

### M4 - Objective

Convert ECC assets and context into execution payloads.

---

### M4 - Features

#### Rule Injection

Include repository rules.

---

#### Skill Injection

Include selected skill instructions.

---

#### Context Injection

Include execution context.

---

### M4 - Deliverables

```typescript
PromptBuilder
```

```typescript
PromptPayload
```

---

### M4 - Success Criteria

Generated payloads contain:

```text
Skill
Rules
Context
User Request
```

in a consistent structure.

---

## M5 - Copilot Integration

### M5 - Objective

Execute ECC skills through GitHub Copilot.

---

### M5 - Features

#### Skill Execution

```text
Run ECC Skill
```

from VS Code.

---

#### Editor Actions

Support:

```text
Right Click
Command Palette
```

execution.

---

#### Copilot Dispatch

Submit generated ECC payloads to Copilot.

---

### M5 - Deliverables

```typescript
CopilotDispatcher
```

---

### M5 - Success Criteria

Developers can execute ECC skills without manually constructing prompts.

---

## M6 - Dynamic Skill Execution

### M6 - Objective

Support arbitrary ECC skills.

---

### M6 - Features

#### Dynamic Registration

Repository-defined skills automatically become executable.

---

#### Skill Metadata Support

Automatically expose:

```text
Name
Description
Instructions
```

for discovered skills.

---

### M6 - Deliverables

```typescript
DynamicSkillExecutor
```

---

### M6 - Success Criteria

New skills appear after discovery with no extension code changes required.

---

## M7 - Agent Tool Surface

### M7 - Objective

Expose ECC to Copilot as a capability surface.

---

### M7 - Features

#### Skill Invocation

Allow Copilot to invoke ECC skills.

---

#### Capability Projection

Present ECC as repository capabilities.

Example:

```text
Security Review
Architecture Review
Generate Tests
Refactor
```

---

### M7 - Deliverables

```typescript
EccToolProvider
```

---

### Success Criteria

ECC skills become directly accessible through Copilot workflows.

---

## Project Milestones

### Release v0.1

Contains:

```text
M1 Repository Discovery
M2 Explorer Experience
```

Focus:

```text
Visibility
Asset Discovery
```

---

### Release v0.2

Contains:

```text
M3 Context Engine
M4 Prompt Assembly
```

Focus:

```text
Execution Readiness
```

---

### Release v0.3

Contains:

```text
M5 Copilot Integration
```

Focus:

```text
End-to-End Usability
```

---

### Release v0.4

Contains:

```text
M6 Dynamic Skill Execution
```

Focus:

```text
Repository-Driven Workflows
```

---

### Release v1.0

Contains:

```text
M7 Agent Tool Surface
```

Focus:

```text
ECC As Native Copilot Capability
```

---

## Agentic Agile Execution Plan

Each milestone is decomposed into:

```text
Epic
  ↓
Feature
  ↓
Issue
  ↓
Pull Request
```

Maximum preferred issue size:

```text
2-6 hours
```

Each issue must:

- map to one milestone
- define acceptance criteria
- define technical constraints
- define testing requirements

---

## Definition of Milestone Completion

A milestone is complete when:

- all associated issues are closed
- all acceptance criteria are met
- documentation is updated
- tests pass
- architecture remains compliant with ARCHITECTURE.md

---

## North Star

The project succeeds when a developer can clone any ECC-enabled repository, install the extension, and immediately gain repository-aware ECC workflows inside GitHub Copilot without additional configuration.
