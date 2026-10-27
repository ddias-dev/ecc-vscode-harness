# ECC Harness Adapter for VS Code

> Native VS Code execution surface for ECC workflows and GitHub Copilot.

The ECC Harness Adapter bridges ECC repositories with GitHub Copilot by automatically discovering ECC assets, assembling repository context, and dispatching structured requests to Copilot. [https://github.com/affaan-m/ECC](https://github.com/affaan-m/ECC)

Instead of manually opening skill files, copying prompts, and gathering repository rules, developers execute ECC workflows directly from VS Code.

---

## Vision

ECC defines workflows.

GitHub Copilot executes workflows.

The ECC Harness Adapter connects the two.

```text
ECC Repository
       │
       ▼
ECC Harness Adapter
       │
       ▼
GitHub Copilot
```

Developers remain inside VS Code while benefiting from repository-specific skills, rules, and guidance.

---

## Problem

Without an adapter, using ECC with GitHub Copilot typically requires:

```text
Find Skill
    ↓
Open Skill File
    ↓
Copy Instructions
    ↓
Find Rules
    ↓
Copy Rules
    ↓
Copy Code Context
    ↓
Open Copilot
    ↓
Build Prompt Manually
```

This process is repetitive, inconsistent, and difficult to scale across teams.

The ECC Harness Adapter automates the process.

---

## Solution

The adapter automatically:

- discovers ECC assets
- loads repository rules
- gathers workspace context
- assembles execution payloads
- dispatches requests to Copilot

Result:

```text
Right Click
      ↓
Run ECC Skill
      ↓
Copilot Receives Full Context
```

---

## Core Capabilities

### ECC Asset Discovery

Automatically discover repository assets.

Supported asset types:

```text
Skills
Rules
Commands
```

Example:

```text
skills/
rules/
commands/
```

---

### ECC Explorer

Dedicated VS Code explorer view.

```text
ECC

Skills
 ├─ security-review
 ├─ refactor
 └─ generate-tests

Rules
 ├─ security
 └─ coding-standards

Commands
 ├─ review
 └─ audit
```

---

### Context Collection

The adapter automatically gathers:

```text
Selected Code
Current File
Programming Language
File Path
Workspace Metadata
Git Branch
```

---

### Prompt Assembly

The adapter builds structured payloads using:

```text
ECC Skill
+
Repository Rules
+
Execution Context
+
User Intent
```

Example:

```text
Execute ECC Skill:
security-review

Repository Rules:
...

Current File:
src/auth.ts

Selected Code:
...

Perform a security review.
```

---

### Copilot Integration

Generated payloads are dispatched directly to GitHub Copilot.

Developers stay within the Copilot workflow without manually constructing prompts.

---

## Example Workflow

### Security Review

Developer selects code:

```typescript
authenticateUser()
```

Then:

```text
Right Click
  └─ ECC → Security Review
```

The adapter:

```text
Loads Skill
Loads Rules
Collects Context
Builds Payload
Dispatches To Copilot
```

Copilot receives a fully assembled request.

---

## Architecture

```text
┌─────────────────────────┐
│        VS Code          │
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│ ECC Harness Adapter     │
└────────────┬────────────┘
             │
     ┌───────┼───────┐
     ▼       ▼       ▼
 Discovery Context Prompt
   Layer    Layer   Layer
             │
             ▼
      Dispatch Layer
             │
             ▼
     GitHub Copilot
```

---

## Project Structure

```text
src/

application/

discovery/
  skillDiscoveryService.ts
  ruleDiscoveryService.ts
  commandDiscoveryService.ts

registry/
  assetRegistry.ts

context/
  executionContextBuilder.ts
  editorContextProvider.ts
  gitContextProvider.ts

prompt/
  promptBuilder.ts

dispatch/
  copilotDispatcher.ts

explorer/
  eccTreeProvider.ts

commands/
  runSkillCommand.ts

types/
```

---

## Roadmap

### v0.1

Repository Discovery

- Skill discovery
- Rule discovery
- Command discovery
- Asset registry

---

### v0.2

Explorer Experience

- ECC Explorer
- Asset browsing
- Refresh support

---

### v0.3

Execution Context

- Editor context
- Git context
- Workspace context

---

### v0.4

Prompt Assembly

- Skill injection
- Rule injection
- Context injection

---

### v0.5

Copilot Integration

- Skill execution
- Command palette actions
- Context menu actions

---

### v1.0

Native ECC Execution Surface

- Dynamic skill execution
- Repository-driven workflows
- ECC capabilities exposed to Copilot

---

## Development Methodology

This repository follows an Agentic Agile workflow.

```text
Roadmap
    ↓
Milestones
    ↓
Epics
    ↓
Issues
    ↓
Pull Requests
    ↓
Review
```

All work must be traced to a GitHub Issue.

See:

- `docs/PRD.md`
- `docs/ARCHITECTURE.md`
- `AGENTS.md`
- `docs/ADR/`

for project governance and implementation guidance.

---

## Repository Setup

```bash
git clone https://github.com/ddias-dev/ecc-vscode-harness.git

cd ecc-vscode-harness

npm install
```

---

## Contributing

Before implementing any feature:

1. Review the current milestone.
2. Review the associated issue.
3. Review architecture requirements.
4. Confirm acceptance criteria.
5. Ensure compliance with `AGENTS.md`.

All architectural changes require an ADR.

---

## Project Goal

The project succeeds when a developer can:

1. Open an ECC-enabled repository.
2. Install the extension.
3. Execute an ECC skill.
4. Have repository rules and context automatically applied.
5. Receive results through GitHub Copilot.

Without manually opening skill files, copying prompts, or assembling context.

---

## Status

Current Status:

```text
Planning / Pre-Development
```

Current Focus:

```text
M1 - Repository Discovery
```
