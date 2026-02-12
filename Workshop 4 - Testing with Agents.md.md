# Workshop 4: Testing with Agents

> _Custom Playwright Agents, Copilot Chat, MCP Concepts_

---

## Overview

- **Duration:** 2.5 - 3 hours  
- **Format:** Instructor-led, challenge-based workshop  
- **Difficulty:** 🟡 Intermediate to 🔴 Advanced  
- **Audience:** Developers, QA Engineers, SDETs, Tech Leads  
- **Focus:** Using AI agents to design, generate, and maintain automated tests with Playwright

---

## 1. Workshop Purpose

This workshop shows how **AI agents can be applied to testing**, not just to generate test code, but to:

*   Understand application behavior
*   Derive meaningful test scenarios
*   Generate maintainable Playwright tests
*   Reduce brittle, low-value automation
---

## 2. Design Principles

- Test intent before test code
- Agents assist testers; they don't replace judgment
- Fewer, meaningful tests over exhaustive scripts
- Maintainability over one-off generation
- Testing as a first-class engineering activity

---

## 3. Scope Decisions (Intentional)

### ✅ Included

- Copilot Chat for reasoning and test generation
- Custom Playwright agents (instruction-based)
- Structured test artifacts
- MCP as a **conceptual model** for shared context

### ❌ Excluded

- Copilot CLI (adds little value for UI testing)
- SDK-based agent orchestration
- Full Playwright framework walkthroughs

This keeps the workshop focused on **how agents improve testing decisions**, not tooling complexity.

---

## Difficulty & Challenge Levels

| Level | Description | Time Pressure |
|-------|-------------|---------------|
| 🟢 **Core** | Must complete - foundational skills | Guided pace |
| 🟡 **Challenge** | Stretch goals - deeper understanding | Time-boxed |
| 🔴 **Bonus** | Expert level - independent problem solving | Self-paced |

---

## 4. Pre-Provisioned Repository

Participants receive a repository containing a **working web application**, Playwright setup, and scaffolding for agent-driven testing.

```
/workshop-repo
├── app-under-test/
│   ├── src/
│   ├── routes/
│   └── README.md
│
├── testing/
│   ├── test-scope.md
│   ├── scenarios.md
│   └── coverage-gaps.md
│
├── playwright/
│   ├── tests/
│   │   └── starter.spec.ts
│   ├── playwright.config.ts
│   └── README.md
│
├── agents/
│   ├── test-design-agent.md
│   ├── playwright-agent.md
│   └── review-agent.md
│
├── prompts/
│   ├── scenario-generation.md
│   ├── test-generation.md
│   └── test-review.md
│
└── README.md
```

> **Note:** All documents are intentionally **partially filled** to guide participants.

---

## 5. Agent Strategy for Testing

Participants work with **three distinct agent roles**:

### 1. 🎯 Test Design Agent
- Understands application behavior
- Identifies test scenarios and edge cases

### 2. 🤖 Playwright Agent
- Generates Playwright tests
- Follows agreed patterns and constraints

### 3. ✅ Review Agent
- Evaluates test quality
- Identifies flakiness and gaps

> Agents are defined via **clear instructions**, not SDKs.

---

## 6. Agenda & Flow (2.5 - 3 Hours)

### 1. Introduction: Why Testing Needs Agents ⏱️ _10 minutes_

**Why test automation often fails:**
- Too many brittle tests
- Poor coverage decisions
- High maintenance cost

**How agents help:**
- Make intent explicit
- Improve test quality
- Reduce noise

#### Flow Overview
```
Understand → Decide → Generate → Review → Improve
```

**✅ Outcome:** Shared understanding of agent-driven testing.

---

### 2. Lab 1: Understand the Application ⏱️ _20 minutes_

**Goal:** Build shared understanding of what needs testing.

**Participants:**
- Review the application behavior
- Use Copilot Chat to:
  - Identify critical user journeys
  - Separate core flows from edge cases

**Artifact Updated:** `testing/test-scope.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 1.1 | Identify 5+ critical user journeys | 🟢 Core | 10 |
| 1.2 | Categorize flows as Core/Important/Nice-to-have | 🟢 Core | 10 |
| 1.3 | Identify 3+ high-risk areas based on complexity | 🟡 Challenge | 15 |
| 1.4 | Create risk-based testing priority matrix | 🔴 Bonus | 20 |

**✅ Outcome:** Clear agreement on _what matters to test_.

---

### 3. Lab 2: Generate Test Scenarios with an Agent ⏱️ _25 minutes_

**Goal:** Move from behavior to test scenarios.

**Participants:**
- Use the **Test Design Agent** to:
  - Generate positive and negative scenarios
  - Identify boundary conditions
- Capture scenarios explicitly

**Artifact Updated:** `testing/scenarios.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 2.1 | Generate 3+ happy path scenarios for critical journey | 🟢 Core | 10 |
| 2.2 | Generate 3+ negative/error scenarios | 🟢 Core | 10 |
| 2.3 | Identify boundary conditions and edge cases | 🟡 Challenge | 15 |
| 2.4 | Create data-driven scenario variations | 🟡 Challenge | 15 |
| 2.5 | Design cross-browser/device test matrix | 🔴 Bonus | 20 |

**✅ Outcome:** Well-defined, human-readable test scenarios.

---

### 4. Lab 3: Create a Custom Playwright Agent ⏱️ _30 minutes_

**Goal:** Build a reusable agent for Playwright test generation.

**Participants define an agent that:**
- Uses agreed selectors and patterns
- Avoids brittle waits
- Produces readable, maintainable tests
- Follows project conventions

**Agent Defined In:** `agents/playwright-agent.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 3.1 | Define selector strategy (data-testid > role > CSS) | 🟢 Core | 10 |
| 3.2 | Include anti-patterns to avoid (brittle waits, etc.) | 🟢 Core | 10 |
| 3.3 | Add error handling and retry patterns | 🟡 Challenge | 15 |
| 3.4 | Include page object model patterns | 🟡 Challenge | 15 |
| 3.5 | Create reusable custom action library | 🔴 Bonus | 25 |

**✅ Outcome:** A purpose-built Playwright test agent.

---

### 5. Lab 4: Generate Playwright Tests ⏱️ _35 minutes_

**Goal:** Convert scenarios into automated tests.

**Participants:**
- Use the Playwright Agent to:
  - Generate tests for selected scenarios
  - Add assertions and validations
- Place tests under: `playwright/tests/`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 4.1 | Generate working test for happy path scenario | 🟢 Core | 15 |
| 4.2 | Generate test for error/negative scenario | 🟢 Core | 10 |
| 4.3 | Implement test with multiple assertions | 🟡 Challenge | 15 |
| 4.4 | Create parameterized/data-driven test | 🟡 Challenge | 20 |
| 4.5 | Implement visual regression test | 🔴 Bonus | 25 |

**✅ Outcome:** Working Playwright tests aligned to intent.

---

### 6. Lab 5: Review and Improve Tests ⏱️ _20 minutes_

**Goal:** Ensure test quality and maintainability.

**Participants:**
- Use the **Review Agent** to:
  - Evaluate test coverage against scenarios
  - Identify flaky patterns
  - Suggest improvements

**Artifact Updated:** `testing/coverage-gaps.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 5.1 | Create coverage matrix: scenarios vs tests | 🟢 Core | 10 |
| 5.2 | Identify and fix 2+ flaky patterns | 🟡 Challenge | 15 |
| 5.3 | Add retry logic for network-dependent tests | 🟡 Challenge | 15 |
| 5.4 | Implement test reporter with custom metrics | 🔴 Bonus | 25 |

**✅ Outcome:** Reviewed tests with identified improvements.

---

### 7. Wrap-Up: Building a Testing Playbook ⏱️ _10 minutes_

**Discussion:**
- How to institutionalize agent-driven testing
- Building team testing playbooks
- Integrating with CI/CD pipelines

**Takeaways:**
- Intent-first testing > code-first testing
- Agents assist judgment, not replace it
- Fewer meaningful tests > many brittle tests

---

## 7. MCP Context Model (Conceptual)

For testing, shared context includes:

| Context Element | Purpose |
|-----------------|---------|
| Application Behavior | What the app does |
| Test Scope | What matters to test |
| Scenarios | Expected behaviors to validate |
| Selector Patterns | Agreed UI element targeting |
| Conventions | Test naming and structure rules |

> MCP is presented conceptually—participants capture context in markdown artifacts.

---

## 8. Success Criteria

By the end of this workshop, participants will have:

- [ ] Identified critical user journeys for testing
- [ ] Generated structured test scenarios
- [ ] Created a custom Playwright test agent
- [ ] Generated maintainable Playwright tests
- [ ] Reviewed tests for quality and coverage
- [ ] Understood intent-first testing methodology

---

## 9. Scoring & Achievement Levels

### Point Breakdown

| Category | Points Available |
|----------|------------------|
| 🟢 Core Challenges | 95 points |
| 🟡 Challenge Tasks | 125 points |
| 🔴 Bonus Tasks | 115 points |
| **Total Possible** | **335 points** |

### Achievement Levels

| Level | Points | Badge |
|-------|--------|-------|
| 🥇 **Test Architect** | 280+ | Elite testing skills |
| 🥈 **Quality Champion** | 200-279 | Strong test design abilities |
| 🥉 **Test Builder** | 120-199 | Solid foundational understanding |
| **Participant** | <120 | Completed core workshop activities |

### Time Bonuses

| Completion Time | Bonus |
|-----------------|-------|
| Under 2 hours | +30 points |
| Under 2.5 hours | +15 points |

---

## Appendix: Starter Prompts

### Test Scope Prompt
```
Analyze this application and identify:

1. Critical user journeys that must be tested
2. Core flows vs. edge cases
3. High-risk areas that need coverage
4. What can be safely excluded from automation

Prioritize by business impact.
```

### Scenario Generation Prompt
```
For this user journey:

[Journey description]

Generate test scenarios including:
1. Happy path scenarios
2. Negative/error scenarios
3. Boundary conditions
4. Edge cases

Format each scenario with:
- Given (preconditions)
- When (actions)
- Then (expected results)
```

### Playwright Agent Definition Prompt
```
You are a Playwright test generation agent.

Your responsibilities:
1. Generate tests following these patterns: [patterns]
2. Use these selector strategies: [selectors]
3. Avoid these anti-patterns: [anti-patterns]
4. Follow project conventions: [conventions]

When generating tests:
- Prefer data-testid selectors over CSS
- Use explicit waits, avoid arbitrary delays
- Include clear assertions for each step
- Make tests readable and maintainable
```

### Test Generation Prompt
```
Generate a Playwright test for this scenario:

[Scenario]

Follow these requirements:
1. Use our selector patterns
2. Include proper assertions
3. Handle async operations correctly
4. Add descriptive test names

Target file: playwright/tests/[feature].spec.ts
```

### Test Review Prompt
```
Review this Playwright test:

[Test code]

Evaluate:
1. Coverage of the intended scenario
2. Selector reliability (flakiness risk)
3. Assertion completeness
4. Maintainability
5. Adherence to conventions

Suggest specific improvements.
```

