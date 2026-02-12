# Workshop 3: Debugging with Agents

> _Copilot CLI, SDK, MCP Concepts, Custom Agents_

---

## Overview

- **Duration:** 2.5 - 3 hours  
- **Format:** Instructor-led, guided hands-on workshop  
- **Difficulty:** 🟡 Intermediate to 🔴 Advanced  
- **Audience:** Developers, Tech Leads, SREs, Support Engineers  
- **Focus:** Using AI agents to systematically diagnose, debug, and resolve application issues

---

## 1. Workshop Purpose

This workshop demonstrates how **AI agents can transform debugging** from ad-hoc investigation to a **structured, repeatable process**.

Participants will learn to:

- Use agents to analyze error patterns and stack traces
- Systematically identify root causes
- Generate targeted fixes with confidence
- Build reusable debugging workflows

The emphasis is on **structured debugging methodology**, not random prompt experimentation.

---

## 2. Design Principles

- Root cause before fix
- Structured investigation over guesswork
- Custom agents for domain-specific debugging
- Evidence-based diagnosis
- Minimal, targeted changes over shotgun fixes
- Reproducibility and documentation

---

## 3. Scope Decisions (Intentional)

### ✅ Included

- Copilot Chat for interactive debugging
- Copilot CLI for terminal-based analysis
- Custom debugging agents (instruction-based)
- MCP as a **conceptual model** for shared debugging context
- Structured error analysis artifacts

### ❌ Excluded

- Full SDK orchestration (too complex for workshop)
- Production monitoring setup
- Infrastructure debugging
- Performance profiling deep-dives

This keeps the workshop focused on **how agents improve debugging decisions**, not tooling complexity.

---

## Difficulty & Challenge Levels

| Level | Description | Time Pressure |
|-------|-------------|---------------|
| 🟢 **Core** | Must complete - foundational skills | Guided pace |
| 🟡 **Challenge** | Stretch goals - deeper understanding | Time-boxed |
| 🔴 **Bonus** | Expert level - independent problem solving | Self-paced |

---

## 4. Pre-Provisioned Repository

Participants receive a repository containing a **buggy application**, error logs, and scaffolding for agent-driven debugging.

```
/workshop-repo
├── buggy-app/
│   ├── src/
│   │   ├── api/
│   │   ├── services/
│   │   ├── utils/
│   │   └── index.ts
│   ├── tests/
│   └── README.md
│
├── debugging/
│   ├── error-catalog.md
│   ├── investigation-log.md
│   ├── root-cause-analysis.md
│   └── fix-validation.md
│
├── logs/
│   ├── error-logs.txt
│   ├── stack-traces.md
│   └── reproduction-steps.md
│
├── agents/
│   ├── triage-agent.md
│   ├── diagnosis-agent.md
│   ├── fix-agent.md
│   └── validation-agent.md
│
├── prompts/
│   ├── error-analysis.md
│   ├── root-cause.md
│   ├── fix-generation.md
│   └── regression-check.md
│
└── README.md
```

> **Note:** The application contains **intentional bugs** of varying complexity. All documents are partially filled to guide participants.

---

## 5. Agent Strategy for Debugging

Participants work with **four distinct agent roles**:

### 1. 🚨 Triage Agent
- Categorizes and prioritizes errors
- Identifies patterns across failures
- Determines investigation order

### 2. 🔍 Diagnosis Agent
- Analyzes stack traces and error messages
- Traces code paths to identify root causes
- Documents findings with evidence

### 3. 🔧 Fix Agent
- Generates targeted fixes
- Follows minimal-change principles
- Explains reasoning behind fixes

### 4. ✅ Validation Agent
- Verifies fixes resolve the issue
- Checks for regressions
- Documents test coverage

> Agents are defined via **clear instructions**, not SDKs.

---

## 6. Copilot CLI Integration

This workshop introduces **Copilot CLI** for terminal-based debugging:

### Key CLI Patterns

```bash
# Explain an error
gh copilot explain "error message or stack trace"

# Suggest a fix
gh copilot suggest "how to fix null reference in UserService"

# Analyze logs
gh copilot explain < error-logs.txt
```

### When to Use CLI vs Chat

| Use Case | CLI | Chat |
|----------|-----|------|
| Quick error explanation | ✅ | |
| Log analysis | ✅ | |
| Interactive investigation | | ✅ |
| Multi-file debugging | | ✅ |
| Complex reasoning | | ✅ |

---

## 7. Agenda & Flow (2.5 - 3 Hours)

### 1. Introduction: Why Debugging Needs Agents ⏱️ _10 minutes_

**Why traditional debugging often fails:**
- Jumping to conclusions without evidence
- Missing the root cause, fixing symptoms
- Lack of structured investigation
- Knowledge loss after each incident

**How agents help:**
- Systematic error analysis
- Evidence-based diagnosis
- Documented investigation trails
- Reusable debugging patterns

#### Flow Overview
```
Triage → Diagnose → Fix → Validate → Document
```

**✅ Outcome:** Shared understanding of agent-driven debugging.

---

### 2. Lab 1: Triage and Categorize Errors ⏱️ _20 minutes_

**Goal:** Understand and prioritize the errors in the application.

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Review the error logs** (3 min)
```
Open these files:
- logs/error-logs.txt
- logs/stack-traces.md
- logs/reproduction-steps.md
```

**Step 2: Categorize errors using Copilot CLI** (5 min)

In terminal, run:

```bash
gh copilot explain "Analyze these errors and categorize them:
$(cat logs/error-logs.txt)

Categories to use:
- Runtime errors (null refs, type errors)
- Logic errors (wrong output, incorrect flow)
- Integration errors (API, database, external)
- Configuration errors (missing config, wrong env)"
```

**Step 3: Assign severity using Copilot Chat** (5 min)

Open Copilot Chat and use this prompt:

```
For each error in @error-logs.txt, assign severity:

| Error | Category | Severity | Impact | Investigation Priority |

Severity criteria:
- CRITICAL: System down, data loss risk
- HIGH: Major feature broken, workaround difficult
- MEDIUM: Feature degraded, workaround exists
- LOW: Minor issue, cosmetic, edge case
```

✅ **Expected Output:** A prioritized table of all errors.

**Step 4: Identify error patterns** (5 min)

Use this prompt:

```
Look for patterns across these errors:

1. Errors that occur together
2. Errors with similar stack traces
3. Errors that might share a root cause
4. Errors that might be causing other errors (cascading)

Group related errors and explain why they might be connected.
```

**Step 5: Document in error catalog** (2 min)
- Copy categorized errors to `debugging/error-catalog.md`
- Note the investigation priority order
- Highlight suspected root causes

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 1.1 (4+ categories) | Think: runtime, logic, integration, config, security |
| 1.2 (severity) | Ask: "What happens if we ignore this for a week?" |
| 1.3 (patterns) | Look for repeated class names or error codes |
| 1.4 (cascading) | Error A causes state that triggers Error B |

---

**Artifact Updated:** `debugging/error-catalog.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 1.1 | Categorize all errors into 4+ distinct categories | 🟢 Core | 10 |
| 1.2 | Assign severity (Critical/High/Medium/Low) to each error | 🟢 Core | 10 |
| 1.3 | Identify 2+ error patterns that suggest common root cause | 🟡 Challenge | 15 |
| 1.4 | Predict cascading failures from the error patterns | 🔴 Bonus | 20 |

**✅ Outcome:** Prioritized list of errors with initial categorization.

---

### 3. Lab 2: Create a Custom Diagnosis Agent ⏱️ _25 minutes_

**Goal:** Build a purpose-driven agent for root cause analysis.

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Create agent file** (2 min)
```
Create agents/diagnosis-agent.md with basic structure:
```

**Step 2: Define agent identity** (5 min)

Add this to your agent file:

```markdown
# Diagnosis Agent

## Identity
You are a debugging expert specializing in root cause analysis.
You think systematically, gather evidence, and never guess.

## Your Approach
1. Understand the symptom completely first
2. Form hypotheses based on evidence
3. Test hypotheses by examining code
4. Document findings with proof
5. Rate confidence in your diagnosis

## You Must NOT
- Jump to conclusions without evidence
- Suggest fixes before confirming root cause
- Ignore related errors or warnings
```

**Step 3: Add diagnosis rules** (8 min)

Use Copilot Chat to generate rules:

```
Generate diagnosis rules for common bug patterns:

1. NullReferenceException diagnosis steps
2. Async/await deadlock diagnosis steps  
3. Race condition diagnosis steps
4. Memory leak diagnosis steps
5. Configuration error diagnosis steps

For each, provide:
- Symptoms to look for
- Evidence to gather
- Common causes
- Verification approach
```

✅ **Expected Output:** Detailed diagnosis procedures for each bug type.

**Step 4: Add evidence collection instructions** (5 min)

Add to your agent:

```markdown
## Evidence Collection

For every diagnosis, gather:
1. ✅ Exact error message and code
2. ✅ Full stack trace
3. ✅ Steps to reproduce
4. ✅ Related log entries (before/after)
5. ✅ Recent code changes
6. ✅ Environment details

## Confidence Scoring
- HIGH (90%+): Have reproduction + root cause in code
- MEDIUM (70-89%): Strong evidence, need verification
- LOW (<70%): Hypothesis only, needs more investigation
```

**Step 5: Add example diagnosis** (5 min)

Add a worked example:

```markdown
## Example Diagnosis

**Symptom:** "Cannot read property 'id' of undefined"

**Evidence:**
- Stack trace points to UserService.getProfile()
- Occurs when user parameter is null
- Recent change: removed null check in refactoring

**Root Cause:** Null check removed in commit abc123

**Confidence:** HIGH (90%) - can reproduce, see exact line
```

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 2.1 (5+ rules) | Think: null, async, race, memory, config |
| 2.2 (evidence) | "What would convince a skeptic?" |
| 2.3 (domain patterns) | Add patterns specific to your tech stack |
| 2.4 (confidence score) | Higher confidence = more evidence |

---

**Agent Defined In:** `agents/diagnosis-agent.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 2.1 | Define 5+ specific diagnosis rules for the agent | 🟢 Core | 10 |
| 2.2 | Include instructions for evidence collection | 🟢 Core | 10 |
| 2.3 | Add domain-specific debugging patterns (async, null refs, etc.) | 🟡 Challenge | 15 |
| 2.4 | Create confidence scoring system for diagnoses | 🔴 Bonus | 25 |

**✅ Outcome:** A reusable diagnosis agent for systematic debugging.

---

### 4. Lab 3: Investigate Root Causes ⏱️ _35 minutes_

**Goal:** Use the diagnosis agent to identify root causes.

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Select errors to investigate** (2 min)
```
From your error-catalog.md, select:
- The highest severity error
- One error that might be related to another
- One error that seems unusual
```

**Step 2: Investigate first error** (10 min)

Open Copilot Chat with your diagnosis agent and error logs:

```
Using @diagnosis-agent.md approach, diagnose this error:

Error: [paste exact error message]
Stack trace: [paste stack trace]

Follow these steps:
1. What is the immediate cause (what failed)?
2. Trace back - why did that value/state exist?
3. What code path led to this state?
4. What's the root cause (first thing that went wrong)?
5. Rate your confidence.
```

✅ **Expected Output:** Step-by-step diagnosis with evidence and confidence rating.

**Step 3: Find the hidden logic bug** (10 min)

Use this prompt:

```
Analyze @buggy-app for logic errors that wouldn't show in error logs:

1. Look for incorrect conditionals (off-by-one, wrong operator)
2. Look for missing edge cases (empty arrays, null inputs)
3. Look for incorrect calculations
4. Look for wrong return values

For each suspected bug:
- Location and line
- What's wrong
- What should it be
- How to verify
```

**Step 4: Hunt for race condition** (8 min)

Use this prompt:

```
Analyze the async code in @buggy-app for race conditions:

1. Shared state modified by multiple async operations
2. Operations that assume order but don't enforce it
3. Missing locks or synchronization
4. Callbacks that might fire in unexpected order

Explain the timing scenario that causes the bug.
```

**Step 5: Document findings** (5 min)
- Create root cause analysis entry for each bug
- Include evidence chain
- Rate confidence
- Note any remaining unknowns

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 3.1 (root cause) | Ask "Why?" 5 times to get to the root |
| 3.2 (evidence chain) | Symptom → Direct cause → Root cause |
| 3.3 (hidden bug) | Test with edge cases: 0, 1, empty, max |
| 3.4 (race condition) | Draw the timeline of concurrent operations |
| 3.5 (security vuln) | Look for: input not validated, SQL strings, auth gaps |

---

#### ⚠️ Common Pitfalls

- ❌ **Fixing symptoms:** Found where it fails, not why
- ❌ **Confirmation bias:** Seeing what you expect, not what's there
- ❌ **Incomplete trace:** Stopping before the real root cause

---

**Artifact Updated:** `debugging/root-cause-analysis.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 3.1 | Identify root cause for the highest-severity error | 🟢 Core | 15 |
| 3.2 | Document evidence chain from symptom to root cause | 🟢 Core | 10 |
| 3.3 | Find hidden bug that isn't in the error logs (logic error) | 🟡 Challenge | 20 |
| 3.4 | Identify race condition or timing-dependent bug | 🟡 Challenge | 20 |
| 3.5 | Discover and document security vulnerability | 🔴 Bonus | 30 |

**✅ Outcome:** Documented root causes with supporting evidence.

---

### 5. Lab 4: Generate and Apply Fixes ⏱️ _30 minutes_

**Goal:** Create targeted fixes using the Fix Agent.

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Review root causes** (2 min)
```
Open debugging/root-cause-analysis.md
Prioritize fixes by:
- Severity of the bug
- Confidence in diagnosis
- Risk of the fix
```

**Step 2: Generate fix for critical bug** (10 min)

Open Copilot Chat with your analysis:

```
Generate a fix for this bug:

Root Cause: [your documented root cause]
Location: [file and line]

Requirements for the fix:
1. Minimal change - only fix the bug
2. No unrelated refactoring
3. Preserve existing behavior for non-buggy cases
4. Add defensive checks to prevent recurrence

Provide:
- The exact code change
- Explanation of why this fixes it
- Any risks or side effects
```

✅ **Expected Output:** Targeted fix with explanation.

**Step 3: Generate fixes for remaining bugs** (10 min)

Use similar prompts for other identified bugs:

```
For each remaining bug, generate:
1. Minimal fix code
2. Test case that proves it's fixed
3. Defensive change to prevent recurrence
```

**Step 4: Apply fixes carefully** (5 min)

For each fix:
```
1. Apply the fix to buggy-app/src/
2. If possible, run existing tests
3. Note any concerns for review
```

**Step 5: Document fixes** (3 min)
- Update `debugging/fix-validation.md`
- Note which bugs are fixed
- Note any remaining concerns

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 4.1 (minimal fix) | Count lines changed - fewer is better |
| 4.2 (document why) | Future you will thank present you |
| 4.3 (fix all bugs) | Do them one at a time, test between |
| 4.4 (defensive fix) | Add validation, add logging, add tests |
| 4.5 (refactor pattern) | Only after all bugs are fixed |

---

**Participants:**
- Use the Fix Agent to:
  - Generate minimal, targeted fixes
  - Explain the reasoning behind each fix
  - Identify potential side effects
- Apply fixes to `buggy-app/src/`

**Principles Enforced:**
- Smallest change that resolves the issue
- No unrelated refactoring
- Clear explanation of the fix

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 4.1 | Apply fix for highest-severity bug | 🟢 Core | 15 |
| 4.2 | Document why fix is minimal and targeted | 🟢 Core | 10 |
| 4.3 | Fix all identified bugs (3+ bugs) | 🟡 Challenge | 20 |
| 4.4 | Propose defensive fix that prevents similar bugs | 🟡 Challenge | 15 |
| 4.5 | Refactor problematic code pattern across codebase | 🔴 Bonus | 25 |

**✅ Outcome:** Applied fixes with documented reasoning.

---

### 6. Lab 5: Validate Fixes and Check Regressions ⏱️ _20 minutes_

**Goal:** Ensure fixes resolve issues without introducing regressions.

---

#### 📖 Step-by-Step Walkthrough

**Step 1: List all fixes to validate** (2 min)
```
Create a validation checklist from your fixes:
- Bug fixed
- Location of fix
- Expected behavior after fix
- How to test
```

**Step 2: Verify each fix** (8 min)

Open Copilot Chat with your fixed code:

```
Verify this fix is correct:

Original bug: [description]
Root cause: [from your analysis]
Fix applied: [the code change]

Check:
1. Does this fix address the root cause?
2. Will the original error still occur?
3. Are there edge cases this doesn't handle?
4. Could this fix cause any new issues?
```

✅ **Expected Output:** Validation verdict with reasoning for each fix.

**Step 3: Identify regression risks** (5 min)

Use this prompt:

```
For the fix in @[fixed-file]:

Identify regression risks:
1. What other code calls this function?
2. What relies on the previous behavior?
3. What edge cases should be tested?
4. What integration points might be affected?

List the top 5 areas to check for regressions.
```

**Step 4: Generate regression tests** (3 min)

Use this prompt:

```
Generate regression test cases for this fix:

Bug: [description]
Fix: [the change]

For each test, provide:
- Test name
- Input/scenario
- Expected result
- Why this test is important
```

**Step 5: Document validation results** (2 min)
- Update `debugging/fix-validation.md`
- Note validation status for each fix
- List any remaining concerns

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 5.1 (verify fixes) | Walk through the fix with specific inputs |
| 5.2 (regression areas) | Check callers, related features, edge cases |
| 5.3 (regression tests) | Test the fix + test it doesn't break related code |
| 5.4 (automation) | Script that runs tests and checks error logs |

---

#### ⚠️ Common Pitfalls

- ❌ **Trusting the fix without verification:** Always test with real scenarios
- ❌ **Missing edge cases:** The fix works for main case but fails on edges
- ❌ **Not checking related code:** Fix in module A breaks module B

---

**Artifact Updated:** `debugging/fix-validation.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 5.1 | Verify all applied fixes resolve their errors | 🟢 Core | 10 |
| 5.2 | Identify 2+ potential regression areas | 🟡 Challenge | 15 |
| 5.3 | Write regression tests for fixed bugs | 🟡 Challenge | 15 |
| 5.4 | Create automated validation script | 🔴 Bonus | 25 |

**✅ Outcome:** Validated fixes with regression check documentation.

---

### 7. Wrap-Up: Building a Debugging Playbook ⏱️ _10 minutes_

**Discussion:**
- How to institutionalize agent-driven debugging
- Building team debugging playbooks
- Integrating with incident response workflows

**Takeaways:**
- Structured debugging > ad-hoc investigation
- Documentation enables knowledge sharing
- Custom agents encode team debugging expertise

---

## 8. CLI Quick Reference

### Error Explanation
```bash
gh copilot explain "TypeError: Cannot read property 'id' of undefined"
```

### Log Analysis
```bash
cat logs/error-logs.txt | gh copilot explain
```

### Fix Suggestion
```bash
gh copilot suggest "fix async race condition in OrderService.processOrder"
```

### Code Explanation
```bash
gh copilot explain -f src/services/OrderService.ts
```

---

## 9. MCP Context Model (Conceptual)

For debugging, shared context includes:

| Context Element | Purpose |
|-----------------|---------|
| Error Catalog | Known errors and patterns |
| Code Architecture | System structure understanding |
| Investigation History | Previous debugging sessions |
| Fix Patterns | Common solutions for error types |
| Test Coverage | What's validated vs. at risk |

> MCP is presented conceptually—participants capture context in markdown artifacts.

---

## 10. Success Criteria

By the end of this workshop, participants will have:

- [ ] Triaged and categorized application errors
- [ ] Created a custom diagnosis agent
- [ ] Identified root causes with documented evidence
- [ ] Generated and applied targeted fixes
- [ ] Validated fixes and checked for regressions
- [ ] Understood how to build debugging playbooks

---

## 11. Scoring & Achievement Levels

### Point Breakdown

| Category | Points Available |
|----------|------------------|
| 🟢 Core Challenges | 100 points |
| 🟡 Challenge Tasks | 135 points |
| 🔴 Bonus Tasks | 125 points |
| **Total Possible** | **360 points** |

### Achievement Levels

| Level | Points | Badge |
|-------|--------|-------|
| 🥇 **Debug Master** | 300+ | Elite debugging skills |
| 🥈 **Root Cause Hunter** | 215-299 | Strong diagnostic abilities |
| 🥉 **Bug Fixer** | 130-214 | Solid foundational understanding |
| **Participant** | <130 | Completed core workshop activities |

### Time Bonuses

| Completion Time | Bonus |
|-----------------|-------|
| Under 2 hours | +30 points |
| Under 2.5 hours | +15 points |

---

## Appendix: Starter Prompts

### Triage Prompt
```
Analyze these error logs and categorize them by:
1. Error type (runtime, logic, data, integration)
2. Severity (critical, high, medium, low)
3. Likely component affected

Prioritize which errors should be investigated first and explain your reasoning.
```

### Diagnosis Prompt
```
Given this error and stack trace, help me identify the root cause:

[Error details]

Trace through the code path, identify where the failure occurs, 
and explain what conditions lead to this error. 
Provide evidence from the code to support your diagnosis.
```

### Fix Generation Prompt
```
Based on this root cause analysis:

[Root cause details]

Generate a minimal fix that:
1. Resolves the root cause
2. Doesn't introduce side effects
3. Follows existing code patterns

Explain your reasoning for the fix approach.
```

### Validation Prompt
```
Review this fix:

[Fix details]

Verify that:
1. The original error is resolved
2. No regressions are introduced
3. Edge cases are handled

Suggest any additional tests needed.
```
