# Product Specification Guide

This document serves as both a template for writing product specs and an interview guide for gathering comprehensive product requirements.

---

## PART 1: INTERVIEW QUESTIONNAIRE

Use these questions when gathering requirements for a new feature or product. The goal is to surface assumptions, understand user needs, define scope, and document business logic comprehensively.

### A. PROBLEM & CONTEXT

1. **What specific user problem are we solving?**
   - What pain point or friction does this address?
   - What happens today when users try to accomplish this?
   - How critical/frequent is this problem?

2. **Who is the target user/persona?**
   - Primary user type(s)?
   - User technical proficiency level?
   - What's their current workflow/tools for this task?

3. **What is the user's goal/desired outcome?**
   - What does success look like from their perspective?
   - What are they trying to accomplish?
   - What constraints or context affects their usage?

4. **Why are we building this now?**
   - Business justification/driver?
   - Strategic importance?
   - Dependencies or blockers being solved?

### B. SCOPE & PRIORITIZATION

5. **What is the MVP scope vs. future enhancements?**
   - What is the minimum viable version?
   - What features are must-haves vs. nice-to-haves?
   - What are we explicitly NOT doing in v1?

6. **Are there any dependencies or prerequisites?**
   - Does this require other features to exist first?
   - Integration with existing systems?
   - Data/content that needs to be ready?

7. **What are the constraints?**
   - Technical limitations we must work within?
   - Performance requirements (speed, size limits)?
   - Platform/browser/device support?
   - Compliance or legal requirements?

### C. USER FLOWS & EXPERIENCE

8. **What is the primary user flow (happy path)?**
   - Step-by-step: how does a user accomplish the goal?
   - What UI elements/screens are involved?
   - What actions does the user take at each step?
   - Where does this flow start and end?

9. **What are the entry points to this feature?**
   - How do users discover/access this?
   - Navigation paths?
   - Deep links or external triggers?

10. **What is the UI layout and key components?**
    - Describe the visual structure (header, sidebar, main area, etc.)
    - What interactive elements exist? (buttons, forms, dropdowns, etc.)
    - What information is displayed?
    - How is information grouped/organized?

11. **What feedback does the user receive?**
    - Success messages?
    - Loading/progress indicators?
    - Confirmation dialogs?
    - Empty states (when no data exists)?

12. **What happens on mobile vs. desktop?**
    - Are there responsive design considerations?
    - Any features that work differently on mobile?
    - Touch-specific interactions?

### D. BUSINESS LOGIC & VALIDATION

13. **What are the validation rules for user inputs?**
    - Required vs. optional fields?
    - Data type constraints (string, number, date, etc.)?
    - Format requirements (email, phone, regex patterns)?
    - Min/max length or value constraints?
    - Allowed/forbidden characters?

14. **What business rules govern this feature?**
    - Conditional logic ("if X then Y")?
    - State transitions and what triggers them?
    - Calculations or derived values?
    - Workflow rules or approval processes?

15. **What are the data dependencies?**
    - What data needs to exist before this works?
    - Where does data come from (user input, API, database)?
    - How is data transformed or processed?
    - What data is created/updated/deleted?

16. **Are there limits or quotas?**
    - Maximum number of items?
    - Rate limits or throttling?
    - Storage or file size limits?
    - Concurrent usage limits?

### E. EDGE CASES & ERROR HANDLING

17. **What are the error scenarios?**
    - What can go wrong at each step?
    - Network failures or timeouts?
    - Invalid data scenarios?
    - Backend errors or unavailability?

18. **How should errors be communicated to users?**
    - Error message wording?
    - Recoverable vs. fatal errors?
    - Retry mechanisms?
    - Fallback behaviors?

19. **What happens with concurrent/conflicting actions?**
    - Multiple users editing the same thing?
    - Stale data or race conditions?
    - Optimistic vs. pessimistic locking?

20. **What are the boundary cases?**
    - Empty/zero state?
    - Maximum values or overflow?
    - First-time user vs. returning user?
    - Deleted or archived items?

### F. PERMISSIONS & SECURITY

21. **Who can access this feature?**
    - Authentication required?
    - Role-based access control?
    - User types/tiers with different access?

22. **What actions can different user types perform?**
    - Read-only vs. edit permissions?
    - Admin/moderator capabilities?
    - Owner vs. collaborator rights?

23. **What data privacy considerations exist?**
    - PII (Personally Identifiable Information)?
    - Data visibility (who can see what)?
    - Data retention/deletion policies?
    - GDPR, CCPA, or other compliance?

24. **Are there security risks to consider?**
    - User-generated content concerns?
    - XSS, CSRF, injection vulnerabilities?
    - Sensitive data exposure?
    - Audit logging requirements?

### G. CROSS-CUTTING CONCERNS

25. **How should this feature work for users with disabilities?**
    - Keyboard navigation support?
    - Screen reader compatibility?
    - Color contrast and visual accessibility?
    - Alternative text for images/icons?

26. **What happens when data is loading?**
    - Skeleton screens vs. spinners?
    - Lazy loading or pagination?
    - Optimistic UI updates?

27. **Is there an offline or degraded mode?**
    - What happens with no internet connection?
    - Graceful degradation strategy?
    - Offline data persistence?

28. **What existing patterns should this follow?**
    - Design system components to use?
    - Interaction patterns from other features?
    - Terminology and labeling consistency?

### H. SUCCESS METRICS & ANALYTICS

29. **How do we measure success?**
    - Primary KPI for this feature?
    - Leading vs. lagging indicators?
    - Quantitative metrics (usage, conversion, time, etc.)?
    - Qualitative metrics (satisfaction, feedback)?

30. **What analytics/tracking is needed?**
    - Events to track?
    - User actions to measure?
    - Funnel or conversion tracking?
    - A/B testing requirements?

31. **What are the success criteria for launch?**
    - Adoption targets?
    - Performance benchmarks?
    - Error rate thresholds?
    - User feedback goals?

### I. ASSUMPTIONS & OPEN QUESTIONS

32. **What assumptions are we making?**
    - User behavior assumptions?
    - Technical assumptions?
    - Business assumptions?
    - Which assumptions are highest risk?

33. **What open questions remain?**
    - Unknowns that need research?
    - Decisions that need stakeholder input?
    - Areas needing design exploration?

34. **What could cause this to fail?**
    - Technical risks?
    - User adoption risks?
    - Business risks?
    - Mitigation strategies?

---

## PART 2: PRODUCT SPEC TEMPLATE

Use this structure when documenting a feature or product specification.

---

# [Feature/Product Name]

**Status:** [Draft | In Review | Approved | In Development | Shipped]
**Owner:** [Product Manager Name]
**Engineering Lead:** [Name]
**Design Lead:** [Name]
**Target Release:** [Date or Version]
**Last Updated:** [Date]

---

## 1. OVERVIEW

### 1.1 Problem Statement
[2-3 sentences describing the user problem this solves]

### 1.2 Solution Summary
[2-3 sentences describing what we're building]

### 1.3 Goals
- [Primary goal]
- [Secondary goal]
- [Secondary goal]

### 1.4 Non-Goals (Out of Scope)
- [What we're explicitly NOT doing]
- [Future considerations]

---

## 2. USER CONTEXT

### 2.1 Target Users/Personas
**Primary Persona:** [Name/Type]
- Role/Job title
- Technical proficiency
- Current workflow/pain points
- Key needs

**Secondary Persona:** [Name/Type] (if applicable)
- Role/Job title
- Technical proficiency
- Current workflow/pain points
- Key needs

### 2.2 User Stories
As a [user type], I want to [action] so that [benefit].

**Primary User Stories:**
1. As a [user], I want to [action] so that [benefit]
2. As a [user], I want to [action] so that [benefit]
3. ...

**Secondary User Stories (Future):**
1. As a [user], I want to [action] so that [benefit]
2. ...

---

## 3. FUNCTIONAL REQUIREMENTS

### 3.1 MVP Features (Must-Have)
1. **[Feature Name]**
   - Description: [What it does]
   - User Benefit: [Why it matters]
   - Acceptance Criteria:
     - [ ] [Specific, testable criterion]
     - [ ] [Specific, testable criterion]
     - [ ] [Specific, testable criterion]

2. **[Feature Name]**
   - Description: [What it does]
   - User Benefit: [Why it matters]
   - Acceptance Criteria:
     - [ ] [Specific, testable criterion]
     - [ ] [Specific, testable criterion]

### 3.2 Post-MVP Features (Nice-to-Have)
1. **[Feature Name]**
   - Description: [What it does]
   - User Benefit: [Why it matters]
   - Rationale for deferring: [Why not MVP]

---

## 4. USER FLOWS

### 4.1 Primary Flow (Happy Path)

**Entry Point:** [Where user starts]

**Flow:**
1. User [action/sees]
   - UI: [Description of what's visible]
   - Interaction: [What user does]

2. User [action/sees]
   - UI: [Description of what's visible]
   - Interaction: [What user does]

3. System [responds/displays]
   - UI: [Description of what's visible]
   - Feedback: [What user sees as confirmation]

4. [Continue step-by-step...]

**Exit Point:** [Where flow ends]

### 4.2 Alternative Flows

**Flow Name:** [e.g., "Edit Existing Item"]
1. [Step-by-step description]
2. ...

**Flow Name:** [e.g., "Bulk Operations"]
1. [Step-by-step description]
2. ...

---

## 5. UI SPECIFICATIONS

### 5.1 Layout & Components

**[Screen/Page Name]**

Structure:
- [Header/Navigation area]
  - Contains: [list components like logo, nav links, user menu]
- [Main content area]
  - Contains: [describe sections, cards, lists]
- [Sidebar/Secondary area] (if applicable)
  - Contains: [describe what's here]
- [Footer] (if applicable)

Interactive Elements:
- **[Button/Link Name]:** [Purpose, what happens when clicked]
- **[Form Field Name]:** [Type, purpose, validation]
- **[Dropdown/Menu Name]:** [Options, behavior]
- **[Other element]:** [Description]

### 5.2 UI States

**Loading State:**
- [Describe what user sees while waiting]
- [Loading indicator type and placement]

**Empty State:**
- [What shows when no data/content exists]
- [Call-to-action or guidance for user]

**Error State:**
- [What shows when something fails]
- [How user can recover]

**Success State:**
- [Confirmation message or indication]
- [Next steps for user]

### 5.3 Responsive Behavior

**Desktop (>1024px):**
- [Layout adjustments]
- [Specific desktop-only features]

**Tablet (768px - 1024px):**
- [Layout adjustments]
- [Differences from desktop]

**Mobile (<768px):**
- [Layout adjustments]
- [Mobile-specific interactions]
- [Simplified or hidden features]

---

## 6. BUSINESS LOGIC & VALIDATION

### 6.1 Input Validation Rules

**[Field Name 1]:**
- Type: [text | number | email | date | etc.]
- Required: [Yes | No]
- Format: [Specific format like "XXX-XXX-XXXX" for phone]
- Min/Max: [Character or value limits]
- Validation: [Regex pattern or rule description]
- Error Message: "[Exact message text]"

### 6.2 Business Rules

**Rule 1: [Rule Name]**
- Condition: When [trigger condition]
- Action: Then [what happens]
- Example: [Concrete example scenario]

### 6.3 State Transitions

States:
- **[State Name]:** [Description of what this state means]
- **[State Name]:** [Description of what this state means]

Valid Transitions:
- [State A] -> [State B]: When [condition/action]
- [State B] -> [State C]: When [condition/action]

### 6.4 Calculations & Derived Data

**[Calculated Field Name]:**
- Formula: [Exact calculation]
- Example: [Concrete example with numbers]
- Rounding: [How to handle decimals]

---

## 7. EDGE CASES & ERROR HANDLING

### 7.1 Error Scenarios

| Scenario | Cause | User Experience | Error Message |
|----------|-------|-----------------|---------------|
| [Error type] | [What triggers it] | [What user sees] | "[Exact message text]" |

### 7.2 Edge Cases

**Case 1: [Name of edge case]**
- Scenario: [Describe the unusual situation]
- Expected Behavior: [What should happen]
- Fallback: [If ideal behavior isn't possible]

**Common Edge Cases to Consider:**
- First-time user with no data
- Maximum limit reached
- Deleted/archived items referenced
- Concurrent edits by multiple users
- Very large data sets (>1000 items)
- Special characters in text input
- Extremely long text input
- Missing or incomplete data
- Stale/cached data

### 7.3 Data Integrity

**Duplicate Prevention:**
- [How system prevents/handles duplicates]

**Data Loss Prevention:**
- [Auto-save, confirmations, undo mechanisms]

**Conflict Resolution:**
- [How system handles concurrent edits]

---

## 8. PERMISSIONS & SECURITY

### 8.1 Access Control

| User Type | Can View | Can Create | Can Edit | Can Delete |
|-----------|----------|------------|----------|------------|
| [Role 1] | Y | Y | Y | Y |
| [Role 2] | Y | Y | N | N |
| Anonymous | N | N | N | N |

### 8.2 Data Privacy

**PII Handling:**
- [What PII is collected]
- [How it's protected]
- [Who can access it]
- [Retention policy]

### 8.3 Security Considerations

- [Input sanitization approach]
- [XSS prevention]
- [CSRF protection]
- [Authentication requirements]
- [Audit logging needs]

---

## 9. ACCESSIBILITY

### 9.1 WCAG Compliance Level
Target: [A | AA | AAA]

### 9.2 Accessibility Requirements

**Keyboard Navigation:**
- All interactive elements accessible via Tab
- Logical tab order
- Visible focus indicators

**Screen Reader Support:**
- Semantic HTML used
- ARIA labels for custom components
- Alt text for all images
- Form labels properly associated

**Visual Accessibility:**
- Color contrast ratio >4.5:1 for text
- No information conveyed by color alone
- Text resizable to 200% without loss of function

---

## 10. SUCCESS METRICS & ANALYTICS

### 10.1 Key Performance Indicators (KPIs)

**Primary KPI:**
- Metric: [Specific metric name]
- Target: [Specific target value]
- Measurement: [How it's calculated]

### 10.2 Analytics Tracking

**Events to Track:**
- Event: `[event_name]`
  - When: [Trigger condition]
  - Properties: [Data to capture]

**Funnel/Conversion Tracking:**
- Step 1: [Event/action]
- Step 2: [Event/action]
- Conversion: [Final goal]

### 10.3 Success Criteria

**Launch Criteria:**
- [Specific requirement for go-live]

**Post-Launch Targets (30 days):**
- [Metric]: [Target value]

---

## 11. DEPENDENCIES & CONSTRAINTS

### 11.1 Technical Dependencies
- [System/service this relies on]

### 11.2 Design Dependencies
- [Mockups/wireframes needed]

### 11.3 Content Dependencies
- [Copy/content that must be written]

### 11.4 Constraints
- Performance: [Requirements like page load <2s]
- Platform: [Browser/device support needed]
- Compliance: [Legal/regulatory requirements]

---

## 12. ASSUMPTIONS & RISKS

### 12.1 Assumptions

| Assumption | Impact if Wrong | Validation Approach |
|------------|-----------------|---------------------|
| [Statement] | [Consequence] | [How to verify] |

### 12.2 Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| [Description] | [H/M/L] | [H/M/L] | [How to reduce] |

### 12.3 Open Questions
- [Question that needs answering]

---

## 13. RELEASE PLAN

### 13.1 Rollout Strategy
- [Phased rollout approach]

### 13.2 Testing Plan
- [Critical path test]
- [Edge case test]
- [Cross-browser/device test]
- [Accessibility test]

### 13.3 Launch Checklist
- [ ] Feature complete and code reviewed
- [ ] QA testing passed
- [ ] Accessibility audit passed
- [ ] Performance benchmarks met
- [ ] Analytics tracking implemented
- [ ] Documentation updated
- [ ] Support team trained
- [ ] Rollback plan documented

---

## 14. APPENDIX

### 14.1 Related Documents
- Design mockups: [Link]
- User research: [Link]
- Technical design doc: [Link]

### 14.2 Revision History

| Date | Author | Changes |
|------|--------|---------|
| [Date] | [Name] | [Summary] |

### 14.3 Stakeholder Sign-Off
- [ ] Product Manager: [Name] - [Date]
- [ ] Engineering Lead: [Name] - [Date]
- [ ] Design Lead: [Name] - [Date]

---

## PART 3: SPEC REVIEW CHECKLIST

See the `spec-review` SKILL.md for the complete review checklist framework used in both automated review and interview modes.
