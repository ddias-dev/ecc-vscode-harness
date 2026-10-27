# ECC Harness Adapter for VS Code - Product Requirement

Version: 0.1  
Status: Draft  
Owner: Product Team  
Target Release: MVP (v0.1)

---

## 1. Executive Summary

ECC provides a reusable workflow layer consisting of skills, rules, commands, and project guidance.

GitHub Copilot provides AI-assisted development inside VS Code.

Today, developers using ECC and Copilot must manually discover ECC assets and copy their contents into chat sessions to achieve repository-specific behaviour.

The ECC Harness Adapter for VS Code bridges this gap by making ECC capabilities directly consumable within the VS Code experience.

The adapter automatically discovers ECC assets, assembles execution context, and dispatches structured requests to Copilot.

The result is a seamless workflow where ECC becomes a native capability layer for GitHub Copilot.

---

## 2. Vision

Enable any repository containing ECC assets to become immediately usable from GitHub Copilot through a dedicated VS Code harness.

Developers should not need to:

- manually open skill files
- manually read repository rules
- manually assemble prompts
- manually copy workflow instructions

The harness should perform those tasks automatically.

---

## 3. Problem Statement

Current workflow:

```text
Developer
    ↓
Find ECC skill
    ↓
Open skill file
    ↓
Copy instructions
    ↓
Open Copilot
    ↓
Paste instructions
    ↓
Paste code
    ↓
Paste rules
    ↓
Request execution
```

Problems:

- repetitive
- inconsistent
- error-prone
- poor discoverability
- low skill adoption

Desired workflow:

```text
Developer
    ↓
Run ECC Action
    ↓
Harness builds context
    ↓
Copilot executes
```

---

## 4. Product Goals

### Goal 1

Make ECC assets discoverable within VS Code.

---

### Goal 2

Reduce prompt construction effort to a single action.

---

### Goal 3

Ensure ECC repository rules are consistently applied.

---

### Goal 4

Allow any ECC skill to be executed through Copilot.

---

### Goal 5

Create a foundation for future agent integrations.

---

## 5. Target Users

### Primary Users

#### AI-Assisted Developers

Developers using:

- VS Code
- GitHub Copilot
- Copilot Chat
- Copilot Agent Mode

who work in repositories containing ECC assets.

---

### Secondary Users

#### Teams Standardising AI Workflows

Engineering organisations that maintain:

- coding standards
- architectural guidance
- reusable review workflows
- repository-specific AI instructions

through ECC.

---

## 6. User Stories

### US-001

As a developer,

I want ECC skills to appear inside VS Code,

So that I can easily discover available workflows.

#### Acceptance Criteria - US-001

- Skills are automatically discovered.
- Skills are displayed in the ECC Explorer.
- No manual configuration is required.

---

### US-002

As a developer,

I want to run an ECC skill from the editor,

So that I do not need to manually copy prompts.

#### Acceptance Criteria - US-002

- Skill execution is available via context menu.
- Skill execution is available via command palette.
- Execution launches Copilot with assembled context.

---

### US-003

As a developer,

I want repository rules automatically included,

So that Copilot follows project guidance.

#### Acceptance Criteria

- Rules are loaded automatically.
- Rules are included in generated prompts.
- No manual rule selection is required.

---

### US-004

As a developer,

I want my current code selection included automatically,

So that Copilot receives the relevant context.

#### Acceptance Criteria - US-004

- Selected code is captured.
- Current file metadata is captured.
- Context is included in the generated request.

---

### US-005

As a developer,

I want custom ECC skills to work automatically,

So that repositories can define their own workflows.

#### Acceptance Criteria - US-005

- No code change is required.
- New skills become available after refresh.
- Skill metadata is discovered dynamically.

---

## 7. MVP Scope

### Feature 1: ECC Discovery Engine

Discover repository ECC assets.

#### Asset Types

```text
Skills
Rules
Commands
```

#### Outputs

```text
ECC Asset Registry
```

---

### Feature 2: ECC Explorer

VS Code sidebar view.

Displays:

```text
Skills
Rules
Commands
```

Example:

```text
ECC

Skills
 ├─ security-review
 ├─ refactor
 └─ generate-tests

Rules
 ├─ architecture
 └─ coding-standards
```

---

### Feature 3: Context Engine

Collect execution context.

#### Context Sources

```text
Selected Text
Current File
File Language
File Path
Git Branch
Workspace Metadata
```

---

### Feature 4: Prompt Assembly Engine

Generate a structured execution payload.

Build:

```text
Skill
+
Rules
+
Context
+
User Intent
```

Example:

```text
Execute ECC Skill:
security-review

Repository Rules:
...

Selected Code:
...

Perform a security review.
```

---

### Feature 5: Copilot Dispatch

Submit assembled payload to GitHub Copilot.

Result:

```text
Copilot executes ECC workflow
```

without requiring manual prompt construction.

---

### Feature 6: VS Code Actions

#### Context Menu

```text
ECC
 ├─ Run Skill...
 ├─ Security Review
 ├─ Refactor
 ├─ Generate Tests
 └─ Explain Code
```

#### Command Palette

```text
ECC: Run Skill
ECC: Search Skills
ECC: Refresh Workspace
ECC: View Active Rules
```

---

## 8. Functional Requirements

### FR-001

System shall discover ECC skills within the workspace.

---

### FR-002

System shall discover ECC rules within the workspace.

---

### FR-003

System shall expose discovered skills in a dedicated explorer view.

---

### FR-004

System shall allow execution of a selected skill.

---

### FR-005

System shall collect editor context before execution.

---

### FR-006

System shall include repository rules in execution payloads.

---

### FR-007

System shall generate a structured execution prompt.

---

### FR-008

System shall dispatch generated prompts to Copilot.

---

### FR-009

System shall refresh discovery without restarting VS Code.

---

## 9. Non-Functional Requirements

### Performance

Workspace discovery:

```text
< 2 seconds
```

for a typical repository.

---

### Reliability

Skill discovery failure must not crash the extension.

---

### Extensibility

New ECC asset types should be addable without major refactoring.

---

### Maintainability

Codebase must follow:

```text
TypeScript Strict Mode
```

and documented module boundaries.

---

## 10. Success Metrics

### User Adoption

- User can execute first skill within 60 seconds.

---

### Workflow Efficiency

- Reduce manual prompt construction to a single action.

---

### Discoverability

- ECC Explorer successfully displays repository assets.

---

### Execution Success

- Skill execution produces a valid Copilot request.

---

## 11. MVP Acceptance Criteria

The product is considered MVP complete when:

1. ECC assets are automatically discovered.
2. ECC assets are visible within VS Code.
3. Developers can execute an ECC skill from the editor.
4. Repository rules are automatically included.
5. Execution context is automatically assembled.
6. Copilot receives the generated ECC payload.
7. No manual prompt construction is required.

---

## 12. Future Evolution

Potential future releases may include:

- Agent Tool integration
- Dynamic command mapping
- Workflow visualisation
- Team governance packs
- Additional harness targets
- Advanced ECC capability projection

These items are outside the MVP scope and will be evaluated after successful validation of the core harness model.
