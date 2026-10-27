# ECC Harness Adapter for VS Code - Technical Decisions

## Technical Decisions Registry

Version: 0.1

This document captures the initial technical decisions for the project.

The purpose is to eliminate ambiguity for autonomous agents and provide a stable foundation for implementation.

Future architectural changes must be documented through ADRs.

---

## TD-001: Primary Technology Stack

### TD-001: Decision

Use:

```text
TypeScript
Node.js
VS Code Extension API
```

### TD-001: Rationale

- Native VS Code ecosystem support
- Strong typing
- Mature tooling
- Excellent testing ecosystem
- Largest contributor pool

### TD-001: Status

Approved

---

## TD-002: Runtime Target

### TD-002: Decision

Target the current VS Code Extension Host runtime.

#### TD-002: Environment

```text
Node.js
VS Code Desktop
```

### TD-002: Rationale

This project is a native VS Code extension.

Browser support is not required for MVP.

### TD-002: Status

Approved

---

## TD-003: Extension Architecture

### TD-003: Decision

Use layered architecture.

```text
UI
 ↓
Application
 ↓
Domain Services
 ↓
Infrastructure
```

#### TD-003: Core Layers

```text
Discovery
Registry
Context
Prompt
Dispatch
```

### TD-003: Rationale

Supports:

- maintainability
- testing
- future execution surfaces

### TD-003: Status

Approved

---

## TD-004: Asset Discovery Strategy

### TD-004: Decision

Use convention-based discovery.

#### TD-004: Supported Locations

```text
skills/
.ecc/skills/

rules/
.ecc/rules/

commands/
.ecc/commands/
```

### TD-004: Rationale

Minimises configuration.

Repositories remain the source of truth.

### TD-004: Status

Approved

---

## TD-005: Central Registry Pattern

### TD-005: Decision

All discovered assets shall be stored in a central registry.

#### TD-005: Component

```typescript
AssetRegistry
```

#### TD-005: Responsibility

```text
Skills
Rules
Commands
```

### TD-005: Rationale

Avoid repeated filesystem scans.

Provides a single source of truth.

### TD-005: Status

Approved

---

## TD-006: Context Collection Model

### TD-006: Decision

Context is collected just-in-time during skill execution.

#### TD-006: Context Sources

```text
Editor
Workspace
Git
```

#### TD-006: Data Captured

```text
Selected Text
Current File
File Type
File Path
Workspace Name
Git Branch
```

### TD-006: Rationale

Avoid stale execution data.

### TD-006: Status

Approved

---

## TD-007: Prompt Assembly Ownership

### TD-007: Decision

Only the Prompt Builder may create execution payloads.

#### TD-007: Component

```typescript
PromptBuilder
```

No other component may assemble prompts.

### TD-007: Rationale

Single ownership.

Predictable prompt generation.

### TD-007: Status

Approved

---

## TD-008: Copilot Isolation

### TD-008: Decision

Copilot integration must be isolated behind an abstraction.

#### TD-008: Interface

```typescript
Dispatcher
```

#### TD-008: Initial Implementation

```typescript
CopilotDispatcher
```

### TD-008: Rationale

Future execution surfaces may exist.

Core business logic should remain Copilot-independent.

### TD-008: Status

Approved

---

## TD-009: Repository-Driven Behaviour

### TD-009: Decision

The extension must never hardcode repository skills.

#### TD-009: Allowed

```text
Repository-defined skills
Repository-defined rules
Repository-defined commands
```

#### TD-009: Not Allowed

```text
Embedded project-specific skills
Embedded workflow definitions
```

### TD-009: Rationale

ECC owns workflow definitions.

The harness projects those definitions.

### TD-009: Status

Approved

---

## TD-010: Skill Execution Model

### TD-010: Decision

Skills execute through a common pipeline.

#### TD-010: Execution Flow

```text
Skill Selected
      ↓
Load Skill
      ↓
Load Rules
      ↓
Collect Context
      ↓
Build Payload
      ↓
Dispatch
```

### TD-010: Rationale

Consistent execution path.

Simplifies testing.

### TD-010: Status

Approved

---

## TD-011: Dependency Management

### TD-011: Decision

Use npm.

#### TD-011: Package Manager

```text
npm
```

### TD-011: Rationale

Default VS Code ecosystem choice.

Reduces onboarding complexity.

### TD-011: Status

Approved

---

## TD-012: Code Quality Standards

### TD-012: Decision

Enable TypeScript strict mode.

#### TD-012: Required

```json
{
  "strict": true
}
```

#### TD-012: Avoid

```typescript
any
```

Use only when unavoidable and documented.

### TD-012: Rationale

Reduces runtime defects.

Improves autonomous code generation reliability.

### TD-012: Status

Approved

---

## TD-013: Linting

### TD-013: Decision

Use ESLint.

#### TD-013: Standard

```text
eslint
typescript-eslint
```

### TD-013: Rationale

Industry standard tooling.

Predictable autonomous development experience.

### TD-013: Status

Approved

---

## TD-014: Formatting

### TD-014: Decision

Use Prettier.

#### TD-014: Enforcement

Automatic formatting on commit.

### TD-014: Rationale

Removes formatting decisions from implementation work.

### TD-014: Status

Approved

---

## TD-015: Unit Testing Framework

### TD-015: Decision

Use Vitest.

#### TD-015: Framework

```text
Vitest
```

### TD-015: Rationale

- Fast execution
- Native TypeScript support
- Simple configuration
- Modern ecosystem

### TD-015: Status

Approved

---

## TD-016: Test Coverage Target

### TD-016: Decision

Target:

```text
90%+
```

for:

```text
Discovery
Registry
Context
Prompt
```

#### TD-016: Exclusions

```text
VS Code API wrappers
Generated boilerplate
```

### TD-016: Status

Approved

---

## TD-017: Integration Testing

### TD-017: Decision

Create integration tests for:

```text
Asset Discovery
Registry Updates
Prompt Assembly
Execution Pipeline
```

### TD-017: Rationale

Most project defects will occur between layers.

### TD-017: Status

Approved

---

## TD-018: Logging Strategy

### TD-018: Decision

Use a centralized logger.

#### TD-018: Component

```typescript
Logger
```

#### TD-018: Levels

```text
Debug
Info
Warn
Error
```

### TD-018: Rationale

Simplifies troubleshooting.

Supports autonomous diagnostics.

### TD-018: Status

Approved

---

## TD-019: Error Handling Philosophy

### TD-019: Decision

Fail gracefully.

#### TD-019: Discovery Errors

```text
Log
Skip Asset
Continue
```

#### TD-019: Workspace Errors

```text
Notify User
Remain Operational
```

### TD-019: Rationale

One malformed asset should not disable the extension.

### TD-019: Status

Approved

---

## TD-020: VS Code Explorer Model

### TD-020: Decision

Use a dedicated Tree View.

#### TD-020: Explorer

```text
ECC

Skills
Rules
Commands
```

#### TD-020: Source

```text
AssetRegistry
```

The explorer must never query the filesystem directly.

### TD-020: Rationale

Clear separation of concerns.

### TD-020: Status

Approved

---

## TD-021: Command Registration Model

### TD-021: Decision

Commands are registered centrally.

#### TD-021: Location

```typescript
extension.ts
```

#### TD-021: Pattern

```typescript
registerCommand()
```

through dedicated command modules.

### TD-021: Rationale

Predictable extension startup.

### TD-021: Status

Approved

---

## TD-022: Configuration Philosophy

### TD-022: Decision

Configuration should be optional.

#### TD-022: Default Behaviour

```text
Install
Open Repository
Use Extension
```

#### TD-022: Configuration Required

Only when overriding discovery conventions.

### TD-022: Rationale

Zero-friction onboarding.

### TD-022: Status

Approved

---

## TD-023: Documentation As Code

### TD-023: Decision

Architecture, roadmap, and governance documents are required project artefacts.

#### TD-023: Required Documents

```text
README.md
PRD.md
ARCHITECTURE.md
ROADMAP.md
AGENTS.md
TECHNICAL_DECISIONS.md
```

Changes to implementation that affect architecture must update documentation.

### TD-023: Status

Approved

---

## TD-024: Autonomous Development Constraints

### TD-024: Decision

Development agents may:

```text
Implement issues
Write tests
Update documentation
Create pull requests
```

Development agents may not:

```text
Change architecture
Change roadmap
Change technical decisions
Change requirements
```

without an approved ADR.

### TD-024: Rationale

Prevent scope drift and architectural instability.

### TD-024: Status

Approved

---

## TD-025: MVP Success Architecture

### TD-025: Decision

The MVP is complete when the following end-to-end workflow succeeds:

```text
Repository Contains ECC Assets
            ↓
Extension Discovers Assets
            ↓
User Selects Skill
            ↓
Context Collected
            ↓
Prompt Generated
            ↓
Prompt Sent To Copilot
```

without manual prompt construction.

### TD-025: Status

Approved

---

## TD-025: Change Process

Any modification to a technical decision requires:

```text
ADR Proposal
      ↓
Review
      ↓
Approval
      ↓
Implementation
```

No implementation should contradict an approved technical decision.
