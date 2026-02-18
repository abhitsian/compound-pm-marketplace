---
name: spec-review
description: Create comprehensive product specs through structured AskUserQuestion interviews or review existing specs against a detailed completeness checklist. Use when creating specs from scratch (no solution doc) or reviewing spec quality.
---

# Spec Review Skill

## Purpose

Provide two complementary spec workflows:
1. **Interview Mode** — Create specs from scratch by interviewing the PM using AskUserQuestion, gathering requirements through structured question groups
2. **Checklist Review Mode** — Analyze existing specs against a comprehensive completeness and quality checklist

## Interview Framework

### Question Categories (34 questions across 9 groups)

| Group | Questions | Focus |
|-------|-----------|-------|
| **A. Problem & Context** | 1-4 | User pain, persona, goals, business justification |
| **B. Scope & Prioritization** | 5-7 | MVP vs future, dependencies, constraints |
| **C. User Flows & Experience** | 8-12 | Happy path, entry points, UI layout, feedback, responsive |
| **D. Business Logic & Validation** | 13-16 | Input rules, business rules, data dependencies, limits |
| **E. Edge Cases & Error Handling** | 17-20 | Errors, error communication, concurrency, boundaries |
| **F. Permissions & Security** | 21-24 | Access control, role permissions, privacy, security risks |
| **G. Cross-Cutting Concerns** | 25-28 | Accessibility, loading states, offline, existing patterns |
| **H. Success Metrics** | 29-31 | KPIs, analytics tracking, launch criteria |
| **I. Assumptions & Risks** | 32-34 | Assumptions, open questions, failure modes |

### Interview Strategy with AskUserQuestion

**Rules:**
- Ask questions in logical groups (2-3 questions per AskUserQuestion call)
- Start with problem/context, then move to scope, flows, logic, edge cases
- Make questions conversational but specific
- Don't ask obvious questions — dig into non-obvious concerns
- Probe for hidden assumptions and edge cases
- Ask follow-up questions based on previous answers
- Continue until all sections of the template are covered
- Focus on functional/product aspects, not deep technical implementation

**AskUserQuestion Pattern:**
- Use 2-3 questions per call for related topics
- Make options concrete and specific to their project
- Follow up on vague or incomplete answers
- Surface hidden assumptions proactively
- Ask "what happens if..." questions for edge cases
- Clarify MVP vs. future scope explicitly

### Example Questions (Non-Obvious Probes)

Instead of: "What are the requirements?"
Ask: "What happens when a user tries to [action] but [constraint]? Should we show an error, disable the button, or handle it differently?"

Instead of: "How should this work?"
Ask: "If two users are editing the same item simultaneously, should we lock it, show a warning, auto-merge, or let the last save win?"

Instead of: "What validations do you need?"
Ask: "For the email field, should we validate format on blur or submit? What's the exact error message? Are temporary email addresses like 10minutemail allowed?"

## Review Checklist Framework

### Completeness Check

**Problem & Context:**
- Clear problem statement that explains user pain
- Identified target users/personas
- Business justification is clear
- Success metrics defined

**Scope:**
- MVP scope clearly defined
- Non-goals/out-of-scope items listed
- Dependencies identified
- Constraints documented

**User Experience:**
- Primary user flow documented step-by-step
- UI layout and components described
- Entry and exit points clear
- All UI states covered (loading, empty, error, success)
- Responsive behavior specified

**Business Logic:**
- Input validation rules are specific and complete
- Business rules documented with examples
- Data dependencies identified
- Calculations/formulas specified

**Edge Cases:**
- Error scenarios identified with user-facing messages
- Edge cases considered and documented
- Data integrity addressed
- Concurrent usage/conflicts handled

**Security & Access:**
- Permission model defined
- PII and privacy considerations addressed
- Security risks identified

**Accessibility:**
- Keyboard navigation specified
- Screen reader support considered
- Visual accessibility requirements noted

**Metrics:**
- KPIs defined with targets
- Analytics events specified
- Success criteria established

**Risks & Assumptions:**
- Key assumptions documented
- Risks identified with mitigations
- Open questions captured

### Quality Check

| Dimension | Criteria |
|-----------|---------|
| **Clarity** | Understandable by all audiences; no ambiguous language; acceptance criteria are testable; error messages written exactly |
| **Consistency** | Terminology used consistently; no contradictions; follows existing patterns |
| **Completeness** | Engineer implements without questions; designer creates mockups; QA writes test cases; all interactions have outcomes |
| **Realism** | Technically feasible; timeline achievable; dependencies available; constraints respected |

### Red Flags

- Vague acceptance criteria ("works well", "is intuitive")
- Missing error handling or edge cases
- No consideration of empty/loading states
- Undefined validation rules for user input
- No metrics or success criteria
- Missing permission/access control
- Undocumented assumptions about user behavior
- Overlooking mobile/responsive considerations
- No accessibility requirements

### Review Output Classification

| Priority | Criteria |
|----------|---------|
| **Critical** | Must-fix before implementation — blocks eng, design, or QA |
| **Important** | Should-fix for quality — spec works but has gaps |
| **Nice-to-have** | Would improve but not blocking — polish items |

## Spec Quality Bar

A complete spec enables:
- **Engineers** to implement without asking clarifying questions
- **Designers** to create mockups with full context
- **QA** to write comprehensive test cases from acceptance criteria
- **Stakeholders** to understand value and tradeoffs

## Reference

The full spec template with all 34 interview questions, 14-section spec structure, and review checklist is available in `references/spec-template.md`.
