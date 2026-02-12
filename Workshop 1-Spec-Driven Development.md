# Workshop 1: Spec → Plan → Design → Code with GitHub Copilot Agents

> **Duration:** 2 hours  
> **Format:** Instructor-led, guided hands-on workshop  
> **Audience:** Developers, Technical Leads, Architects  
> **Focus:** Creating agent-ready specifications and leveraging autonomous GitHub Copilot agents for implementation

---

## Table of Contents

1. [Workshop Purpose](#1-workshop-purpose)
   - Creating agent-ready specifications
   - Human-AI collaboration vs. autonomous execution
   - Structure over prompting tricks
2. [Design Principles](#2-design-principles)
   - Spec-first approach
   - Agent-ready specifications
   - Human-agent collaboration model
   - Lightweight, repeatable artifacts
3. [Pre-Provisioned Repository](#3-pre-provisioned-repository)
   - Spec-kit structure overview
   - Repository folder organization
   - Starter prompt files for each phase
4. [Two-Phase Approach: Collaborative + Autonomous](#4-two-phase-approach-collaborative--autonomous)
   - [Phase 1: Collaborative Specification (Labs 1-3)](#phase-1-collaborative-specification-labs-1-3)
     - Using GitHub Copilot Chat as reasoning partner
     - Creating structured, agent-consumable specifications
   - [Phase 2: Autonomous Implementation (Lab 4)](#phase-2-autonomous-implementation-lab-4)
     - Assigning work to GitHub Copilot coding agent
     - Agent autonomously implements and opens PR
5. [Agenda & Flow (2 Hours)](#5-agenda--flow-2-hours)
   - [1. Introduction: From Copilot Chat to Autonomous Agents (10 min)](#1-introduction-from-copilot-chat-to-autonomous-agents-10-minutes)
     - Understanding AI agents vs. code completion
     - Why agents need structured inputs
     - Workshop flow overview
   - [2. Lab 1: Specification with Agents (20 min)](#2-lab-1-specification-with-agents-20-minutes)
     - Clarify ambiguous problem statements
     - Define functional & non-functional requirements
     - Capture assumptions, constraints, and acceptance criteria
     - **Artifacts:** `spec.md`, `acceptance.md`, `assumptions.md`, `constraints.md`
   - [3. Lab 2: Planning from the Specification (20 min)](#3-lab-2-planning-from-the-specification-20-minutes)
     - Break solution into logical components
     - Identify dependencies and sequencing
     - Create task breakdown
     - **Artifacts:** `plan.md`
   - [4. Lab 3: Design with Validation (20 min)](#4-lab-3-design-with-validation-20-minutes)
     - Define high-level architecture
     - Assign component responsibilities
     - Outline APIs and data models
     - Validate against specification
     - **Artifacts:** `design.md`
   - [5. Lab 4: Autonomous Implementation with GitHub Copilot Agent (30 min)](#5-lab-4-autonomous-implementation-with-github-copilot-agent-30-minutes)
     - Create GitHub issue referencing spec/plan/design
     - Assign issue to `@copilot` for autonomous implementation
     - Monitor agent progress
     - Review agent-generated pull request
     - **Artifacts:** GitHub Issue, Branch, Pull Request with code
   - [6. PR Review and Reflection (10 min)](#6-pr-review-and-reflection-10-minutes)
     - Group discussion on agent performance
     - Quality correlation between specs and implementation
     - Key takeaways and next steps

---

## 1. Workshop Purpose

This workshop demonstrates how to prepare specifications that enable **autonomous AI agents** to successfully implement solutions with minimal human intervention.

Participants start with a loosely defined problem and work through **specification, planning, and design** using GitHub Copilot Chat as a collaborative partner. They then **hand off implementation to the GitHub Copilot coding agent**, which autonomously creates a pull request with working code.

The emphasis is on **structure over prompting tricks**—showing how well-defined, structured artifacts (using the spec-kit pattern) enable AI agents to produce more reliable and predictable results. This teaches a critical skill for the AI-augmented development era: **creating specifications that agents can execute.**

## 2. Design Principles

- ✅ Spec-first, not code-first
- ✅ Agent-ready specifications using structured formats
- ✅ Human-agent collaboration in early phases
- ✅ Autonomous agent execution for implementation
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

## 4. Two-Phase Approach: Collaborative + Autonomous

This workshop demonstrates a **hybrid workflow** that combines human-AI collaboration with autonomous agent execution:

### Phase 1: Collaborative Specification (Labs 1-3)
Participants use **GitHub Copilot Chat** as a reasoning partner to create structured specifications. Starter prompt guidance is provided to help participants have productive conversations with Copilot.

**Starter prompts:**
- Act as conversation guides, not scripts
- Help participants ask better questions
- Ensure artifacts are agent-ready

### Phase 2: Autonomous Implementation (Lab 4)
Participants create a GitHub issue from their specifications and **assign it to the GitHub Copilot coding agent**. The agent autonomously:
- Reads the spec-kit structured files
- Plans the implementation approach
- Creates a new branch
- Implements the solution
- Opens a pull request for review

This teaches the critical transition from **human-guided specification** to **agent-driven execution**.

## 5. Agenda & Flow (2 Hours)

### 1. Introduction: From Copilot Chat to Autonomous Agents (10 minutes)

- How Copilot is commonly used today (code completion)
- What makes an AI system an "agent" (autonomy, planning, execution)
- Introduction to GitHub Copilot coding agent
- Why autonomous agents require structured, high-quality inputs
- Overview of the workshop flow: **Spec (Human+AI) → Plan (Human+AI) → Design (Human+AI) → Code (Autonomous Agent) → Review**

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

### 4. Lab 3: Design with Validation (20 minutes)

Participants create a simple but structured design.

Activities include:

- Defining a high-level architecture
- Assigning responsibilities to components
- Outlining APIs or data models (where applicable)
- Validating the design against the specification
- **Ensuring all artifacts are agent-ready** (clear, unambiguous, complete)

**Artifact updated:**
- `design/design.md`

**✅ Outcome:** A design that clearly satisfies the documented requirements and provides sufficient detail for an autonomous agent to implement.

### 5. Lab 4: Autonomous Implementation with GitHub Copilot Agent (30 minutes)

Participants **hand off implementation to the GitHub Copilot coding agent** for autonomous execution.

**Activities:**

1. **Create a GitHub Issue** summarizing the work:
   - Reference the spec, plan, and design files
   - Include acceptance criteria
   - Provide any implementation preferences

2. **Assign the issue to `@copilot`** using the GitHub Copilot coding agent:
   - The agent reads all spec-kit files
   - Plans its implementation approach
   - Creates a branch autonomously
   - Implements the solution
   - Opens a pull request

3. **Monitor agent progress** through GitHub notifications

4. **Review the agent's PR**:
   - Does it satisfy the specification?
   - Does it follow the design?
   - Are acceptance criteria met?
   - What would you accept/reject?

**Artifacts created:**
- GitHub Issue
- Agent-created branch
- Agent-created Pull Request with implementation

**✅ Outcome:** Experience the full lifecycle of agent-driven development—from structured specification to autonomous implementation to human review.

### 6. PR Review and Reflection (10 minutes)

Participants review the agent's work and reflect on the process:

**Group Discussion:**
- How well did the agent follow the specification?
- What made the difference between good and poor agent outcomes?
- How did spec quality impact implementation quality?
- What would you do differently next time?

**Key Takeaways:**
- Well-structured specs = better agent results
- The spec-kit pattern provides agent-consumable structure
- Human oversight remains critical (review, validation)
- Agent workflows require different thinking than manual coding

**Next Steps:**
- Consider using spec-kit as a tool (not just a pattern) for automation
- Explore other GitHub Copilot agent capabilities
- Apply this workflow to real projects
