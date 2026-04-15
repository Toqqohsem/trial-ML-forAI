# Context Engineering Workflow for AI-Assisted Software Development

> Based on Zainul Zain's 2026 Workflow methodology

---

## Overview

This workflow replaces the old "AI Pair Programming" approach where AI only assists during coding. Instead, AI is integrated into **all phases** of software development through proper context engineering.

### The Old Way vs. The New Way

| Old Way (AI Pair Programming) | New Way (Context Engineering) |
|-------------------------------|-------------------------------|
| Human Think/Design | AI-assisted Brainstorming |
| Human Plans | AI-generated Specs & Plans |
| Human codes, AI helps | AI Codes with detailed context |
| Human debug while cursing AI | Multi-AI Review + Human Review |

---

## Part 1: THE HOW — Agent Rules

To stay in control when AI handles all phases, you must define **how** AI should work. This is done through agent rule files:

- **Cursor**: `.cursorrule`
- **Codex**: `AGENTS.md`
- **Claude Code**: `CLAUDE.md`

### What to Include in Agent Rules

```
1. Tech Stack
   - Languages, frameworks, versions
   - Required dependencies

2. Architecture Rules
   - Design patterns to follow
   - Separation of concerns
   - Dependency injection requirements

3. Project Structure
   - Folder organization
   - File naming conventions
   - Module boundaries

4. Feature Delivery Workflow
   - How features should be implemented
   - Data pipeline setup
   - State management approach

5. Testing Policy
   - TDD requirements
   - Test coverage expectations
   - Types of tests (unit, integration, e2e)

6. Database Rules
   - Schema conventions
   - Migration practices
   - Query patterns

7. Error Handling Contract
   - Error response formats
   - Logging requirements
   - Recovery strategies

8. Definition of Done
   - Checklist AI must complete
   - Quality gates
   - Documentation requirements

9. Docs & Evidence Rules
   - Where to save reports
   - Format of completion reports
   - Test evidence requirements

10. Environment & Config
    - Environment variable handling
    - Config file locations
    - Secrets management
```

---

## Part 2: THE WHAT — Documentation Workflow

This pipeline ensures AI produces exactly what you expect through progressive refinement.

### Folder Structure

```
project/
├── docs/
│   ├── 10-drafts/           # Ideas and concept documents
│   ├── 20-specs/            # Full specification documents
│   ├── 30-scoped-specs/     # Module-level specifications
│   ├── 40-plans/            # Detailed implementation plans
│   ├── 50-implementations/  # Code completion reports
│   └── 60-evidence/         # Test run results and evidence
```

### The Pipeline

```
┌─────────────────┐
│   IDEA/CONCEPT  │
│   (Brain Dump)  │
└────────┬────────┘
         │ AI generates
         ▼
┌─────────────────┐     ┌──────────┐
│   10-drafts/    │────▶│  REVIEW  │
│  Product Idea   │     │ (Human)  │
└─────────────────┘     └────┬─────┘
                             │ Satisfied?
                             ▼
┌─────────────────┐     ┌──────────┐
│    20-specs/    │◀────│  REVIEW  │
│    Full Spec    │     │ (Human)  │
└────────┬────────┘     └──────────┘
         │
         │ Contains:
         │ • Functional Requirements
         │ • Full Schema
         │ • API Contracts
         │ • Acceptance Criteria
         │
         ▼
┌─────────────────┐     ┌──────────┐
│ 30-scoped-specs/│────▶│  REVIEW  │
│ Module Breakdown│     │ (Human)  │
└────────┬────────┘     └────┬─────┘
         │                   │
         │ Adds:             │
         │ • Module Boundaries
         │ • FR Subset       │
         │ • Validation      │
         │ • Edge Cases      │
         │                   │
         ▼                   │
┌─────────────────┐     ┌────┴─────┐
│    40-plans/    │◀────│  REVIEW  │
│  Detailed Plan  │     │ (Human)  │
└────────┬────────┘     └──────────┘
         │
         │ Step-by-step actions
         │
         ▼
┌─────────────────┐
│ CODE EXECUTION  │
└────────┬────────┘
         │
         ├────────────────────┐
         ▼                    ▼
┌─────────────────┐  ┌─────────────────┐
│50-implementations│  │   60-evidence/  │
│Completion Report│  │  Test Results   │
└────────┬────────┘  └────────┬────────┘
         │                    │
         └─────────┬──────────┘
                   ▼
              ┌──────────┐
              │  REVIEW  │
              │ (Human)  │
              └────┬─────┘
                   │
                   │ Issues found?
                   │ Generate fix plan
                   │ Return to execution
                   ▼
              ┌──────────┐
              │   DONE   │
              │ (Module) │
              └──────────┘
                   │
                   │ Next module
                   ▼
              [Repeat for each module]
```

---

## Part 3: Multi-AI Strategy

Different AI models excel at different tasks. Use them strategically:

| Phase | Recommended AI | Why |
|-------|----------------|-----|
| Brainstorming | ChatGPT / Claude | Creative, conversational |
| Spec Generation | ChatGPT / Claude | Good at structured docs |
| Detailed Planning | Claude Opus 4.5 | Strong reasoning, thorough |
| Code Generation | Claude Sonnet 4.5 / GPT-5.2 | Fast, accurate coding |
| Code Review | Claude Opus 4.5 | Deep analysis |
| Co-Review | Gemini 3 / Grok | Different perspective |

### Review Loop

```
         ┌─────────────────────────────────────┐
         │           HUMAN REVIEW              │
         │         (Central Control)           │
         └──────────────┬──────────────────────┘
                        │
    ┌───────────────────┼───────────────────┐
    │                   │                   │
    ▼                   ▼                   ▼
┌────────┐       ┌────────────┐       ┌──────────┐
│AI Code │       │ AI Review  │       │AI Co-Rev │
│Review  │       │   Codes    │       │(2nd AI)  │
│(Opus)  │       │  (Sonnet)  │       │(Gemini)  │
└────────┘       └────────────┘       └──────────┘
```

---

## Part 4: Prompt Templates

### 1. Idea/Concept Prompt

```markdown
You are a product analyst. Based on my brain dump below, create a 
structured Product Concept document.

## Brain Dump:
[Your raw ideas here]

## Output Format:
- Product Name
- Problem Statement
- Proposed Solution
- Key Features (bullet points)
- Target Users
- Success Metrics

Save to: docs/10-drafts/[product-name]-concept.md
```

### 2. Full Spec Prompt

```markdown
Based on the product concept in [link to concept doc], generate a 
Full Specification document with these sections:

1. **Functional Requirements**
   - User stories
   - Feature descriptions
   - Business rules

2. **Data Schema**
   - Entity definitions
   - Relationships
   - Field specifications

3. **API Contracts**
   - Endpoints
   - Request/Response formats
   - Authentication requirements

4. **Acceptance Criteria**
   - Testable conditions
   - Edge cases
   - Performance requirements

Save to: docs/20-specs/[product-name]-full-spec.md
```

### 3. Scoped Spec Prompt (Module Breakdown)

```markdown
Based on the full spec at [link to full spec], create a Scoped 
Specification for the [MODULE NAME] module.

Include:
1. **Module Boundaries**
   - What this module handles
   - What it does NOT handle
   - Dependencies on other modules

2. **Functional Requirements Subset**
   - Specific features for this module
   - User interactions

3. **Validation Rules**
   - Input validation
   - Business rule validation

4. **Edge Cases**
   - Error scenarios
   - Boundary conditions

Save to: docs/30-scoped-specs/[module-name]-scope-spec.md
```

### 4. Detailed Plan Prompt

```markdown
Based on the scoped spec at [link to scoped spec], create a 
Detailed Implementation Plan.

Format each step as:
- Step number
- Action (single unit of work)
- Files affected
- Dependencies
- Verification method

The plan should be executable step-by-step by an AI coding agent.

Save to: docs/40-plans/[module-name]-plan.md
```

### 5. Execution Prompt

```markdown
Execute the implementation plan at [link to plan] step by step.

Rules:
- Follow agent rules in CLAUDE.md
- Run tests after each significant change
- Document any deviations

On completion, generate:
1. Completion Report → docs/50-implementations/[module-name]-completion.md
2. Test Evidence → docs/60-evidence/[module-name]-tests.md
```

### 6. Scaffolding Prompt

```markdown
Based on the full spec at [link to full spec] and agent rules, 
scaffold the project structure.

Create:
- Folder structure per project conventions
- Base configuration files
- Initial boilerplate
- README with setup instructions

Save scaffolding plan to: docs/10-drafts/scaffold-plan.md
Then execute the scaffolding.
```

---

## Part 5: Practical Execution Checklist

### Per Module Workflow

- [ ] **Draft Phase**
  - [ ] Brain dump idea to AI
  - [ ] Generate concept document
  - [ ] Human review → iterate until satisfied

- [ ] **Spec Phase**
  - [ ] Generate full spec from concept
  - [ ] Human review → iterate until satisfied
  - [ ] Break into scoped specs (if multi-module)
  - [ ] Human review each scoped spec

- [ ] **Plan Phase**
  - [ ] Generate detailed plan from scoped spec
  - [ ] Human review plan
  - [ ] Ask AI to explain unclear steps
  - [ ] Finalize plan

- [ ] **Execute Phase**
  - [ ] Run execution prompt
  - [ ] AI generates code following plan
  - [ ] AI runs tests
  - [ ] AI generates completion report
  - [ ] AI generates test evidence

- [ ] **Review Phase**
  - [ ] Human reviews completion report
  - [ ] Human reviews test evidence
  - [ ] Run secondary AI review
  - [ ] Fix issues (generate fix plan → re-execute)
  - [ ] Mark module complete

- [ ] **Next Module**
  - [ ] Proceed to next scoped spec
  - [ ] Repeat entire workflow

---

## Part 6: Tips & Best Practices

1. **Never skip human review** — This is your control point

2. **Use different AIs for review** — Catches different issues

3. **Keep plans atomic** — Each step should be one unit of action

4. **Trust but verify** — AI can explain its decisions; ask when confused

5. **Maintain folder discipline** — Always save to correct numbered folders

6. **Test-driven development** — Let AI write tests; they catch regressions

7. **Iterate quickly** — Small review loops are better than big rewrites

8. **Document deviations** — If AI does something unexpected, document it

---

## Quick Reference

```
WORKFLOW SUMMARY:
─────────────────
Brain Dump → Concept (10) → Full Spec (20) → Scoped Spec (30) 
→ Detail Plan (40) → Execute → Implementation (50) + Evidence (60)
→ Review → Next Module → Repeat

CONTROL POINTS:
───────────────
THE HOW = Agent Rules (tech stack, architecture, DoD)
THE WHAT = Documentation Pipeline (progressive refinement)

AI ASSIGNMENT:
─────────────
Brainstorm: ChatGPT/Claude
Spec: ChatGPT/Claude  
Plan: Opus 4.5
Code: Sonnet 4.5 / GPT-5.2
Review: Opus 4.5 + Gemini 3
```

---

*Adapted from Zainul Zain's Context Engineering Workflow (2026)*
