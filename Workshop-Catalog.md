# GitHub Copilot Agent AI Workshops - Catalog

> **Professional Training Series**  
> Mastering AI-Assisted Software Engineering with GitHub Copilot

---

## Executive Summary

This comprehensive workshop series transforms how development teams leverage GitHub Copilot—moving beyond simple code completion to **systematic, agent-driven workflows** across the entire software development lifecycle.

### Series Overview

**5 hands-on workshops** covering critical engineering activities:
- **Workshop 1:** Spec-Driven Development
- **Workshop 2:** Migrate & Modernize Applications  
- **Workshop 3:** Debugging with Agents
- **Workshop 4:** Testing with Agents
- **Workshop 5:** Security Verification & Code Review

### Key Benefits

✅ **Systematic Workflows** - Repeatable, structured processes for common engineering tasks  
✅ **Custom Agent Development** - Build domain-specific agents tailored to your needs  
✅ **Production-Ready Skills** - Practical techniques applicable immediately  
✅ **Reduced Cognitive Load** - Let agents handle tedious analysis while you focus on decisions  
✅ **Knowledge Capture** - Document tribal knowledge in reusable agent patterns

### Audience

- Developers, Technical Leads, Architects
- QA Engineers, SDETs, Test Automation Engineers
- Security Engineers, Code Reviewers
- SREs, DevOps Engineers, Support Engineers

---

## Quick Reference Matrix

| Workshop | Duration | Difficulty | Primary Copilot Features | Key Agents Created |
|----------|----------|------------|-------------------------|-------------------|
| **1. Spec-Driven Development** | 2 hrs | 🟡🔴 Intermediate-Advanced | Copilot Chat, File Reference (`@`), Multi-turn Conversations | Spec Agent, Planning Agent, Design Agent, Coding Agent |
| **2. Migrate & Modernize** | 2 hrs | 🟡🔴 Intermediate-Advanced | Copilot Chat, File Reference (`@`), Custom Agents | Analysis Agent, Modernization Agent, Review Agent |
| **3. Debugging with Agents** | 2 hrs | 🟡🔴 Intermediate-Advanced | Copilot CLI (`gh copilot`), Copilot Chat, Log Analysis | Triage Agent, Diagnosis Agent, Fix Agent, Validation Agent |
| **4. Testing with Agents** | 2 hrs | 🟡🔴 Intermediate-Advanced | Copilot Chat, Gherkin Generation, Pattern Templates | Test Design Agent, Playwright Agent, Review Agent |
| **5. Verify with Agents** | 2 hrs | 🟡🔴 Intermediate-Advanced | Copilot CLI + Chat, OWASP Scanning, Threat Modeling | Security Scanner Agent, Code Review Agent, Remediation Agent, Verification Agent |

---

## Copilot Features Used Across Workshops

### Core Features
- ✅ **Copilot Chat** - All workshops use interactive chat for reasoning and generation
- ✅ **File Reference (`@filename`)** - Context-aware analysis across multiple files
- ✅ **Multi-turn Conversations** - Iterative refinement of outputs
- ✅ **Structured Prompting** - Template-driven agent interactions

### Advanced Features
- ✅ **Copilot CLI** (`gh copilot explain`, `gh copilot suggest`) - Workshops 3, 5
- ✅ **Custom Agent Definitions** - All workshops create reusable agents
- ✅ **Pattern Detection** - Architectural smells, vulnerabilities, flakiness
- ✅ **Code Generation with Constraints** - Following defined patterns and rules
- ✅ **Before/After Comparison** - Validation and impact analysis

### MCP (Model Context Protocol) Concepts
All workshops introduce MCP as a **conceptual model** for managing shared context between agents and development activities, preparing teams for future SDK-based integrations.

---

## Workshop 1: Spec → Plan → Design → Code with GitHub Copilot Agents

### Overview
**Duration:** 2 hours  
**Audience:** Developers, Technical Leads, Architects  
**Focus:** Applying GitHub Copilot across the full software development lifecycle

### What You'll Learn
Transform ambiguous requirements into production-ready code through structured labs:
- Extract clear requirements from vague problem statements
- Create traceable plans from specifications
- Design architectures validated against requirements
- Implement code aligned with design decisions

### Workshop Structure

#### Lab 1: Specification
- **Mode:** Standard Copilot Chat with structured prompts
- **Create:** Specification artifacts (requirements, acceptance criteria, assumptions, constraints)
- **Agent:** Spec Agent clarifies requirements and identifies assumptions

#### Lab 2: Planning
- **Mode:** Copilot Chat with file reference (`@spec.md`)
- **Create:** Component breakdown, dependency graphs, task sequencing
- **Agent:** Planning Agent breaks down solutions and identifies critical paths

#### Lab 3: Design
- **Mode:** Copilot Chat with multi-file context
- **Create:** Architecture diagrams, API contracts, traceability matrix
- **Agent:** Design Agent validates coverage of requirements

#### Lab 4: Implementation
- **Mode:** Custom Coding Agent via Copilot Chat
- **Create:** Project structure, data models, services, unit tests
- **Agent:** Coding Agent scaffolds implementation following design

#### Lab 5: Validation
- **Mode:** Copilot Chat for alignment review
- **Create:** Alignment checklist, spec drift analysis, validation tests
- **Agent:** Validation ensures implementation matches specification

### Key Outcomes
✅ Structured specification from ambiguous inputs  
✅ Traceable plan linked to requirements  
✅ Validated design architecture  
✅ Aligned implementation with minimal drift  
✅ Reusable agent definitions for future projects

### Copilot Features Used
- Copilot Chat with file reference (`@`)
- Multi-turn structured conversations
- Gherkin-style acceptance criteria generation
- Mermaid diagram generation
- Code scaffolding with validation

---

## Workshop 2: Migrate & Modernize with Agents

### Overview
**Duration:** 2 hours  
**Audience:** Developers, Tech Leads, Architects  
**Focus:** Using custom AI agents to modernize legacy .NET and Java applications

### What You'll Learn
Systematically analyze and modernize legacy applications:
- Identify architectural smells and technical debt
- Define modernization goals with measurable criteria
- Create custom modernization agents with transformation rules
- Apply incremental, safe modernization patterns
- Validate changes without introducing regressions

### Workshop Structure

#### Lab 1: Understand Legacy Application
- **Mode:** Standard Copilot Chat with codebase context
- **Analyze:** Architectural smells, deprecated patterns, technical debt
- **Create:** Technical debt heatmap with priorities
- **Challenges:** 5+ architectural smells, 3+ deprecated APIs

#### Lab 2: Define Goals & Constraints
- **Mode:** Copilot Chat with artifact context (`@current-state.md`)
- **Define:** Target framework versions, architecture styles, success criteria
- **Create:** Phased modernization roadmap with constraints
- **Challenges:** 3+ success criteria, 3+ hard constraints

#### Lab 3: Create Modernization Agent
- **Mode:** Agent definition creation (markdown-based)
- **Build:** Custom agent with transformation rules
- **Patterns:** .NET (async/await, HttpClient, EF Core), Java (java.time, Spring Boot 3.x, records)
- **Challenges:** 5+ modernization rules, validation checklist

#### Lab 4: Apply Modernization
- **Mode:** Custom Agent via Copilot Chat with multi-file context
- **Transform:** Service layer, data access (ADO.NET→EF Core, JDBC→JPA), API layer
- **Preserve:** Business logic while modernizing implementation
- **Challenges:** Modernize 2+ services, convert to async, implement DI patterns

#### Lab 5: Validate Changes
- **Mode:** Custom Review Agent for comparison
- **Verify:** Business logic preservation, alignment with goals
- **Identify:** Regression risks and mitigation plans
- **Challenges:** Before/after comparison, regression test suite

### Technology-Specific Patterns

#### .NET Modernization
- .NET Framework 4.x → .NET 8+
- Web Forms → Blazor / Razor Pages
- WCF Services → gRPC / REST APIs
- Entity Framework 6 → EF Core 8
- Synchronous → async/await patterns

#### Java Modernization
- Java 8 → Java 17/21
- Spring Boot 2.x → Spring Boot 3.x
- JAX-RS → Spring WebFlux
- JDBC → R2DBC / Virtual Threads

### Key Outcomes
✅ Documented legacy application baseline  
✅ Clear modernization goals and constraints  
✅ Reusable modernization agent  
✅ Partially modernized application  
✅ Validated changes with risk assessment  
✅ Incremental modernization methodology

### Copilot Features Used
- Copilot Chat with file reference (`@`)
- Custom agent instructions
- Before/after code comparison
- Multi-file context analysis
- Pattern-based transformation

---

## Workshop 3: Debugging with Agents

### Overview
**Duration:** 2 hours  
**Audience:** Developers, Tech Leads, SREs, Support Engineers  
**Focus:** Systematic diagnosis, debugging, and resolution of application issues

### What You'll Learn
Transform debugging from ad-hoc investigation to structured process:
- Triage and categorize errors systematically
- Perform root cause analysis with evidence chains
- Generate minimal, targeted fixes
- Validate fixes without introducing regressions
- Build reusable debugging playbooks

### Workshop Structure

#### Lab 1: Triage Errors
- **Mode:** Copilot CLI + Copilot Chat with logs
- **CLI Usage:** `gh copilot explain` with piped log files for batch analysis
- **Categorize:** Runtime, logic, integration, configuration errors
- **Prioritize:** CRITICAL/HIGH/MEDIUM/LOW severity assignment
- **Challenges:** 4+ categories, identify patterns, predict cascading failures

#### Lab 2: Create Diagnosis Agent
- **Mode:** Agent definition creation with diagnosis rules
- **Build:** Evidence-based diagnosis agent
- **Rules:** NullReference, async deadlock, race conditions, memory leaks, config errors
- **Confidence:** HIGH/MEDIUM/LOW scoring system
- **Challenges:** 5+ diagnosis rules, evidence collection, confidence scoring

#### Lab 3: Investigate Root Causes
- **Mode:** Custom Diagnosis Agent via Copilot Chat
- **Analyze:** Step-by-step investigation with evidence chains
- **Find:** Hidden logic bugs, race conditions, security vulnerabilities
- **Document:** Root cause analysis with confidence ratings
- **Challenges:** Root cause for high-severity error, evidence chain, hidden bug, race condition

#### Lab 4: Generate Fixes
- **Mode:** Custom Fix Agent with code context
- **Generate:** Minimal, targeted fixes with explanations
- **Preserve:** Existing behavior for non-buggy cases
- **Add:** Defensive checks to prevent recurrence
- **Challenges:** Fix critical bug, fix 3+ bugs, defensive patterns

#### Lab 5: Validate Fixes
- **Mode:** Custom Validation Agent for verification
- **Verify:** Each fix addresses root cause
- **Check:** Regression risks (callers, edge cases, integration points)
- **Generate:** Regression test cases
- **Challenges:** Verify all fixes, identify regressions, automated test suite

### CLI Integration
```bash
# Explain errors
gh copilot explain "error message or stack trace"

# Analyze logs
gh copilot explain < error-logs.txt

# Suggest fixes
gh copilot suggest "how to fix null reference in UserService"
```

### Key Outcomes
✅ Prioritized error catalog  
✅ Reusable diagnosis agent  
✅ Documented root causes with evidence  
✅ Applied targeted fixes  
✅ Validated fixes with regression checks  
✅ Debugging playbook methodology

### Copilot Features Used
- Copilot CLI for terminal-based analysis
- Copilot Chat with multi-file context
- Stack trace analysis
- Evidence chain reasoning
- Pattern detection for bugs

---

## Workshop 4: Testing with Agents

### Overview
**Duration:** 2 hours  
**Audience:** Developers, QA Engineers, SDETs, Tech Leads  
**Focus:** Design, generate, and maintain automated tests with Playwright

### What You'll Learn
Move beyond test generation to intelligent test design:
- Understand application behavior for meaningful test coverage
- Derive test scenarios from user journeys
- Generate maintainable Playwright tests with proper patterns
- Reduce brittle, flaky test automation
- Review tests for quality and coverage gaps

### Workshop Structure

#### Lab 1: Understand Application
- **Mode:** Standard Copilot Chat with application context
- **Identify:** Critical user journeys and priorities
- **Assess:** Testing risk (complexity, data sensitivity, dependencies)
- **Scope:** MUST/SHOULD/COULD/WON'T test decisions
- **Challenges:** 5+ critical journeys, risk assessment, priority matrix

#### Lab 2: Generate Test Scenarios
- **Mode:** Copilot Chat for scenario generation
- **Format:** Gherkin-style Given-When-Then scenarios
- **Cover:** Happy paths, negative scenarios, boundary conditions
- **Document:** scenarios.md with priorities
- **Challenges:** 3+ happy path, 3+ negative, boundary conditions, cross-browser matrix

#### Lab 3: Create Playwright Agent
- **Mode:** Agent definition with test patterns
- **Strategy:** Selector strategy (data-testid > ARIA > text > CSS)
- **Patterns:** Page Object Model, fixtures, waiting patterns
- **Anti-patterns:** No arbitrary waits, no brittle selectors
- **Challenges:** Selector strategy, anti-patterns, page object patterns

#### Lab 4: Generate Tests
- **Mode:** Custom Playwright Agent via Copilot Chat
- **Generate:** Tests following agent conventions
- **Include:** Proper selectors, explicit waits, meaningful assertions
- **Parameterize:** Data-driven test variations
- **Challenges:** Happy path test, error test, multiple assertions, parameterized test, visual regression

#### Lab 5: Review & Improve
- **Mode:** Custom Review Agent for quality analysis
- **Create:** Coverage matrix (scenarios vs tests)
- **Find:** Flaky patterns (arbitrary waits, unreliable selectors, race conditions)
- **Fix:** Improve reliability with proper patterns
- **Challenges:** Coverage matrix, fix 2+ flaky patterns, retry logic

### Playwright Best Practices

#### Selector Strategy (Priority Order)
1. **data-testid** (most reliable) - `[data-testid="submit-button"]`
2. **ARIA roles** (accessible) - `page.getByRole('button', { name: 'Submit' })`
3. **Text content** (visible) - `page.getByText('Submit')`
4. **CSS selectors** (last resort) - `.submit-btn`

#### Waiting Patterns
✅ **DO:** `await page.waitForSelector('[data-testid="loaded"]')`  
✅ **DO:** `await expect(page.locator('.result')).toBeVisible()`  
❌ **DON'T:** `await page.waitForTimeout(3000)` - Never use arbitrary waits

### Key Outcomes
✅ Critical user journeys identified  
✅ Well-defined test scenarios  
✅ Custom Playwright agent with conventions  
✅ Maintainable, reliable tests  
✅ Coverage gaps identified and addressed  
✅ Intent-first testing methodology

### Copilot Features Used
- Copilot Chat with file reference
- Gherkin scenario generation
- Pattern-based code generation
- Coverage analysis
- Flakiness detection

---

## Workshop 5: Verify with Agents

### Overview
**Duration:** 2 hours  
**Audience:** Developers, Security Engineers, Tech Leads, Reviewers  
**Focus:** Systematic security analysis and code reviews

### What You'll Learn
Elevate verification from checklists to intelligent analysis:
- Perform threat modeling with STRIDE methodology
- Identify OWASP Top 10 vulnerabilities systematically
- Conduct structured code reviews with consistent criteria
- Generate actionable remediation guidance
- Validate fixes with verification evidence

### Workshop Structure

#### Lab 1: Define Verification Scope
- **Mode:** Standard Copilot Chat with architecture context
- **Analyze:** Entry points, data flows, critical components
- **Model:** STRIDE threat model (Spoofing, Tampering, Repudiation, Info Disclosure, DoS, Elevation)
- **Map:** Trust boundaries (user→app, app→DB, app→APIs)
- **Challenges:** 5+ high-risk components, threat model, trust boundaries, attack vectors

#### Lab 2: Create Security Scanner Agent
- **Mode:** Agent definition with OWASP detection rules
- **Coverage:** Injection, Broken Auth, Data Exposure, Access Control, Misconfiguration
- **Severity:** CRITICAL/HIGH/MEDIUM/LOW classification
- **Format:** Severity, location, evidence, impact, fix
- **Challenges:** 5+ OWASP rules, severity criteria, false positive filtering, CWE/CVE mapping

#### Lab 3: Perform Security Analysis
- **Mode:** Custom Security Scanner + Copilot CLI
- **CLI Usage:** `gh copilot explain` for config/dependency checks
- **Scan:** Authentication (SQL injection, weak passwords, session management, tokens)
- **Check:** Input validation (SQL, command, XSS, path traversal injections)
- **Find:** Data exposure (logs, URLs, API responses, hardcoded secrets)
- **Challenges:** 3+ injection vulns, auth flaws, data exposure, misconfiguration, business logic vuln

#### Lab 4: Structured Code Review
- **Mode:** Custom Code Review Agent + CLI
- **Review:** Error handling, logging practices, input validation
- **Check:** Dependencies for known CVEs
- **Document:** Review checklist with findings
- **Challenges:** Checklist for 3+ components, error leaks, sensitive data in logs, vulnerable dependencies

#### Lab 5: Generate Remediation
- **Mode:** Custom Remediation Agent
- **Prioritize:** Risk × Exploitability ÷ Effort = Priority
- **Generate:** Secure code fixes with explanations
- **Create:** Secure patterns library (SQL, auth, validation, logging, errors)
- **Challenges:** Fix critical vuln, priority matrix, auth fix, patterns library

#### Lab 6: Verification & Sign-Off
- **Mode:** Custom Verification Agent
- **Validate:** Fixes address root causes
- **Check:** Regression risks
- **Compare:** Before/after security posture
- **Document:** Verification evidence
- **Challenges:** Verify all fixes, before/after comparison, regression test suite

### OWASP Top 10 Coverage

| # | Vulnerability | Agent Checks |
|---|---------------|--------------|
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

### CLI Integration
```bash
# Security analysis
gh copilot explain "check this code for injection vulnerabilities:
$(cat src/api/userController.ts)"

# Secure patterns
gh copilot suggest "secure password hashing in Node.js"

# Config review
gh copilot explain -f config/security.json "identify security misconfigurations"

# Dependency check
gh copilot explain "security implications:
$(cat package.json | jq '.dependencies')"
```

### Key Outcomes
✅ Threat model with attack vectors  
✅ Reusable security scanner agent  
✅ Documented vulnerabilities with severity  
✅ Structured code review findings  
✅ Prioritized remediation plan  
✅ Verification evidence and sign-off  
✅ Continuous verification methodology

### Copilot Features Used
- Copilot CLI for security checks
- Copilot Chat with threat modeling
- OWASP pattern detection
- STRIDE methodology
- Evidence extraction
- Secure code generation

---

## Learning Paths

### Path 1: Full-Stack Developer Journey
**Recommended Order:** 1 → 4 → 3 → 2 → 5

1. **Spec-Driven Development** - Foundation for structured thinking
2. **Testing with Agents** - Quality assurance skills
3. **Debugging with Agents** - Problem-solving capabilities
4. **Migrate & Modernize** - Legacy code understanding
5. **Verify with Agents** - Security awareness

**Why:** Build from greenfield (spec) to quality (testing) to maintenance (debugging/modernization) to security.

### Path 2: Security-First Engineer
**Recommended Order:** 5 → 1 → 4 → 3 → 2

1. **Verify with Agents** - Security fundamentals
2. **Spec-Driven Development** - Security requirements in specs
3. **Testing with Agents** - Security test scenarios
4. **Debugging with Agents** - Security bug diagnosis
5. **Migrate & Modernize** - Secure modernization patterns

**Why:** Security-first mindset applied to all activities.

### Path 3: Platform Engineer / Tech Lead
**Recommended Order:** 2 → 3 → 5 → 1 → 4

1. **Migrate & Modernize** - Technical debt management
2. **Debugging with Agents** - Production incident response
3. **Verify with Agents** - Security governance
4. **Spec-Driven Development** - Architecture design
5. **Testing with Agents** - Quality standards

**Why:** Focus on production systems, technical leadership, and standards.

### Path 4: QA Engineer / SDET
**Recommended Order:** 4 → 1 → 3 → 5 → 2

1. **Testing with Agents** - Core testing skills
2. **Spec-Driven Development** - Understanding requirements
3. **Debugging with Agents** - Bug investigation
4. **Verify with Agents** - Security testing
5. **Migrate & Modernize** - Regression testing strategies

**Why:** Testing-centric with expanding scope into quality areas.

---

## Prerequisites

### Technical Requirements
- GitHub account with Copilot access
- VS Code installed with GitHub Copilot extension
- GitHub CLI (`gh`) installed (for Workshops 3, 5)
- Git basics (clone, commit, branch)

### Knowledge Prerequisites
- Intermediate programming experience in any language
- Basic understanding of software development lifecycle
- Familiarity with command-line interfaces
- For Workshop 2: .NET or Java experience
- For Workshop 4: Basic understanding of web applications
- For Workshop 5: Basic security awareness

### No Prerequisites Required
- ❌ AI/ML knowledge
- ❌ Prompt engineering expertise  
- ❌ Previous agent development experience
- ❌ Specific framework knowledge (provided in workshop)

---

## What Participants Receive

### During Workshop
- ✅ Pre-configured repository with workshop materials
- ✅ Starter prompts and templates
- ✅ Agent definition scaffolds
- ✅ Step-by-step guided labs
- ✅ Challenge-based scoring system

### Post-Workshop
- ✅ Workshop materials for reference
- ✅ Reusable agent definitions
- ✅ Prompt library for common tasks
- ✅ Achievement badge and score
- ✅ Recommended next steps
- ✅ Access to community/support channel

---

**Document Version:** 1.0  
**Last Updated:** February 12, 2026  
**Maintained by:** GitHub Copilot Workshop Team

---

*This catalog represents a comprehensive training program for GitHub Copilot adoption, focusing on practical, agent-driven workflows that deliver immediate value to development teams.*
