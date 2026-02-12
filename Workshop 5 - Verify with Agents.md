# Workshop 5: Verify with Agents

> _Security & Code Review with Copilot CLI, SDK, MCP Concepts, Custom Agents_

---

## Overview

- **Duration:** 2.5 - 3 hours  
- **Format:** Instructor-led, challenge-based workshop  
- **Difficulty:** 🟡 Intermediate to 🔴 Advanced  
- **Audience:** Developers, Security Engineers, Tech Leads, Reviewers  
- **Focus:** Using AI agents to perform systematic security analysis and code reviews

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

**Participants:**
- Review the target application architecture
- Use Copilot Chat to:
  - Identify high-risk areas (auth, data handling, APIs)
  - Prioritize components for review
  - Define verification objectives

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

**Participants define an agent that:**
- Checks for OWASP Top 10 vulnerabilities
- Analyzes authentication and session management
- Identifies data exposure and injection risks
- Documents findings with severity and context

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

**Participants:**
- Use the Security Scanner Agent to analyze:
  - Authentication flows
  - Input validation and sanitization
  - Data handling and storage
  - API security

**Vulnerability Categories Covered:**
- Injection (SQL, Command, XSS)
- Broken Authentication
- Sensitive Data Exposure
- Security Misconfiguration
- Insecure Direct Object References

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

**Participants:**
- Use the Code Review Agent to:
  - Check code quality and maintainability
  - Identify error handling gaps
  - Verify logging and monitoring practices
  - Assess adherence to secure coding patterns

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

**Participants:**
- Use the Remediation Agent to:
  - Generate secure code alternatives
  - Prioritize fixes by risk and effort
  - Provide implementation guidance
  - Identify quick wins vs. longer-term improvements

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

**Participants:**
- Use the Verification Agent to:
  - Confirm findings are addressed
  - Check for regression risks
  - Document verification evidence

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
