# Workshop 5: Verify with Agents

> _Security & Code Review with Copilot CLI, SDK, MCP Concepts, Custom Agents_

---

## Overview

- **Duration:** 2.5 - 3 hours  
- **Format:** Instructor-led, guided hands-on workshop  
- **Difficulty:** 🟡 Intermediate to 🔴 Advanced  
- **Audience:** Developers, Security Engineers, Tech Leads, Reviewers  
- **Focus:** Using AI agents to perform systematic security analysis and code reviews

---

## Table of Contents

1. [Workshop Purpose](#1-workshop-purpose)  
   *How AI agents elevate verification from checklist-driven reviews to intelligent, context-aware analysis for security vulnerabilities, structured code reviews, and actionable remediation*

2. [Design Principles](#2-design-principles)  
   *Core principles: Security as first-class concern, context-aware review over generic rules, custom agents for domain-specific verification, actionable findings over noise, remediation guidance, continuous verification*

3. [Scope Decisions (Intentional)](#3-scope-decisions-intentional)  
   *What's included: Copilot Chat, Copilot CLI, custom security/review agents, MCP concepts, structured verification artifacts. What's excluded: Full SAST/DAST tools, compliance deep-dives, penetration testing, infrastructure security*

4. [Pre-Provisioned Repository](#4-pre-provisioned-repository)  
   *Repository with target-app/ (intentional security vulnerabilities), verification/, security/, agents/ (security-scanner, code-review, remediation, verification), and prompts/ folders*

5. [Agent Strategy for Verification](#5-agent-strategy-for-verification)  
   *Four distinct agent roles: Security Scanner Agent (identifies vulnerabilities), Code Review Agent (consistent criteria), Remediation Agent (fix recommendations), Verification Agent (validates completeness)*

6. [Copilot CLI Integration](#6-copilot-cli-integration)  
   *Terminal-based security checks with `gh copilot explain` and `gh copilot suggest`. When to use CLI vs Chat for quick checks, single-file review vs multi-file analysis, threat modeling*

7. [Agenda & Flow (2.5 - 3 Hours)](#7-agenda--flow-25---3-hours)  
   *Complete workflow: Scope → Scan → Review → Remediate → Verify*
   
   - **[Introduction: Why Verification Needs Agents](#1-introduction-why-verification-needs-agents-️-10-minutes)** _(10 min)_  
     - Conceptual overview - no Copilot usage
     - Why traditional security reviews fail (inconsistent criteria, missed vulnerabilities, generic findings, vague remediation)
     - How agents provide systematic analysis, context-aware detection, actionable guidance, documented trails
   
   - **[Lab 1: Define Verification Scope](#2-lab-1-define-verification-scope-️-20-minutes)** _(20 min)_  
     - **Mode:** Standard Copilot Chat with application context
     - **Features Used:**
       - File reference (`@target-app`) for architecture analysis
       - Multi-turn conversations for threat modeling
       - Structured output for risk assessment
     - **Activities:**
       - Review application architecture (entry points, data flows, critical components)
       - Identify high-risk areas (auth, data I/O, database ops, APIs, admin functions)
       - Create STRIDE threat model (Spoofing, Tampering, Repudiation, Information Disclosure, DoS, Elevation of Privilege)
       - Map trust boundaries (user → app, app → DB, app → APIs, admin vs user)
       - Document scope in security-scope.md with priorities
     - **Challenges:** 5+ high-risk components, threat model diagram, map data flows/trust boundaries, identify attack vectors
   
   - **[Lab 2: Create a Custom Security Scanner Agent](#3-lab-2-create-a-custom-security-scanner-agent-️-25-minutes)** _(25 min)_  
     - **Mode:** Agent definition creation (instruction-based, not SDK)
     - **Features Used:**
       - Copilot Chat for generating OWASP detection rules
       - Manual markdown file creation (`agents/security-scanner-agent.md`)
       - Security pattern templates with severity classification
     - **Activities:**
       - Define agent identity (systematic scanner, assume inputs malicious, document everything)
       - Add OWASP Top 10 detection rules (Injection, Broken Auth, Data Exposure, Access Control, Misconfiguration)
       - Add severity classification (CRITICAL/HIGH/MEDIUM/LOW with criteria)
       - Define finding format (severity, location, description, evidence, impact, fix)
       - Add false positive filtering (reachability check, validation elsewhere, test code detection)
     - **Challenges:** 5+ OWASP detection rules, severity criteria, false positive filtering, CWE/CVE compliance mapping
   
   - **[Lab 3: Perform Security Analysis](#4-lab-3-perform-security-analysis-️-35-minutes)** _(35 min)_  
     - **Mode:** Custom Security Scanner Agent + Copilot CLI
     - **Features Used:**
       - File reference (`@security-scanner-agent.md` + `@target-app`) for agent-guided scanning
       - **CLI:** `gh copilot explain` with piped config files for quick checks
       - Pattern detection for OWASP vulnerabilities
       - Evidence extraction from code
     - **Activities:**
       - Analyze authentication (SQL injection, weak passwords, session management, token vulnerabilities, rate limiting)
       - Check input validation (SQL injection, command injection, XSS, path traversal, LDAP/XML injection)
       - Find data exposure (passwords in logs, data in URLs, excessive API responses, hardcoded secrets, insecure storage)
       - Check configurations (debug mode, default credentials, CORS, security headers)
       - Document findings with severity, location, and evidence
     - **Challenges:** 3+ injection vulnerabilities, auth/authorization flaws, sensitive data exposure, security misconfiguration, business logic vulnerability
   
   - **[Lab 4: Structured Code Review](#5-lab-4-structured-code-review-️-25-minutes)** _(25 min)_  
     - **Mode:** Custom Code Review Agent via Copilot Chat + CLI
     - **Features Used:**
       - File reference (`@target-app`) for multi-dimensional review
       - Pattern search for error handling and logging issues
       - **CLI:** `gh copilot explain` for dependency vulnerability checks
       - Structured checklist generation
     - **Activities:**
       - Create review checklist (component, files, date)
       - Review error handling (silent catches, stack trace exposure, logging context, global handler, DB error exposure)
       - Review logging practices (passwords, tokens, PII, financial data, secrets in logs; security events logged?)
       - Check input validation (server-side, all APIs, centralized, error messages, whitelist vs blacklist)
       - Check dependencies for known CVEs
       - Complete security review checklist
     - **Challenges:** Complete checklist for 3+ components, identify error handling leaks, find logging exposing sensitive data, vulnerable dependencies with CVE references
   
   - **[Lab 5: Generate Remediation Plan](#6-lab-5-generate-remediation-plan-️-25-minutes)** _(25 min)_  
     - **Mode:** Custom Remediation Agent via Copilot Chat
     - **Features Used:**
       - File reference (`@findings.md`) for prioritization
       - Secure code generation with explanations
       - Pattern library creation
       - Risk/effort matrix generation
     - **Activities:**
       - Prioritize findings by severity and effort (Critical + Low Effort = Fix Immediately, etc.)
       - Generate secure fix for critical vulnerability (secure code, explanation, hardening, tests)
       - Generate fixes for all findings (minimal changes, secure patterns, related areas, verification)
       - Create secure patterns library (SQL, auth, input validation, logging, error handling)
       - Document remediation plan with priorities and owners
     - **Challenges:** Secure fix for critical vuln, risk/effort prioritization matrix, implement auth fix, create reusable secure patterns library
   
   - **[Lab 6: Verification and Sign-Off](#7-lab-6-verification-and-sign-off-️-15-minutes)** _(15 min)_  
     - **Mode:** Custom Verification Agent via Copilot Chat
     - **Features Used:**
       - Fix validation analysis
       - Regression risk detection
       - Before/after comparison generation
       - Evidence documentation
     - **Activities:**
       - Create verification checklist (finding ID, original issue, fix applied, status)
       - Verify critical fixes (addresses root cause, secure code, edge cases, new vulnerabilities, follows patterns)
       - Check for regressions (functionality, performance, dependencies, tests)
       - Create before/after security comparison table
       - Document verification evidence
     - **Challenges:** Verify all critical findings, create before/after comparison, generate security regression test suite

8. [CLI Quick Reference](#8-cli-quick-reference)  
   *Command examples: Security analysis with piped files, secure pattern suggestions, configuration review with `-f` flag, dependency checks with jq*

9. [MCP Context Model (Conceptual)](#9-mcp-context-model-conceptual)  
   *Shared context: Threat Model (attack vectors), Security Policies (requirements), Secure Patterns (approved implementations), Finding History (previous vulnerabilities), Compliance Requirements (regulations). Captured in markdown artifacts*

10. [OWASP Top 10 Reference](#10-owasp-top-10-reference)  
    *Agent checks mapped to OWASP Top 10: Injection, Broken Authentication, Sensitive Data Exposure, XXE, Broken Access Control, Security Misconfiguration, XSS, Insecure Deserialization, Known Vulnerabilities, Insufficient Logging*

11. [Success Criteria](#11-success-criteria)  
    *Workshop completion checklist: defined verification scope, created security scanner agent, identified vulnerabilities with categorization, performed structured code review, generated remediation guidance, understood verification/sign-off*

12. [Scoring & Achievement Levels](#12-scoring--achievement-levels)  
    *375 total points (100 core, 125 challenge, 150 bonus). Achievement levels: 🥇 Security Champion (315+), 🥈 Vulnerability Hunter (225-314), 🥉 Security Reviewer (135-224). Time bonuses available*

13. [Appendix: Starter Prompts](#appendix-starter-prompts)  
    *Ready-to-use prompts for: Security Scope (risk assessment), Vulnerability Scan (OWASP checks with severity), Code Review (best practices evaluation), Remediation (secure alternatives), Verification (fix validation)*

14. [Appendix: Security Review Checklist](#appendix-security-review-checklist)  
    *Comprehensive checklist covering: Authentication (password hashing, sessions, MFA, lockout), Authorization (server-side enforcement, least privilege, direct object refs), Input Validation (sanitization, parameterized queries, output encoding), Data Protection (encryption, TLS, no sensitive logs), Error Handling (no sensitive info exposure, graceful failures, security event logging)*

---

## 1. Workshop Purpose

This workshop demonstrates how **AI agents can elevate verification activities** from checklist-driven reviews to **intelligent, context-aware analysis**.

Participants will learn to:

- Use agents to identify security vulnerabilities
- Perform structured code reviews with consistent criteria
- Generate actionable remediation guidance
- Build reusable verification workflows

The emphasis is on **systematic verification methodology**, not superficial scanning.

---

## 2. Design Principles

- Security as a first-class concern
- Context-aware review over generic rules
- Custom agents for domain-specific verification
- Actionable findings over noise
- Remediation guidance with every finding
- Continuous verification, not one-time audits

---

## 3. Scope Decisions (Intentional)

### ✅ Included

- Copilot Chat for interactive security analysis
- Copilot CLI for quick vulnerability checks
- Custom security and review agents (instruction-based)
- MCP as a **conceptual model** for shared security context
- Structured verification artifacts

### ❌ Excluded

- Full SAST/DAST tool integration
- Compliance framework deep-dives (SOC2, PCI-DSS)
- Penetration testing
- Infrastructure security review

This keeps the workshop focused on **how agents improve verification decisions**, not compliance tooling.

---

## Difficulty & Challenge Levels

| Level | Description | Time Pressure |
|-------|-------------|---------------|
| 🟢 **Core** | Must complete - foundational skills | Guided pace |
| 🟡 **Challenge** | Stretch goals - deeper understanding | Time-boxed |
| 🔴 **Bonus** | Expert level - independent problem solving | Self-paced |

---

## 4. Pre-Provisioned Repository

Participants receive a repository containing an **application with security issues**, review templates, and scaffolding for agent-driven verification.

```
/workshop-repo
├── target-app/
│   ├── src/
│   │   ├── auth/
│   │   ├── api/
│   │   ├── data/
│   │   └── utils/
│   ├── config/
│   └── README.md
│
├── verification/
│   ├── security-scope.md
│   ├── findings.md
│   ├── remediation-plan.md
│   └── review-checklist.md
│
├── security/
│   ├── threat-model.md
│   ├── vulnerability-catalog.md
│   └── secure-patterns.md
│
├── agents/
│   ├── security-scanner-agent.md
│   ├── code-review-agent.md
│   ├── remediation-agent.md
│   └── verification-agent.md
│
├── prompts/
│   ├── vulnerability-scan.md
│   ├── code-review.md
│   ├── remediation.md
│   └── verification.md
│
└── README.md
```

> **Note:** The application contains **intentional security vulnerabilities** (OWASP Top 10 examples). All documents are partially filled to guide participants.

---

## 5. Agent Strategy for Verification

Participants work with **four distinct agent roles**:

### 1. 🔒 Security Scanner Agent
- Identifies common vulnerability patterns
- Analyzes authentication and authorization
- Checks for data exposure risks

### 2. 📋 Code Review Agent
- Applies consistent review criteria
- Identifies code quality issues
- Checks adherence to secure coding patterns

### 3. 🛠️ Remediation Agent
- Generates fix recommendations
- Provides secure code alternatives
- Explains security implications

### 4. ✅ Verification Agent
- Validates remediation completeness
- Checks for regression risks
- Documents verification evidence

> Agents are defined via **clear instructions**, not SDKs.

---

## 6. Copilot CLI Integration

This workshop uses **Copilot CLI** for quick security checks:

### Key CLI Patterns

```bash
# Analyze code for security issues
gh copilot explain "check this code for SQL injection vulnerabilities"

# Suggest secure alternatives
gh copilot suggest "secure way to handle user authentication tokens"

# Review specific patterns
gh copilot explain -f src/auth/login.ts "identify security issues"
```

### When to Use CLI vs Chat

| Use Case | CLI | Chat |
|----------|-----|------|
| Quick vulnerability check | ✅ | |
| Single-file review | ✅ | |
| Multi-file security analysis | | ✅ |
| Interactive threat modeling | | ✅ |
| Complex remediation planning | | ✅ |

---

## 7. Agenda & Flow (2.5 - 3 Hours)

### 1. Introduction: Why Verification Needs Agents ⏱️ _10 minutes_

**Why traditional security reviews often fail:**
- Inconsistent review criteria
- Missed vulnerabilities due to time pressure
- Generic findings without context
- Remediation guidance too vague to act on

**How agents help:**
- Systematic, repeatable analysis
- Context-aware vulnerability detection
- Actionable remediation guidance
- Documented verification trails

#### Flow Overview
```
Scope → Scan → Review → Remediate → Verify
```

**✅ Outcome:** Shared understanding of agent-driven verification.

---

### 2. Lab 1: Define Verification Scope ⏱️ _20 minutes_

**Goal:** Establish clear boundaries for security and code review.

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Review application architecture** (3 min)
```
Open target-app/ and identify:
- Entry points (APIs, web routes, CLI)
- Data flows (user input → storage → output)
- Critical components (auth, payment, admin)
```

**Step 2: Identify high-risk areas** (5 min)

Open Copilot Chat:

```
Analyze @target-app and identify high-risk security areas:

1. Authentication and session management
2. Data input/output handlers
3. Database operations
4. External API integrations
5. Admin/privileged functions

For each area, rate risk as: Critical / High / Medium / Low
Explain why.
```

✅ **Expected Output:** Risk-rated list of 5+ components.

**Step 3: Create threat model** (7 min)

Use this prompt:

```
Create a STRIDE threat model for @target-app:

- Spoofing: Identity impersonation risks
- Tampering: Data modification risks
- Repudiation: Audit trail gaps
- Information Disclosure: Data leakage risks
- Denial of Service: Availability threats
- Elevation of Privilege: Authorization bypass

For each threat type, identify:
- Where it applies
- Attack scenario
- Potential impact
```

**Step 4: Map trust boundaries** (3 min)

Use this prompt:

```
Identify trust boundaries in @target-app:

1. User → Application (input validation boundary)
2. Application → Database (query boundary)
3. Application → External APIs (integration boundary)
4. Admin vs User access (authorization boundary)

What data crosses each boundary? What validation happens?
```

**Step 5: Document scope** (2 min)
- Copy findings to `verification/security-scope.md`
- Prioritize components for review
- Note exclusions

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 1.1 (high-risk) | Think: auth, input, data, admin, integrations |
| 1.2 (threat model) | Use STRIDE: S-T-R-I-D-E |
| 1.3 (data flows) | Follow user input from entry to storage to output |
| 1.4 (attack vectors) | Think like an attacker: "How would I break this?" |

---

**Artifact Updated:** `verification/security-scope.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 1.1 | Identify 5+ high-risk components for review | 🟢 Core | 10 |
| 1.2 | Create threat model diagram for the application | 🟢 Core | 10 |
| 1.3 | Map data flows and identify trust boundaries | 🟡 Challenge | 15 |
| 1.4 | Identify attack vectors based on STRIDE model | 🔴 Bonus | 25 |

**✅ Outcome:** Clear, prioritized scope for verification activities.

---

### 3. Lab 2: Create a Custom Security Scanner Agent ⏱️ _25 minutes_

**Goal:** Build a purpose-driven agent for vulnerability detection.

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Create agent file** (2 min)
```
Create agents/security-scanner-agent.md
```

**Step 2: Define agent identity** (5 min)

Add to your agent file:

```markdown
# Security Scanner Agent

## Identity
You are a security analyst specializing in application security.
You find vulnerabilities systematically and document them clearly.

## Your Approach
1. Scan methodically – don’t skip areas
2. Assume inputs are malicious until proven otherwise
3. Document every finding with evidence
4. Rate severity based on exploitability and impact
5. Suggest remediations, not just problems

## You Must NOT
- Ignore "minor" issues – document everything
- Make assumptions without checking code
- Report findings without severity and location
```

**Step 3: Add OWASP detection rules** (10 min)

Use Copilot to generate rules:

```
Generate detection rules for these OWASP Top 10 categories:

1. Injection (SQL, XSS, Command)
2. Broken Authentication
3. Sensitive Data Exposure
4. Broken Access Control
5. Security Misconfiguration

For each category:
- Code patterns to look for
- Example vulnerable code
- Why it’s dangerous
- How to fix it
```

✅ **Expected Output:** Detection rules for 5+ OWASP categories.

**Step 4: Add severity classification** (5 min)

Add to your agent:

```markdown
## Severity Classification

| Severity | Criteria | Example |
|----------|----------|----------|
| CRITICAL | RCE, data breach, auth bypass | SQL injection in login |
| HIGH | Significant data exposure, escalation | IDOR, XSS with session theft |
| MEDIUM | Limited exploitation, requires auth | Self-XSS, verbose errors |
| LOW | Informational, best practice | Missing headers, weak algo |

## Finding Format
```
**[SEVERITY] Finding Title**
- Location: file:line
- Description: What’s wrong
- Evidence: Code snippet
- Impact: What attacker can do
- Fix: How to remediate
```
```

**Step 5: Add false positive filtering** (3 min)

```markdown
## False Positive Checks

Before reporting, verify:
1. Is the vulnerable code actually reachable?
2. Is there validation elsewhere that mitigates?
3. Is this intentional test/sample code?
4. Does the context change the risk?
```

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 2.1 (5+ OWASP) | Injection, AuthN, Data, Access, Config |
| 2.2 (severity) | Impact × Exploitability = Severity |
| 2.3 (false positives) | "Is this actually exploitable?" |
| 2.4 (CWE mapping) | Reference cwe.mitre.org |

---

**Agent Defined In:** `agents/security-scanner-agent.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 2.1 | Define detection rules for 5+ OWASP categories | 🟢 Core | 10 |
| 2.2 | Include severity classification criteria | 🟢 Core | 10 |
| 2.3 | Add context-aware false positive filtering | 🟡 Challenge | 15 |
| 2.4 | Include compliance mapping (CWE/CVE references) | 🔴 Bonus | 25 |

**✅ Outcome:** A reusable security scanning agent.

---

### 4. Lab 3: Perform Security Analysis ⏱️ _35 minutes_

**Goal:** Use the security agent to identify vulnerabilities.

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Start with authentication** (10 min)

Open Copilot Chat with your agent and auth files:

```
Using @security-scanner-agent.md, analyze @target-app/src/auth/ for:

1. SQL injection in login/registration
2. Weak password handling (plain text, weak hash)
3. Session management issues
4. Token vulnerabilities (JWT, session)
5. Missing rate limiting

Document each finding with severity, location, and evidence.
```

✅ **Expected Output:** 2-3 authentication-related findings.

**Step 2: Check input validation** (8 min)

Use this prompt:

```
Analyze @target-app/src/api/ for injection vulnerabilities:

1. SQL injection (string concatenation in queries)
2. Command injection (exec, spawn with user input)
3. XSS (user input reflected without encoding)
4. Path traversal (file paths from user input)
5. LDAP/XML injection

For each, show the vulnerable code and explain exploitation.
```

**Step 3: Find data exposure** (8 min)

Use this prompt:

```
Analyze @target-app for sensitive data exposure:

1. Passwords or tokens in logs
2. Sensitive data in URLs (GET parameters)
3. API responses with excessive data
4. Hardcoded secrets in code
5. Insecure data storage

Check: logs, error messages, API responses, config files.
```

**Step 4: Check configurations** (5 min)

Use CLI for quick checks:

```bash
gh copilot explain "security issues in this config:
$(cat target-app/config/*.json)"
```

**Step 5: Document findings** (4 min)
- Copy all findings to `verification/findings.md`
- Organize by severity (Critical first)
- Note the evidence for each

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 3.1 (injection) | Search for: exec, query, eval + user input |
| 3.2 (auth flaws) | Check password storage, session handling |
| 3.3 (data exposure) | Grep for: console.log, password, secret |
| 3.4 (misconfig) | Check: debug mode, default creds, CORS |
| 3.5 (business logic) | What if user manipulates hidden fields? |

---

#### ⚠️ Common Pitfalls

- ❌ **Missing context:** Finding in dead code isn’t exploitable
- ❌ **Over-reporting:** One root cause, multiple symptoms
- ❌ **Severity inflation:** Not every finding is “Critical”

---

**Artifact Updated:** `verification/findings.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 3.1 | Find and document 3+ injection vulnerabilities | 🟢 Core | 15 |
| 3.2 | Identify authentication/authorization flaws | 🟢 Core | 10 |
| 3.3 | Discover sensitive data exposure issues | 🟡 Challenge | 15 |
| 3.4 | Find security misconfiguration in configs | 🟡 Challenge | 15 |
| 3.5 | Identify and exploit business logic vulnerability | 🔴 Bonus | 30 |

**✅ Outcome:** Documented security findings with severity ratings.

---

### 5. Lab 4: Structured Code Review ⏱️ _25 minutes_

**Goal:** Perform code review beyond security vulnerabilities.

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Create review checklist** (3 min)
```
Open verification/review-checklist.md and add:
- Component name
- Files reviewed
- Review date
```

**Step 2: Review error handling** (7 min)

Open Copilot Chat:

```
Review error handling in @target-app:

1. Are there catch blocks that swallow errors silently?
2. Do error messages expose stack traces to users?
3. Are errors logged with useful context?
4. Is there a global error handler?
5. Are database errors exposed to clients?

For each issue, note the file, line, and concern.
```

✅ **Expected Output:** Error handling review with 2-3 findings.

**Step 3: Review logging practices** (7 min)

Use this prompt:

```
Review logging in @target-app for security issues:

1. Passwords logged in plain text
2. Session tokens in logs
3. PII (email, phone, SSN) in logs
4. Credit card numbers or financial data
5. API keys or secrets in logs

Also check: Are security events logged? (Failed logins, access denied)
```

**Step 4: Check input validation** (5 min)

Use this prompt:

```
Review input validation patterns:

1. Is validation done server-side (not just client)?
2. Are all API inputs validated?
3. Is validation centralized or scattered?
4. Are validation errors helpful but not revealing?
5. Is there a whitelist or blacklist approach?

Identify gaps and inconsistencies.
```

**Step 5: Check dependencies** (3 min)

Use CLI:

```bash
gh copilot explain "check these dependencies for known vulnerabilities:
$(cat target-app/package.json)"
```

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 4.1 (checklist) | Use the appendix checklist as starting point |
| 4.2 (error handling) | Search for: catch, error, exception |
| 4.3 (logging) | Search for: log, console, logger + sensitive terms |
| 4.4 (dependencies) | Check npm audit or snyk for CVEs |

---

**Review Dimensions:**
- Input validation
- Error handling
- Logging (without sensitive data)
- Authentication/Authorization checks
- Dependency management

**Artifact Updated:** `verification/review-checklist.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 4.1 | Complete security review checklist for 3+ components | 🟢 Core | 10 |
| 4.2 | Identify error handling gaps that leak information | 🟡 Challenge | 15 |
| 4.3 | Find logging that exposes sensitive data | 🟡 Challenge | 15 |
| 4.4 | Identify vulnerable dependencies with CVE references | 🔴 Bonus | 20 |

**✅ Outcome:** Comprehensive code review with actionable feedback.

---

### 6. Lab 5: Generate Remediation Plan ⏱️ _25 minutes_

**Goal:** Create actionable remediation guidance for findings.

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Prioritize findings** (5 min)

Open Copilot Chat with your findings:

```
Create a remediation priority matrix for @findings.md:

| Finding | Severity | Effort | Priority |
|---------|----------|--------|---------|

Priority formula:
- Critical + Low Effort = Fix Immediately
- Critical + High Effort = Fix Soon, Plan Carefully
- Low + Low Effort = Quick Win
- Low + High Effort = Backlog
```

✅ **Expected Output:** Prioritized matrix of all findings.

**Step 2: Generate fix for critical vuln** (8 min)

For your highest-priority critical finding:

```
Generate a secure fix for this vulnerability:

**Finding:** [paste from findings.md]

Provide:
1. The secure code replacement
2. Explanation of why this is secure
3. Any additional hardening to add
4. Tests to verify the fix works
```

**Step 3: Generate fixes for other findings** (7 min)

Use this prompt:

```
For each finding in @findings.md, provide:

1. Minimal code change to fix
2. Secure coding pattern to follow
3. Related areas to check
4. Verification criteria

Format as a remediation checklist.
```

**Step 4: Create secure patterns library** (3 min)

Use this prompt:

```
Based on the vulnerabilities found, create a secure patterns library:

1. Secure SQL query pattern
2. Secure authentication pattern
3. Secure input validation pattern
4. Secure logging pattern
5. Secure error handling pattern

Provide code examples for each.
```

**Step 5: Document remediation plan** (2 min)
- Copy to `verification/remediation-plan.md`
- Order by priority
- Assign owners if working in team

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 5.1 (critical fix) | Use parameterized queries for SQL injection |
| 5.2 (priority matrix) | Severity × Exploitability ÷ Effort = Priority |
| 5.3 (auth fix) | Use bcrypt for passwords, secure session config |
| 5.4 (patterns library) | Reusable templates for common security patterns |

---

**Artifact Updated:** `verification/remediation-plan.md`

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 5.1 | Generate secure code fix for critical vulnerability | 🟢 Core | 15 |
| 5.2 | Create risk/effort prioritization matrix | 🟢 Core | 10 |
| 5.3 | Implement fix for authentication vulnerability | 🟡 Challenge | 20 |
| 5.4 | Create reusable secure coding patterns library | 🔴 Bonus | 25 |

**✅ Outcome:** Prioritized remediation plan with specific guidance.

---

### 7. Lab 6: Verification and Sign-Off ⏱️ _15 minutes_

**Goal:** Validate remediation and document verification evidence.

---

#### 📖 Step-by-Step Walkthrough

**Step 1: Create verification checklist** (2 min)
```
For each remediated finding, create:
- Finding ID
- Original issue
- Fix applied
- Verification status: ⬜ Pending / ✅ Verified / ❌ Failed
```

**Step 2: Verify critical fixes** (7 min)

Open Copilot Chat:

```
Verify this security fix:

**Original Finding:** [paste]
**Applied Fix:** [paste code change]

Confirm:
1. Does this fix address the root cause?
2. Is the new code secure?
3. Are there edge cases this misses?
4. Could this introduce new vulnerabilities?
5. Does this follow secure coding patterns?

Verdict: PASS / FAIL with explanation.
```

✅ **Expected Output:** Verification verdict for each critical finding.

**Step 3: Check for regressions** (3 min)

Use this prompt:

```
Analyze the remediation changes for regression risks:

[paste diff or changed files]

Check:
1. Functionality still works as expected?
2. Performance not degraded?
3. Other code that depends on changed code?
4. Tests still pass?
```

**Step 4: Create before/after comparison** (3 min)

Use this prompt:

```
Create a before/after security comparison:

| Category | Before | After | Status |
|----------|--------|-------|--------|
| SQL Injection | 3 vulnerabilities | 0 | ✅ Fixed |
| XSS | ... | ... | ... |

Summarize the security posture improvement.
```

---

#### 💡 Tips & Hints

| Challenge | Hint |
|-----------|------|
| 6.1 (verify all) | Walk through each fix with test inputs |
| 6.2 (before/after) | Count vulnerabilities by category |
| 6.3 (regression tests) | Create tests that would catch if vuln returns |

---

#### ⚠️ Common Pitfalls

- ❌ **Verifying without testing:** Always test with real inputs
- ❌ **Missing edge cases:** Test boundary conditions
- ❌ **Sign-off without evidence:** Document how you verified

---

**Discussion:**
- When is "good enough" good enough?
- Balancing security with delivery
- Continuous verification in CI/CD

**✅ Outcome:** Verification evidence and sign-off criteria.

#### 🎯 Challenges

| # | Challenge | Difficulty | Points |
|---|-----------|------------|--------|
| 6.1 | Verify all critical findings are remediated | 🟢 Core | 10 |
| 6.2 | Create before/after security comparison | 🟡 Challenge | 15 |
| 6.3 | Generate security regression test suite | 🔴 Bonus | 25 |

**Discussion:**
- When is "good enough" good enough?
- Balancing security with delivery
- Continuous verification in CI/CD

**✅ Outcome:** Verification evidence and sign-off criteria.

---

## 8. CLI Quick Reference

### Security Analysis
```bash
gh copilot explain "check this code for injection vulnerabilities:
$(cat src/api/userController.ts)"
```

### Secure Pattern Suggestion
```bash
gh copilot suggest "secure password hashing in Node.js"
```

### Configuration Review
```bash
gh copilot explain -f config/security.json "identify security misconfigurations"
```

### Dependency Check
```bash
gh copilot explain "security implications of these dependencies:
$(cat package.json | jq '.dependencies')"
```

---

## 9. MCP Context Model (Conceptual)

For verification, shared context includes:

| Context Element | Purpose |
|-----------------|---------|
| Threat Model | Known threats and attack vectors |
| Security Policies | Organization security requirements |
| Secure Patterns | Approved implementation patterns |
| Finding History | Previous vulnerabilities found |
| Compliance Requirements | Applicable regulations |

> MCP is presented conceptually—participants capture context in markdown artifacts.

---

## 10. OWASP Top 10 Reference

Agents are configured to check for:

| # | Vulnerability | Agent Check |
|---|---------------|-------------|
| 1 | Injection | SQL, Command, XSS patterns |
| 2 | Broken Authentication | Session, password, token handling |
| 3 | Sensitive Data Exposure | Logging, storage, transmission |
| 4 | XML External Entities | Parser configuration |
| 5 | Broken Access Control | Authorization checks |
| 6 | Security Misconfiguration | Config files, defaults |
| 7 | Cross-Site Scripting | Output encoding |
| 8 | Insecure Deserialization | Object handling |
| 9 | Known Vulnerabilities | Dependency versions |
| 10 | Insufficient Logging | Audit trail gaps |

---

## 11. Success Criteria

By the end of this workshop, participants will have:

- [ ] Defined a clear verification scope
- [ ] Created a custom security scanner agent
- [ ] Identified security vulnerabilities with proper categorization
- [ ] Performed structured code review
- [ ] Generated actionable remediation guidance
- [ ] Understood verification and sign-off processes

---

## 12. Scoring & Achievement Levels

### Point Breakdown

| Category | Points Available |
|----------|------------------|
| 🟢 Core Challenges | 100 points |
| 🟡 Challenge Tasks | 125 points |
| 🔴 Bonus Tasks | 150 points |
| **Total Possible** | **375 points** |

### Achievement Levels

| Level | Points | Badge |
|-------|--------|-------|
| 🥇 **Security Champion** | 315+ | Elite security verification skills |
| 🥈 **Vulnerability Hunter** | 225-314 | Strong security analysis abilities |
| 🥉 **Security Reviewer** | 135-224 | Solid foundational understanding |
| **Participant** | <135 | Completed core workshop activities |

### Time Bonuses

| Completion Time | Bonus |
|-----------------|-------|
| Under 2 hours | +30 points |
| Under 2.5 hours | +15 points |

---

## Appendix: Starter Prompts

### Security Scope Prompt
```
Analyze this application structure and identify:
1. High-risk areas that need security review (auth, data, APIs)
2. Components that handle sensitive data
3. External interfaces and attack surface

Prioritize areas for security review based on risk.
```

### Vulnerability Scan Prompt
```
Review this code for security vulnerabilities:

[Code snippet]

Check for:
1. Injection vulnerabilities (SQL, command, XSS)
2. Authentication/authorization issues
3. Sensitive data exposure
4. Input validation gaps

For each finding, provide:
- Severity (Critical/High/Medium/Low)
- Location in code
- Description of the risk
- Remediation guidance
```

### Code Review Prompt
```
Perform a code review of this component:

[Code snippet]

Evaluate:
1. Security best practices
2. Error handling completeness
3. Input validation
4. Logging practices (no sensitive data)
5. Code maintainability

Provide specific, actionable feedback.
```

### Remediation Prompt
```
For this security finding:

[Finding details]

Provide:
1. Secure code alternative
2. Step-by-step remediation instructions
3. Verification criteria
4. Any related areas to check
```

### Verification Prompt
```
Verify this remediation:

Original finding: [Finding]
Applied fix: [Fix details]

Confirm:
1. The vulnerability is resolved
2. No new issues introduced
3. Tests cover the fixed behavior
4. Documentation is updated
```

---

## Appendix: Security Review Checklist

### Authentication
- [ ] Passwords hashed with strong algorithm (bcrypt, Argon2)
- [ ] Session tokens are secure and expire appropriately
- [ ] Multi-factor authentication where required
- [ ] Account lockout after failed attempts

### Authorization
- [ ] Access controls enforced server-side
- [ ] Principle of least privilege applied
- [ ] Direct object references validated

### Input Validation
- [ ] All inputs validated and sanitized
- [ ] Parameterized queries used
- [ ] Output encoding applied

### Data Protection
- [ ] Sensitive data encrypted at rest
- [ ] TLS enforced for data in transit
- [ ] No sensitive data in logs

### Error Handling
- [ ] Errors don't expose sensitive information
- [ ] Failures handled gracefully
- [ ] Security events logged appropriately
