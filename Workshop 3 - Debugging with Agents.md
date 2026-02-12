# Workshop 3: Debugging with Agents

> _Using Copilot Chat as Your Debugging Partner_

---

## Executive Summary

**Duration:** 2 hours | **Audience:** Developers, Tech Leads | **Level:** Intermediate

**Core Concept:** Teach debugging as a structured conversation with AI, moving from trial-and-error to systematic problem-solving.

**Key Differentiator:** Uses Copilot Chat as-is (no custom agent setup), making this the most accessible agent workshop.

**Skills Taught:**
- Systematic debugging through AI conversation
- 5-phase debugging framework (Understand → Explore → Hypothesize → Fix → Learn)
- Pattern recognition for common bug types
- Knowledge capture for team learning

---

## 1. Workshop Purpose & Value Proposition

Transform debugging from reactive trial-and-error into a **structured, documented conversation** with AI.

**Participants learn to:**
- Partner with Copilot for systematic bug analysis
- Build debugging context progressively through dialogue
- Generate and validate hypotheses efficiently
- Document debugging journeys for team knowledge
- Extract reusable patterns from individual bugs

**Business Value:**
- Reduced time-to-resolution for bugs
- Better onboarding (debugging unfamiliar code with AI assistance)
- Team knowledge capture (debugging conversations become documentation)
- Consistent debugging approach across teams

---

## 2. Workshop Approach

### Core Methodology: Conversational Debugging

Unlike Workshops 2 & 4 which require custom agent definitions, this workshop uses **Copilot Chat directly**.

**Why this approach:**
- Lowest barrier to entry (no setup)
- Debugging needs flexibility, not rigid instructions
- Immediate applicability to daily work
- Focus on conversation patterns, not tool configuration

### The 5-Phase Framework

Each bug follows this conversation pattern:

1. **Understand** 🔍 - "What is this bug telling me?"
2. **Explore** 🗺️ - "What code is involved?"
3. **Hypothesize** 💡 - "What could cause this?"
4. **Fix** 🛠️ - "What's the right solution?"
5. **Learn** 📚 - "How do we prevent this?"

---

## 3. Repository Structure

Pre-provisioned repository with 3 intentionally buggy features:

```
/workshop-repo
├── app/src/
│   ├── calculator.js          # Bug 1: Logic error
│   ├── order-service.js       # Bug 2: Integration bug
│   └── cart-manager.js        # Bug 3: State management
├── tests/                     # Failing tests
├── debugging-journal/         # Guided templates
└── copilot-prompts/           # Conversation starters
```

**Design Principles:**
- Simple, focused codebase (not production complexity)
- Each bug demonstrates common pattern (80% coverage)
- Progressive difficulty
- Self-documenting through conversation

---

## 4. Workshop Agenda (120 minutes)

### Introduction (10 min)
- Traditional debugging challenges vs AI-assisted approach
- Overview of 5-phase framework
- Workshop flow and expectations

### Bug Pattern 1: Logic Error (40 min)
**Scenario:** Discount calculator fails for edge cases

| Phase | Time | Activities | Key Skills |
|-------|------|-----------|------------|
| Understand | 10m | Analyze test failures, reproduce bug | Reading errors with AI |
| Explore | 10m | Code walkthrough, identify edge cases | Systematic exploration |
| Hypothesize & Fix | 15m | Generate solutions, implement fix | Solution design |
| Learn | 5m | Create tests, document pattern | Knowledge capture |

**Outcome:** Fixed bug + documented pattern + regression tests

### Bug Pattern 2: Integration Bug (35 min)
**Scenario:** Service calls fail intermittently

| Phase | Time | Activities | Key Skills |
|-------|------|-----------|------------|
| Understand | 8m | Log analysis, identify failure patterns | Async debugging |
| Explore | 10m | Trace service integration, find gaps | Distributed systems |
| Hypothesize & Fix | 12m | Implement resilience patterns | Production-ready fixes |
| Learn | 5m | Document integration checklist | Team standards |

**Outcome:** Reliable integration + monitoring strategy

### Bug Pattern 3: State Management (25 min)
**Scenario:** Race condition in shopping cart

**Accelerated format:** Participants apply framework independently
- Understand (5m), Explore (5m), Hypothesize & Fix (10m), Learn (5m)

**Outcome:** Thread-safe implementation + concurrency guidelines

### Wrap-up (10 min)
- Framework review and discussion
- Building team debugging practice
- Next steps and resources

---

## 5. Learning Outcomes

**By end of workshop, participants can:**

✅ **Immediate Skills:**
- Apply 5-phase debugging framework
- Use Copilot Chat systematically for debugging
- Debug 3 common bug patterns (logic, integration, state)

✅ **Team Impact:**
- Document debugging journeys
- Build team debugging prompt library
- Create reusable pattern knowledge base

✅ **Long-term Value:**
- Reduce debugging time through structure
- Onboard faster on unfamiliar code
- Maintain debugging knowledge across team

---

## 6. Prerequisites & Setup

**Required:**
- GitHub Copilot subscription (Chat enabled)
- VS Code with Copilot extension
- Basic debugging experience

**Not Required:**
- Custom agent knowledge
- Advanced debugging skills
- Familiarity with workshop codebase

**Instructor Prep (30 min):**
- Seed 3 bugs in repository
- Test conversation flows with Copilot
- Prepare debugging journal templates

---

## 7. Optional: Advanced Path (Custom Agents)

For teams ready to scale their debugging practice:

**When to Add Custom Agents:**
- ✅ Repeating bug patterns in your domain
- ✅ Team-wide debugging standards to enforce
- ✅ Legacy system quirks to encode
- ✅ Compliance requirements

**Bonus Lab (20 min):** Build domain-specific debug agent
- Extract patterns from workshop bugs
- Create custom agent definition
- Apply to validate approach

**Evolution Path:**
Week 1-2 (Copilot Chat) → Week 3-4 (Document patterns) → Week 5+ (Custom agents)

---

## 8. Workshop Variants

Choose based on audience:

| Variant | Focus | Best For |
|---------|-------|----------|
| **A: Pattern-Based** (Default) | 3 bug patterns systematically | General audience |
| **B: Debug Archaeology** | Learn from historical bug fixes | Existing codebases |
| **C: Debug Sprint** | Competitive, time-boxed | Experienced devs |
| **D: Agent Evolution** | Compare Copilot vs custom agents | Advanced teams |

---

## 9. Differentiation from Other Workshops

| Aspect | Workshop 2 (Modernization) | **Workshop 3 (Debugging)** | Workshop 4 (Testing) |
|--------|---------------------------|--------------------------|----------------------|
| **Tool** | Custom agents | Copilot Chat (no custom) | Custom agents |
| **Complexity** | Medium | **Low** | Medium |
| **Setup** | Agent definitions required | None | Agent roles required |
| **Best For** | Specialized workflows | **Daily debugging** | Domain-specific QA |

**Why this matters:**
- Lowest barrier to entry → Highest adoption
- Immediately applicable → Instant ROI
- Extensible → Can add custom agents later

---

## 10. Success Metrics & Follow-up

**During Workshop:**
- All 3 bugs fixed and documented
- Debugging journals completed
- Pattern library started

**Post-Workshop (30 days):**
- Team using 5-phase framework
- Debugging prompt library growing
- Knowledge wiki established
- (Optional) Custom agents created for domain patterns

**Instructor Materials Needed:**
- Pre-seeded bug repository
- Debugging journal templates
- Sample conversation prompts
- Example solutions (instructor reference)
- Timing guide and facilitation notes

---

## 11. Content Development Plan

**Phase 1: Core Materials (Week 1-2)**
- [ ] Build workshop repository with 3 seeded bugs
- [ ] Create debugging journal templates
- [ ] Write conversation prompt starters
- [ ] Develop instructor guide with timing

**Phase 2: Testing & Refinement (Week 3)**
- [ ] Pilot with internal team
- [ ] Refine based on feedback
- [ ] Adjust timing and complexity

**Phase 3: Documentation (Week 4)**
- [ ] Finalize participant materials
- [ ] Create slide deck
- [ ] Record demo videos
- [ ] Prepare facilitator notes

---

_Outline prepared for Microsoft team review_
_Detailed content to be developed upon approval_
