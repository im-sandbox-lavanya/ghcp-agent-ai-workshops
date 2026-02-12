# Workshop 3: Debugging with Agents

> _Copilot CLI, SDK, MCP Concepts, Custom Agents_

---

## Overview

- **Duration:** 2.5 - 3 hours  
- **Format:** Instructor-led, challenge-based workshop  
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

**Participants:**
- Review error logs and stack traces
- Use Copilot Chat and CLI to:
  - Categorize errors by type and severity
  - Identify patterns across failures
  - Prioritize investigation order

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

**Participants define an agent that:**
- Analyzes error messages and stack traces
- Traces execution paths through code
- Identifies likely root causes
- Documents evidence and reasoning

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

**Participants:**
- Select 2-3 prioritized errors
- Use the Diagnosis Agent to:
  - Trace the error source
  - Identify contributing factors
  - Document the root cause with evidence

**Techniques Applied:**
- Stack trace analysis
- Code path tracing
- State inspection reasoning

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

**Participants:**
- Use the Validation Agent to:
  - Verify the error is resolved
  - Check for regressions in related functionality
  - Suggest additional test coverage

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
