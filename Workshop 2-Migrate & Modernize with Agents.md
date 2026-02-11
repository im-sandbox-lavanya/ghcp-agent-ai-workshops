# Workshop 2: Migrate & Modernize with Agents (.NET, Custom Agents)

---

## Overview

**Duration:** 2 hours  
**Format:** Instructor-led, guided hands-on workshop  
**Audience:** Developers, Tech Leads, Architects  
**Focus:** Using custom AI agents to modernize an existing .NET application

---

## 1. Workshop Purpose

This workshop demonstrates how **custom AI agents** can be used to **analyze, migrate, and modernize legacy applications**, with a focus on .NET.

Participants will move beyond generic Copilot usage by **creating and applying a purpose-built agent** that understands modernization goals, constraints, and target architectures.

The emphasis is on **guided, repeatable modernization workflows**, not one-off refactoring.

---

## 2. Design Principles

- Modernization before migration
- Custom agents over generic prompting
- Incremental change, not big-bang rewrites
- Explicit constraints and target state
- Enterprise-safe patterns and decisions

---

## 3. Pre-Provisioned Repository

Participants are provided with a pre-configured repository containing a
**legacy .NET application**, modernization targets, and scaffolding for
custom agents.

No live installation or setup is performed during the workshop.

```
/workshop-repo
├── legacy-app/                    ← Legacy .NET application
│   ├── Controllers/
│   ├── Services/
│   ├── Data/
│   └── Program.cs
│
├── modernization/
│   ├── current-state.md
│   ├── target-state.md
│   ├── constraints.md
│   └── modernization-goals.md
│
├── agents/
│   ├── modernization-agent.md     ← Custom agent definition
│   └── review-agent.md            ← Optional validation agent
│
├── src-modernized/
│   └── starter/
│
├── prompts/
│   ├── analysis.md
│   ├── modernization.md
│   └── validation.md
│
└── README.md
```

All documentation is intentionally incomplete to support guided completion.

---

## 4. Custom Agent Strategy

This workshop introduces **custom agents** as first-class modernization
tools.

The agent is designed to:

- Understand the legacy codebase
- Apply modernization goals consistently
- Enforce constraints (e.g., frameworks, patterns)
- Produce explainable, reviewable output

The agent is defined using **clear instructions and responsibilities**, not complex tooling.

---

## 5. Agenda & Flow (2 Hours)

### 1. Introduction: Why Modernization Needs Agents (10 minutes)

- Common failure modes of legacy modernization
- Limitations of generic AI prompts
- Why custom agents improve consistency and safety
- Overview of the workshop flow:  
  **Analyze → Define Agent → Modernize → Validate**

**Outcome:** Shared understanding of agent-driven modernization.

### 2. Lab 1: Understand the Legacy Application (20 minutes)

**Goal:** Build a shared understanding of the current state.

**Participants:**

- Review the legacy .NET application
- Use Copilot Chat to:
  - Identify architectural smells
  - Highlight outdated patterns
  - Surface technical debt

**Artifacts updated:**

- `modernization/current-state.md`

**Outcome:** Documented baseline of the existing system.

### 3. Lab 2: Define Modernization Goals & Constraints (15 minutes)

**Goal:** Make modernization intent explicit.

**Participants:**

- Define target outcomes (e.g., .NET version, architecture style)
- Capture constraints (time, scope, dependencies)
- Clarify what will *not* be modernized

**Artifacts updated:**

- `modernization/modernization-goals.md`
- `modernization/constraints.md`

**Outcome:** Clear modernization boundaries for the agent.

### 4. Lab 3: Create a Custom Modernization Agent (25 minutes)

**Goal:** Build a purpose-driven agent for modernization.

**Participants:**

- Define agent responsibilities:
  - Code analysis
  - Refactoring guidance
  - Pattern enforcement
- Specify tone, constraints, and success criteria
- Store agent definition in:
  - `agents/modernization-agent.md`

**Outcome:** A reusable, domain-specific modernization agent.

### 5. Lab 4: Apply the Agent to Modernize the Application (30 minutes)

**Goal:** Perform guided modernization using the custom agent.

**Participants:**

- Use the agent to:
  - Refactor selected components
  - Modernize APIs and patterns
  - Improve structure and readability
- Implement changes in:
  - `src-modernized/`

**Outcome:** Partially modernized application aligned with stated goals.

### 6. Lab 5: Validate & Review with a Secondary Agent (10 minutes)

**Goal:** Ensure modernization quality and alignment.

**Participants:**

- Use a review agent to:
  - Compare legacy vs modernized code
  - Validate alignment with goals and constraints
  - Identify risks or regressions

**Artifacts updated:**

- Inline comments or `validation.md`

**Outcome:** Increased confidence in modernization decisions.


