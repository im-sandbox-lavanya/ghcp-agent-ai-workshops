# Workshop 4: Testing with Agents

> _Custom Playwright Agents, Copilot Chat, MCP Concepts_

---

## Overview

- **Duration:** 2 hours  
- **Format:** Instructor-led, guided hands-on workshop  
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
- SDK-based agent orchestration (too heavy for 2 hours)
- Full Playwright framework walkthroughs

This keeps the workshop focused on **how agents improve testing decisions**, not tooling complexity.

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

## 6. Agenda & Flow (2 Hours)

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

---
**Participants:**
- Review the application behavior
- Use Copilot Chat to:
  - Identify critical user journeys
  - Separate core flows from edge cases

**Artifact Updated:** `testing/test-scope.md`

**✅ Outcome:** Clear agreement on _what matters to test_.

---

### 3. Lab 2: Generate Test Scenarios with an Agent ⏱️ _20 minutes_

**Goal:** Move from behavior to test scenarios.

**Participants:**
- Use the **Test Design Agent** to:
  - Generate positive and negative scenarios
  - Identify boundary conditions
- Capture scenarios explicitly

**Artifact Updated:** `testing/scenarios.md`

**✅ Outcome:** Well-defined, human-readable test scenarios.

---

### 4. Lab 3: Create a Custom Playwright Agent ⏱️ _25 minutes_

**Goal:** Build a reusable agent for Playwright test generation.

**Participants define an agent that:**
- Uses agreed selectors and patterns
- Avoids brittle waits
- Produces readable, maintainable tests
- Follows project conventions

**Agent Defined In:** `agents/playwright-agent.md`

**✅ Outcome:** A purpose-built Playwright test agent.

---

### 5. Lab 4: Generate Playwright Tests ⏱️ _25 minutes_

**Goal:** Convert scenarios into automated tests.

**Participants:**
- Use the Playwright Agent to:
  - Generate tests for selected scenarios
  - Add assertions and validations
- Place tests under: `playwright/tests/`

**✅ Outcome:** Working Playwright tests aligned to intent.

