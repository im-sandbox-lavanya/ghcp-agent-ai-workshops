# Workshop 1: Spec → Plan → Design → Code with GitHub Copilot Agents

> **Duration:** 2 hours  
> **Format:** Instructor-led, guided hands-on workshop  
> **Audience:** Developers, Technical Leads, Architects  
> **Focus:** Applying GitHub Copilot as an agent across the software development lifecycle

---

## 1. Workshop Purpose

This workshop demonstrates a practical approach to using **GitHub Copilot beyond code completion**, by applying it across the full software development lifecycle.

Participants start with a loosely defined problem and progressively move through **specification, planning, design, and implementation**, using Copilot as a reasoning partner at each stage.

The emphasis is on **structure over prompting tricks**—showing how well-defined artifacts enable AI agents to produce more reliable and predictable results.

## 2. Design Principles

- ✅ Spec-first, not code-first
- ✅ Workflow over tooling
- ✅ No live installations during the session
- ✅ One continuous use case throughout
- ✅ Lightweight, repeatable artifacts
- ✅ Explicit alignment between spec, design, and code

## 3. Pre-Provisioned Repository

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

## 4. Prompting Approach

This workshop uses **guided prompting** to ensure consistent outcomes while allowing participants to iterate and adapt.

Prompting happens primarily through **GitHub Copilot Chat**, grounded by the repository artifacts. To support a smooth hands-on experience, **starter prompts** are provided for each stage of the workflow.

### These prompts:

- Act as starting points, not scripts
- Describe intent as well as example wording
- Encourage refinement based on evolving context

## 5. Agenda & Flow (2 Hours)

### 1. Introduction: Copilot as an Agent (10 minutes)

- How Copilot is commonly used today
- Why agent-style workflows require better inputs
- Overview of the workshop flow: **Spec → Plan → Design → Code → Validate**

### 2. Lab 1: Specification with Agents (20 minutes)

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

**✅ Outcome:** A clear, structured specification that both humans and AI agents can reason over.

### 3. Lab 2: Planning from the Specification (20 minutes)

Participants derive an execution plan directly from the completed specification.

With Copilot support, they:

- Break the solution into logical components
- Identify dependencies and sequencing
- Create a lightweight task breakdown

**Artifact updated:**
- `plan/plan.md`

**✅ Outcome:** A plan that is explicitly traceable to the original requirements.

### 4. Lab 3: Design with Validation (25 minutes)

Participants create a simple but structured design.

Activities include:

- Defining a high-level architecture
- Assigning responsibilities to components
- Outlining APIs or data models (where applicable)
- Validating the design against the specification

**Artifact updated:**
- `design/design.md`

**✅ Outcome:** A design that clearly satisfies the documented requirements.

### 5. Lab 4: Implementation with Copilot Agents (25 minutes)

Participants move from design to code, using Copilot as:

- A scaffolding assistant
- A reviewer for spec alignment
- A refactoring advisor

Only core functionality is implemented to keep scope controlled.

**✅ Outcome:** A minimal working implementation aligned with the original specification.

### 6. Validation and Alignment Review (10 minutes)

Participants use Copilot to:

- Compare code against the specification
- Identify missing or partially implemented requirements
- Detect areas of potential spec drift
