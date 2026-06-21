# github-contribution-log
GitHub contribution log for CodePath Summer - AI 301

# Contribution [1]: [[React Doctor] alt-text: Missing alt attribute (14 occurrences)]

**Contribution Number:** [1]  
**Student:** [Dhruvi Rana]  
**Issue:** Issue #27869 - [[GitHub issue link](https://github.com/wso2/product-is/issues/27869)]
**Status:** [Phase I Complete]

---

## Why I Chose This Issue

[1-2 paragraphs explaining why this issue interests you, how it matches your skills/learning goals, what you hope to learn]

This issue interests me because it focuses on improving accessibility for users. Ensuring that websites are usable by everyone, including people who rely on assistive technologies such as screen readers, is an important part of creating an inclusive user experience.

Relevant experience and goals:

* Experience working with JavaScript, TypeScript, and CSS projects.
* Interested in gaining experience contributing to open-source projects and working with a larger codebase.
* Looking to learn more about accessibility best practices in real-world applications.

Based on the issue description and linked files, I understand that I need to add appropriate alt attributes to images, using `alt=""` for decorative images and descriptive alt text for non-decorative images. I have already introduced myself on the issue, and the maintainer has assigned it to me.

---

## Understanding the Issue

### Problem Description

[In your own words, what's broken or missing?]

14 <img> tags across the codebase are missing alt attributes, violating the react-doctor/alt-text ESLint rule at error severity. This is an accessibility issue that affects users who rely on screen readers.

### Expected Behavior

[What should happen?]

The reported <img> tags should have alt attributes. Decorative images should use alt="" and non-decorative images should have descriptive alt="..." or use aria-label or aria-labelledby. 

### Current Behavior

[What actually happens?]

14 <img> tags across 11 files are missing alt attributes and are flagged as errors by the react-doctor/alt-text rule.

### Affected Components

[Which parts of the codebase are involved?]

Affected files: 
./features/admin.application-templates.v1/components/application-template-card.tsx
./features/admin.core.v1/components/modals/feature-preview-modal.tsx
./features/admin.flow-builder-core.v1/components/resources/elements/adapters/button-adapter.tsx
./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/apple-execution.tsx
./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/facebook-execution.tsx
./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/github-execution.tsx
./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/google-execution.tsx
./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/microsoft-execution.tsx
./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/index.tsx
./features/admin.login-flow-builder.v1/components/nodes/sign-in-box-node/sign-in-box-node.tsx
./features/admin.push-providers.v1/components/push-provider-card.tsx

These are also the same files mentioned in the comment on the issue page. 
---

## Reproduction Process

### Environment Setup

[Notes on setting up your local development environment - challenges you faced, how you solved them]

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
