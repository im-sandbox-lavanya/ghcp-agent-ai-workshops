# Workshop 2: Migrate & Modernize with Agents

> _.NET & Java, Custom Agents, Copilot Chat_

---

## Overview

- **Duration:** 2.5 - 3 hours  
- **Format:** Instructor-led, challenge-based workshop  
- **Difficulty:** 🟡 Intermediate to 🔴 Advanced  
- **Audience:** Developers, Tech Leads, Architects  
- **Focus:** Using custom AI agents to modernize existing .NET and Java applications

---

## 1. Workshop Purpose

This workshop demonstrates how **custom AI agents** can be used to **analyze, migrate, and modernize legacy applications**, with focus on .NET and Java ecosystems.

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

## 3. Scope Decisions (Intentional)

### ✅ Included

- Copilot Chat for analysis and modernization
- Custom modernization agents (instruction-based)
- Structured modernization artifacts
- .NET Framework → .NET 8+ patterns
- Java 8 → Java 17+ patterns
- MCP as a **conceptual model** for shared context

### ❌ Excluded

- Full migration tooling (Azure Migrate, etc.)
- Database migration
- Infrastructure modernization
- Complete application rewrites

This keeps the workshop focused on **how agents improve modernization decisions**, not tooling complexity.

---

## Difficulty & Challenge Levels

| Level | Description | Time Pressure |
|-------|-------------|---------------|
| 🟢 **Core** | Must complete - foundational skills | Guided pace |
| 🟡 **Challenge** | Stretch goals - deeper understanding | Time-boxed |
| 🔴 **Bonus** | Expert level - independent problem solving | Self-paced |

---

## 4. Pre-Provisioned Repository

Participants are provided with a pre-configured repository containing a
**legacy .NET or Java application**, modernization targets, and scaffolding for
custom agents.

No live installation or setup is performed during the workshop.

```
/workshop-repo
├── legacy-app/                    ← Legacy .NET/Java application
│   ├── Controllers/               (.NET) or src/main/java/ (Java)
│   ├── Services/
│   ├── Data/
│   └── Program.cs / Application.java
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

## 5. Agent Strategy for Modernization

Participants work with **three distinct agent roles**:

### 1. 🔍 Analysis Agent
- Understands the legacy codebase
- Identifies architectural smells
- Surfaces technical debt and outdated patterns

### 2. 🔄 Modernization Agent
- Applies modernization goals consistently
- Enforces target framework constraints
- Produces explainable, reviewable output

### 3. ✅ Review Agent
- Validates modernization against goals
- Identifies regressions or risks
- Ensures enterprise-safe patterns

> Agents are defined via **clear instructions**, not SDKs.

---

## 6. Agenda & Flow (2.5 - 3 Hours)

### 1. Introduction: Why Modernization Needs Agents ⏱️ _10 minutes_

**Why legacy modernization often fails:**
- Inconsistent refactoring decisions
- Loss of business logic during rewrites
- Scope creep and big-bang failures

**How agents help:**
- Consistent application of rules
- Explainable, reviewable changes
- Incremental, safe modernization

#### Flow Overview
```
Analyze → Define Goals → Create Agent → Modernize → Validate
```

**✅ Outcome:** Shared understanding of agent-driven modernization.

---

### 2. Lab 1: Understand the Legacy Application ⏱️ _25 minutes_

**Goal:** Build a shared understanding of the current state.

**Participants:**

- Review the legacy .NET/Java application
- Use Copilot Chat to:
  - Identify architectural smells
  - Highlight outdated patterns
  - Surface technical debt

**Artifacts updated:**

- `modernization/current-state.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 1.1 | Identify 5+ architectural smells in the legacy code | 🟢 Core | 10 |
| 1.2 | Document 3+ deprecated APIs or patterns in use | 🟢 Core | 10 |
| 1.3 | Create technical debt heatmap (high/medium/low areas) | 🟡 Challenge | 15 |
| 1.4 | Calculate modernization complexity score with justification | 🔴 Bonus | 20 |

**✅ Outcome:** Documented baseline of the existing system.

---

### 3. Lab 2: Define Modernization Goals & Constraints ⏱️ _20 minutes_

**Goal:** Make modernization intent explicit.

**Participants:**

- Define target outcomes (e.g., .NET 8, Java 17, architecture style)
- Capture constraints (time, scope, dependencies)
- Clarify what will *not* be modernized

**Artifacts updated:**

- `modernization/modernization-goals.md`
- `modernization/constraints.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 2.1 | Define 3+ measurable modernization success criteria | 🟢 Core | 10 |
| 2.2 | Identify 3+ hard constraints that cannot be violated | 🟢 Core | 10 |
| 2.3 | Create prioritized modernization roadmap (phases) | 🟡 Challenge | 15 |
| 2.4 | Define rollback strategy for each modernization phase | 🔴 Bonus | 20 |

**✅ Outcome:** Clear modernization boundaries for the agent.

---

### 4. Lab 3: Create a Custom Modernization Agent ⏱️ _30 minutes_

**Goal:** Build a purpose-driven agent for modernization.

**Participants:**

- Define agent responsibilities:
  - Code analysis
  - Refactoring guidance
  - Pattern enforcement
- Specify tone, constraints, and success criteria
- Store agent definition in:
  - `agents/modernization-agent.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 3.1 | Define 5+ specific modernization rules for the agent | 🟢 Core | 10 |
| 3.2 | Include error handling and edge case instructions | 🟢 Core | 10 |
| 3.3 | Add framework-specific transformation patterns | 🟡 Challenge | 15 |
| 3.4 | Create agent self-validation checklist | 🟡 Challenge | 15 |
| 3.5 | Build versioned agent with upgrade path | 🔴 Bonus | 25 |

**✅ Outcome:** A reusable, domain-specific modernization agent.

---

### 5. Lab 4: Apply the Agent to Modernize the Application ⏱️ _40 minutes_

**Goal:** Perform guided modernization using the custom agent.

**Participants:**

- Use the agent to:
  - Refactor selected components
  - Modernize APIs and patterns
  - Improve structure and readability
- Implement changes in:
  - `src-modernized/`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 4.1 | Modernize 2+ service classes using the agent | 🟢 Core | 15 |
| 4.2 | Update deprecated API calls to modern equivalents | 🟢 Core | 10 |
| 4.3 | Convert synchronous code to async/await patterns | 🟡 Challenge | 20 |
| 4.4 | Modernize dependency injection patterns | 🟡 Challenge | 15 |
| 4.5 | Implement strangler fig pattern for gradual migration | 🔴 Bonus | 30 |

**✅ Outcome:** Partially modernized application aligned with stated goals.

---

### 6. Lab 5: Validate & Review with a Secondary Agent ⏱️ _20 minutes_

**Goal:** Ensure modernization quality and alignment.

**Participants:**

- Use a review agent to:
  - Compare legacy vs modernized code
  - Validate alignment with goals and constraints
  - Identify risks or regressions

**Artifacts updated:**

- Inline comments or `validation.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 5.1 | Create before/after comparison for 3+ components | 🟢 Core | 10 |
| 5.2 | Verify business logic preservation with test cases | 🟡 Challenge | 15 |
| 5.3 | Identify 2+ potential regressions and mitigation plans | 🟡 Challenge | 15 |
| 5.4 | Generate automated regression test suite | 🔴 Bonus | 25 |

**✅ Outcome:** Increased confidence in modernization decisions.

---

## 7. Technology-Specific Patterns

### .NET Modernization Targets

| Legacy Pattern | Modern Target |
|----------------|---------------|
| .NET Framework 4.x | .NET 8+ |
| Web Forms | Blazor / Razor Pages |
| WCF Services | gRPC / REST APIs |
| Entity Framework 6 | EF Core 8 |
| Synchronous code | async/await patterns |

### Java Modernization Targets

| Legacy Pattern | Modern Target |
|----------------|---------------|
| Java 8 | Java 17/21 |
| Spring Boot 2.x | Spring Boot 3.x |
| JAX-RS | Spring WebFlux |
| Servlet-based | Reactive patterns |
| Synchronous JDBC | R2DBC / Virtual Threads |

---

## 8. MCP Context Model (Conceptual)

For modernization, shared context includes:

| Context Element | Purpose |
|-----------------|---------|
| Current State | Legacy architecture and patterns |
| Target State | Desired modern architecture |
| Constraints | What cannot change |
| Modernization Goals | Specific outcomes expected |
| Migration Patterns | Approved transformation rules |

> MCP is presented conceptually—participants capture context in markdown artifacts.

---

## 9. Success Criteria

By the end of this workshop, participants will have:

- [ ] Analyzed and documented a legacy application
- [ ] Defined explicit modernization goals and constraints
- [ ] Created a custom modernization agent
- [ ] Applied the agent to modernize selected components
- [ ] Validated changes against original goals
- [ ] Understood incremental modernization patterns

---

## 10. Scoring & Achievement Levels

### Point Breakdown

| Category | Points Available |
|----------|------------------|
| 🟢 Core Challenges | 95 points |
| 🟡 Challenge Tasks | 110 points |
| 🔴 Bonus Tasks | 120 points |
| **Total Possible** | **325 points** |

### Achievement Levels

| Level | Points | Badge |
|-------|--------|-------|
| 🥇 **Modernization Master** | 275+ | Expert-level migration skills |
| 🥈 **Transformation Lead** | 195-274 | Strong modernization execution |
| 🥉 **Migration Specialist** | 115-194 | Solid foundational understanding |
| **Participant** | <115 | Completed core workshop activities |

### Time Bonuses

| Completion Time | Bonus |
|-----------------|-------|
| Under 2 hours | +30 points |
| Under 2.5 hours | +15 points |

---

## Appendix: Starter Prompts

### Analysis Prompt
```
Analyze this legacy application and identify:

1. Architectural patterns in use
2. Outdated practices or dependencies
3. Technical debt hotspots
4. Components that would benefit from modernization

Prioritize findings by modernization impact.
```

### Goals Definition Prompt
```
Help me define modernization goals for this application:

Current state: [summary]
Business drivers: [why modernize]

Define:
1. Target framework/runtime version
2. Architecture style goals
3. Specific patterns to adopt
4. What is explicitly out of scope
```

### Modernization Agent Prompt
```
You are a modernization agent for [.NET/.Java] applications.

Your responsibilities:
1. Analyze legacy code and suggest modern equivalents
2. Apply these modernization rules: [rules]
3. Enforce these constraints: [constraints]
4. Explain your reasoning for each change

Target state: [target description]

When modernizing code:
- Prefer incremental changes over rewrites
- Preserve business logic exactly
- Flag risky changes for human review
```

### Modernization Prompt
```
Modernize this component according to our goals:

[Code snippet]

Apply these changes:
1. Update to target framework patterns
2. Replace deprecated APIs
3. Improve structure where safe
4. Add comments explaining changes

Do NOT change: [exclusions]
```

### Validation Prompt
```
Compare this modernized code against the original:

Original: [legacy code]
Modernized: [new code]

Verify:
1. Business logic is preserved
2. Modernization goals are met
3. No regressions introduced
4. Constraints are respected

Flag any concerns.
```


