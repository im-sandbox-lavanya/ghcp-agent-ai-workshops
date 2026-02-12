# Workshop 1: Spec → Plan → Design → Code with GitHub Copilot Agents

> **Duration:** 2.5 - 3 hours  
> **Format:** Instructor-led, challenge-based workshop  
> **Difficulty:** 🟡 Intermediate to 🔴 Advanced  
> **Audience:** Developers, Technical Leads, Architects  
> **Focus:** Applying GitHub Copilot as an agent across the software development lifecycle

---

## 1. Workshop Purpose

This workshop demonstrates a practical approach to using **GitHub Copilot beyond code completion**, by applying it across the full software development lifecycle.

Participants start with a loosely defined problem and progressively move through **specification, planning, design, and implementation**, using Copilot as a reasoning partner at each stage.

The emphasis is on **structure over prompting tricks**—showing how well-defined artifacts enable AI agents to produce more reliable and predictable results.

## 2. Design Principles

- Spec-first, not code-first
- Workflow over tooling
- No live installations during the session
- One continuous use case throughout
- Lightweight, repeatable artifacts
- Explicit alignment between spec, design, and code

---

## 3. Scope Decisions (Intentional)

### ✅ Included

- Copilot Chat for reasoning and generation
- Spec-kit style artifacts (markdown-based)
- Structured prompting patterns
- MCP as a **conceptual model** for shared context

### ❌ Excluded

- Copilot CLI (focus is on structured artifacts, not terminal)
- SDK-based agent orchestration
- Full application deployment
- Complex technical domains

This keeps the workshop focused on **how structure improves AI outputs**, not tooling complexity.

---

## Difficulty & Challenge Levels

| Level | Description | Time Pressure |
|-------|-------------|---------------|
| 🟢 **Core** | Must complete - foundational skills | Guided pace |
| 🟡 **Challenge** | Stretch goals - deeper understanding | Time-boxed |
| 🔴 **Bonus** | Expert level - independent problem solving | Self-paced |

---

## 4. Pre-Provisioned Repository

To keep the workshop focused and on schedule, participants are provided with a pre-configured repository.

The repository includes a **spec-kit-style structure**, implemented as simple markdown files. Spec-kit is used here as a **structuring pattern**, not as a runtime tool or dependency.

```
/workshop-repo
├── spec/                  ← Spec-Kit structure
│   ├── spec.md
│   ├── acceptance.md
│   ├── assumptions.md
│   └── constraints.md
├── plan/
│   └── plan.md
├── design/
│   └── design.md
├── src/
│   └── starter/
├── prompts/               ← Starter prompts
│   ├── spec-agent.md
│   ├── planning-agent.md
│   ├── design-agent.md
│   └── coding-agent.md
└── README.md
```

> **Note:** All documents are intentionally incomplete to support guided completion during the workshop.

---

## 5. Agent Strategy for Spec-Driven Development

Participants work with **four distinct agent roles**:

### 1. 📋 Spec Agent
- Clarifies requirements from ambiguous inputs
- Identifies assumptions and constraints
- Structures acceptance criteria

### 2. 🗺️ Planning Agent
- Breaks requirements into components
- Identifies dependencies and sequencing
- Creates traceable task breakdowns

### 3. 🏗️ Design Agent
- Defines high-level architecture
- Assigns component responsibilities
- Validates design against specification

### 4. 💻 Coding Agent
- Scaffolds implementation from design
- Reviews code for spec alignment
- Advises on refactoring

> Agents are defined via **clear instructions**, not SDKs.

---

## 6. Prompting Approach

This workshop uses **guided prompting** to ensure consistent outcomes while allowing participants to iterate and adapt.

Prompting happens primarily through **GitHub Copilot Chat**, grounded by the repository artifacts. To support a smooth hands-on experience, **starter prompts** are provided for each stage of the workflow.

### These prompts:

- Act as starting points, not scripts
- Describe intent as well as example wording
- Encourage refinement based on evolving context

## 7. Agenda & Flow (2.5 - 3 Hours)

### 1. Introduction: Copilot as an Agent ⏱️ _10 minutes_

**Why typical Copilot usage falls short:**
- Over-reliance on code completion
- Lack of structured inputs
- Inconsistent outputs

**How agent-style workflows help:**
- Better inputs produce better outputs
- Structure enables reasoning
- Artifacts create traceability

#### Flow Overview
```
Spec → Plan → Design → Code → Validate
```

**✅ Outcome:** Shared understanding of structured AI workflows.

---

### 2. Lab 1: Specification with Agents ⏱️ _25 minutes_

Participants begin with a short, ambiguous problem statement.

Using Copilot Chat, they:

- Clarify requirements
- Identify assumptions and constraints
- Define functional and non-functional requirements
- Capture acceptance criteria

**Artifacts updated:**
- `spec/spec.md`
- `spec/acceptance.md`
- `spec/assumptions.md`
- `spec/constraints.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 1.1 | Extract 5+ functional requirements from the ambiguous statement | 🟢 Core | 10 |
| 1.2 | Identify 3+ hidden assumptions the stakeholder didn't mention | 🟢 Core | 10 |
| 1.3 | Define 3+ measurable acceptance criteria with specific thresholds | 🟡 Challenge | 15 |
| 1.4 | Identify a conflicting requirement and propose resolution | 🔴 Bonus | 20 |

**✅ Outcome:** A clear, structured specification that both humans and AI agents can reason over.

---

### 3. Lab 2: Planning from the Specification ⏱️ _25 minutes_

Participants derive an execution plan directly from the completed specification.

With Copilot support, they:

- Break the solution into logical components
- Identify dependencies and sequencing
- Create a lightweight task breakdown

**Artifact updated:**
- `plan/plan.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 2.1 | Break solution into 4+ logical components with clear boundaries | 🟢 Core | 10 |
| 2.2 | Create dependency graph showing component relationships | 🟢 Core | 10 |
| 2.3 | Identify critical path and estimate relative effort | 🟡 Challenge | 15 |
| 2.4 | Propose parallel workstreams and identify merge points | 🔴 Bonus | 20 |

**✅ Outcome:** A plan that is explicitly traceable to the original requirements.

---

### 4. Lab 3: Design with Validation ⏱️ _30 minutes_

Participants create a simple but structured design.

Activities include:

- Defining a high-level architecture
- Assigning responsibilities to components
- Outlining APIs or data models (where applicable)
- Validating the design against the specification

**Artifact updated:**
- `design/design.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 3.1 | Create architecture diagram with component interactions | 🟢 Core | 10 |
| 3.2 | Define API contracts for 2+ component interfaces | 🟢 Core | 10 |
| 3.3 | Create traceability matrix: requirements → design decisions | 🟡 Challenge | 15 |
| 3.4 | Identify 2+ design trade-offs and justify your choices | 🟡 Challenge | 15 |
| 3.5 | Propose alternative architecture and compare pros/cons | 🔴 Bonus | 25 |

**✅ Outcome:** A design that clearly satisfies the documented requirements.

---

### 5. Lab 4: Implementation with Copilot Agents ⏱️ _35 minutes_

Participants move from design to code, using Copilot as:

- A scaffolding assistant
- A reviewer for spec alignment
- A refactoring advisor

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 4.1 | Scaffold complete project structure matching design | 🟢 Core | 10 |
| 4.2 | Implement 2+ core components with working code | 🟢 Core | 15 |
| 4.3 | Add input validation and error handling | 🟡 Challenge | 15 |
| 4.4 | Write unit tests for at least one component | 🟡 Challenge | 15 |
| 4.5 | Implement stretch feature not in original spec | 🔴 Bonus | 25 |

**✅ Outcome:** A minimal working implementation aligned with the original specification.

---

### 6. Lab 5: Validation and Alignment Review ⏱️ _15 minutes_

**Goal:** Ensure implementation aligns with specification.

Participants use Copilot to:

- Compare code against the specification
- Identify missing or partially implemented requirements
- Detect areas of potential spec drift

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 5.1 | Create alignment checklist: spec requirement → implementation status | 🟢 Core | 10 |
| 5.2 | Identify and document 2+ spec drift areas | 🟡 Challenge | 15 |
| 5.3 | Propose fixes for identified gaps | 🟡 Challenge | 15 |
| 5.4 | Generate automated validation tests from acceptance criteria | 🔴 Bonus | 25 |

**✅ Outcome:** Verified alignment between spec and implementation.

---

## 8. MCP Context Model (Conceptual)

For spec-driven development, shared context includes:

| Context Element | Purpose |
|-----------------|---------|
| Specification | Requirements and acceptance criteria |
| Assumptions | Explicit assumptions made |
| Constraints | Technical and business boundaries |
| Plan | Task breakdown and sequencing |
| Design | Architecture and component responsibilities |

> MCP is presented conceptually—participants capture context in markdown artifacts.

---

## 9. Success Criteria

By the end of this workshop, participants will have:

- [ ] Created a structured specification from ambiguous requirements
- [ ] Derived an explicit plan traceable to requirements
- [ ] Designed a solution validated against the spec
- [ ] Implemented core functionality aligned with design
- [ ] Validated implementation against original specification
- [ ] Understood how structure improves AI agent outputs

---

## 10. Scoring & Achievement Levels

### Point Breakdown

| Category | Points Available |
|----------|------------------|
| 🟢 Core Challenges | 95 points |
| 🟡 Challenge Tasks | 120 points |
| 🔴 Bonus Tasks | 115 points |
| **Total Possible** | **330 points** |

### Achievement Levels

| Level | Points | Badge |
|-------|--------|-------|
| 🥇 **Spec Master** | 280+ | Exceptional spec-driven development skills |
| 🥈 **Architect** | 200-279 | Strong end-to-end workflow execution |
| 🥉 **Builder** | 120-199 | Solid foundational understanding |
| **Participant** | <120 | Completed core workshop activities |

### Time Bonuses

| Completion Time | Bonus |
|-----------------|-------|
| Under 2 hours | +30 points |
| Under 2.5 hours | +15 points |

---

## Appendix: Starter Prompts

### Specification Prompt
```
Given this problem statement:

[Problem statement]

Help me create a structured specification by:
1. Clarifying ambiguous requirements
2. Identifying assumptions we need to make
3. Defining constraints (technical, time, scope)
4. Writing clear acceptance criteria

Ask clarifying questions if needed.
```

### Planning Prompt
```
Based on this specification:

[Specification summary]

Create an execution plan that:
1. Breaks the solution into logical components
2. Identifies dependencies between components
3. Sequences tasks appropriately
4. Maps each task back to a requirement

Keep the plan lightweight and actionable.
```

### Design Prompt
```
Given this plan:

[Plan summary]

Create a high-level design that:
1. Defines the architecture approach
2. Assigns responsibilities to components
3. Outlines key interfaces or data models
4. Validates coverage of all requirements

Highlight any design decisions that need confirmation.
```

### Implementation Prompt
```
Based on this design:

[Design summary]

Help me implement [component name] by:
1. Scaffolding the basic structure
2. Implementing core functionality
3. Following the patterns established in the design
4. Flagging any spec alignment concerns

Keep the implementation minimal but complete.
```

### Validation Prompt
```
Compare this implementation against the original specification:

Specification: [spec summary]
Implementation: [code or description]

Identify:
1. Requirements that are fully implemented
2. Requirements that are partially implemented
3. Requirements that are missing
4. Any spec drift or deviations
```
