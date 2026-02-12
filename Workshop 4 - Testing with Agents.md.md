# Workshop 4: Testing with Agents

> _Custom Playwright Agents, Copilot Chat, MCP Concepts_

---

## Overview

- **Duration:** 2.5 - 3 hours  
- **Format:** Instructor-led, guided hands-on workshop  
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

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Explore the application** (3 min)
```
Open app-under-test/ and:
- Read README.md for app overview
- Identify the main features
- Run the app locally if time permits
```

**Step 2: Identify user journeys with Copilot** (5 min)

Open Copilot Chat with app files:

```
Analyze @app-under-test and identify:

1. The critical user journeys (what users MUST be able to do)
2. Important flows (valuable but not critical)
3. Nice-to-have features (low priority for testing)

For each journey, describe:
- Entry point
- Key steps
- Expected outcome
- What could go wrong
```

✅ **Expected Output:** List of 5-10 user journeys with priority levels.

**Step 3: Assess testing risk** (5 min)

Use this prompt:

```
For the user journeys identified, assess testing risk:

1. Which involve complex logic?
2. Which handle money/sensitive data?
3. Which have many state transitions?
4. Which interact with external systems?

Create a risk assessment table:
| Journey | Complexity | Data Sensitivity | External Deps | Risk Level |
```

**Step 4: Create test scope** (5 min)

Use this prompt:

```
Based on the journeys and risk assessment, recommend:

1. MUST test (high risk, high value)
2. SHOULD test (medium risk or value)
3. COULD test (nice to have)
4. WON'T test (low value, high cost)

Explain the reasoning for each category.
```

**Step 5: Document in test-scope.md** (2 min)
- Copy prioritized journeys to `testing/test-scope.md`
- Note the risk assessment
- Document exclusions and why

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 1.1 (5+ journeys) | Think: login, main feature, edge features, errors |
| 1.2 (categorize) | Ask: "What if this breaks in production?" |
| 1.3 (high-risk) | Complex code + external deps = risk |
| 1.4 (priority matrix) | Risk × Business Value = Priority |

---

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

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Select journey to test** (2 min)
```
From test-scope.md, pick the highest priority journey.
Example: "User login and authentication"
```

**Step 2: Generate happy path scenarios** (8 min)

Open Copilot Chat:

```
For this user journey: [paste journey]

Generate happy path test scenarios in Given-When-Then format:

**Scenario 1: [Name]**
- Given: [preconditions]
- When: [user actions]
- Then: [expected results]

Include:
- Main success scenario
- Variations (different valid inputs)
- Different user types if applicable
```

✅ **Expected Output:** 3+ happy path scenarios in Gherkin-style format.

**Step 3: Generate negative scenarios** (7 min)

Use this prompt:

```
For the same journey, generate negative/error test scenarios:

1. Invalid input scenarios
2. Unauthorized access attempts
3. Service unavailable scenarios
4. Timeout scenarios
5. Concurrent operation conflicts

For each:
- Given: [setup that creates error condition]
- When: [user action]
- Then: [expected error handling]
```

**Step 4: Identify boundary conditions** (5 min)

Use this prompt:

```
Identify boundary conditions and edge cases:

1. Minimum/maximum input values
2. Empty vs null vs whitespace
3. Special characters and encoding
4. First/last items in lists
5. Pagination boundaries
6. Session/token expiration edges

For each boundary, specify the test scenario.
```

**Step 5: Document scenarios** (3 min)
- Copy all scenarios to `testing/scenarios.md`
- Group by: Happy Path, Negative, Boundary
- Add test priority for each

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 2.1 (happy paths) | Think: different valid inputs, user types |
| 2.2 (negative) | What happens when things go wrong? |
| 2.3 (boundaries) | 0, 1, max-1, max, max+1 |
| 2.4 (data-driven) | Same test, different data combinations |
| 2.5 (cross-browser) | Chrome, Firefox, Safari × Mobile, Desktop |

---

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

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Create agent file** (2 min)
```
Create agents/playwright-agent.md with basic structure
```

**Step 2: Define agent identity** (5 min)

Add to your agent file:

```markdown
# Playwright Test Generation Agent

## Identity
You are a Playwright testing expert who generates reliable,
maintainable end-to-end tests.

## Your Values
1. Test reliability over test speed
2. Readability over cleverness
3. Maintainability over coverage count
4. Explicit waits over arbitrary delays
```

**Step 3: Define selector strategy** (8 min)

Use Copilot to generate selector rules:

```
Generate a selector strategy for Playwright tests:

Priority order:
1. data-testid (most reliable)
2. ARIA roles (accessible)
3. Text content (visible to users)
4. CSS selectors (last resort)

For each strategy, provide:
- When to use it
- Example code
- Why it's reliable (or not)

Include anti-patterns to avoid.
```

✅ **Expected Output:** Complete selector strategy with examples.

**Step 4: Add waiting patterns** (5 min)

Add this to your agent:

```markdown
## Waiting Patterns

### ✅ DO
```typescript
await page.waitForSelector('[data-testid="loaded"]');
await expect(page.locator('.result')).toBeVisible();
await page.waitForResponse('**/api/data');
```

### ❌ DON'T
```typescript
await page.waitForTimeout(3000); // NEVER use arbitrary waits
```
```

**Step 5: Add test structure patterns** (5 min)

Use this prompt:

```
Generate Playwright test structure patterns:

1. Page Object Model example
2. Fixture usage pattern
3. Test isolation approach
4. Shared setup/teardown
5. Error handling in tests

Include code examples for each.
```

**Step 6: Add conventions** (5 min)

Add naming and structure conventions:

```markdown
## Conventions

### File Naming
- Feature tests: `{feature}.spec.ts`
- Integration: `{integration}.e2e.ts`

### Test Naming
```typescript
test('should [action] when [condition]', async () => {
```

### Assertions
- One logical assertion per test step
- Use `expect` with descriptive matchers
```

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 3.1 (selector strategy) | data-testid → role → text → CSS |
| 3.2 (anti-patterns) | No arbitrary waits, no magic numbers |
| 3.3 (error handling) | try/catch + screenshot on failure |
| 3.4 (page objects) | One PO per page/component |
| 3.5 (action library) | login(), addToCart(), checkout() |

---

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

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Review scenarios and agent** (3 min)
```
Open:
- testing/scenarios.md (what to test)
- agents/playwright-agent.md (how to test)
```

**Step 2: Generate first test** (10 min)

Open Copilot Chat with both files:

```
Using @playwright-agent.md conventions, generate a Playwright test for:

**Scenario:** [paste your first happy path scenario]

Requirements:
1. Follow the selector strategy defined
2. Use proper waiting patterns
3. Include meaningful assertions
4. Add descriptive test name
5. Handle potential errors

Target file: playwright/tests/[feature].spec.ts
```

✅ **Expected Output:** Complete, runnable Playwright test file.

**Step 3: Generate negative test** (8 min)

Use this prompt:

```
Generate a test for this error scenario:

**Scenario:** [paste negative scenario]

The test should:
1. Set up the error condition
2. Perform the action
3. Assert the error is handled correctly
4. Verify no data corruption occurred
```

**Step 4: Add multiple assertions** (7 min)

Use this prompt:

```
Enhance this test with comprehensive assertions:

[paste your generated test]

Add assertions for:
1. Page load success indicators
2. Form state validation
3. API response verification
4. UI feedback elements
5. Final state confirmation
```

**Step 5: Create parameterized test** (5 min)

Use this prompt:

```
Convert this test to be data-driven:

[paste test]

Test data variations:
- Valid input 1
- Valid input 2 (different format)
- Edge case input

Use Playwright's parameterized test pattern.
```

**Step 6: Save tests** (2 min)
- Save generated tests to `playwright/tests/`
- Organize by feature
- Run one test to verify it works

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 4.1 (happy path) | Follow the scenario exactly |
| 4.2 (negative) | Setup → Action → Assert Error |
| 4.3 (multiple assertions) | Assert at each meaningful step |
| 4.4 (parameterized) | Use `test.describe.each` or similar |
| 4.5 (visual) | `await expect(page).toHaveScreenshot()` |

---

#### ⚠️ Common Pitfalls

- ❌ **Arbitrary waits:** Use `waitForSelector`, not `waitForTimeout`
- ❌ **Flaky selectors:** Prefer data-testid over dynamic classes
- ❌ **Missing assertions:** Every action should verify something

---

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

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Create coverage matrix** (5 min)

Open Copilot Chat:

```
Create a coverage matrix comparing:

Scenarios from @scenarios.md
vs.
Tests in @playwright/tests/

| Scenario | Test File | Coverage Status |
|----------|-----------|----------------|
| [name]   | [file]    | ✅ Covered / ❌ Missing / ⚠️ Partial |

Identify any coverage gaps.
```

✅ **Expected Output:** Coverage matrix showing gaps.

**Step 2: Review tests for flakiness** (7 min)

Use this prompt:

```
Review these Playwright tests for flakiness risks:

@playwright/tests/

Check for:
1. Arbitrary waits (waitForTimeout)
2. Unreliable selectors (nth-child, dynamic classes)
3. Race conditions (actions without waiting)
4. Network timing assumptions
5. State leakage between tests

For each issue found, suggest the fix.
```

**Step 3: Fix identified issues** (5 min)

For each flaky pattern found:

```
Refactor this test to be more reliable:

[paste problematic test code]

Specific issue: [flakiness pattern]

Apply the fix following @playwright-agent.md patterns.
```

**Step 4: Add retry and error handling** (3 min)

Use this prompt:

```
Add proper retry and error handling to this test:

[paste test]

Include:
1. Retry for flaky network operations
2. Screenshot on failure
3. Cleanup in finally block
4. Meaningful error messages
```

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 5.1 (coverage matrix) | Compare scenarios.md to test files |
| 5.2 (flaky patterns) | Search for: waitForTimeout, nth-child |
| 5.3 (retry logic) | Use `test.retry()` or custom retry wrapper |
| 5.4 (reporter) | Playwright built-in reporters + custom |

---

#### ⚠️ Common Pitfalls

- ❌ **100% coverage obsession:** Quality over quantity
- ❌ **Ignoring flakiness:** One flaky test ruins CI trust
- ❌ **No maintenance plan:** Tests need regular review

---

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

