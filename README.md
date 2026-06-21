# github-contribution-log
GitHub contribution log for CodePath Summer - AI 301

# Contribution [1]: [[React Doctor] alt-text: Missing alt attribute (14 occurrences)]

**Contribution Number:** [1]  
**Student:** [Dhruvi Rana]  
**Issue:** #27869 - [[GitHub issue link](https://github.com/wso2/product-is/issues/27869)]
**Status:** [Phase II Complete]

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

14 <img> tags across the codebase are missing alt attributes, violating the react-doctor/alt-text ESLint rule at error severity. This is an accessibility issue that affects users who rely on screen readers.

### Expected Behavior

The reported `<img>` tags should have alt attributes. Decorative images should use alt="" and non-decorative images should have descriptive alt="..." or use aria-label or aria-labelledby. 

### Current Behavior

[What actually happens?]

14 `<img>` tags across 11 files are missing alt attributes and are flagged as errors by the react-doctor/alt-text rule.

### Affected Components

[Which parts of the codebase are involved?]

Affected files: 
1. ./features/admin.application-templates.v1/components/application-template-card.tsx
2. ./features/admin.core.v1/components/modals/feature-preview-modal.tsx
3. ./features/admin.flow-builder-core.v1/components/resources/elements/adapters/button-adapter.tsx
4. ./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/apple-execution.tsx
5. ./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/facebook-execution.tsx
6. ./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/github-execution.tsx
7. ./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/google-execution.tsx
8. ./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/microsoft-execution.tsx
9. ./features/admin.flow-builder-core.v1/components/resources/steps/execution/execution-factory/index.tsx
10. ./features/admin.login-flow-builder.v1/components/nodes/sign-in-box-node/sign-in-box-node.tsx
11. ./features/admin.push-providers.v1/components/push-provider-card.tsx

These are also the same files mentioned in the comment on the issue page. 

---

## Reproduction Process

### Environment Setup

Used the README and CONTRIBUTING.md of the repo to complete the environment setup. It took approximately 3 hours to install all prerequisites (JDK, Maven, Node.js, pnpm, Git), clone the repo, download and configure WSO2 Identity Server 7.3.0, and get the app running locally.

Challenges faced:

- Had a Node.js version conflict with a previously installed version — resolved by reinstalling the correct version
- pnpm install was failing with ERR_PNPM_FETCH_404 errors for @wso2is packages due to a broken lockfile — resolved by pulling from upstream again after the wso2 team pushed a fix

Working branch: https://github.com/Dhruvirana08/identity-apps/tree/fix-issue-27869

### Steps to Reproduce

1. Clone the repository and run pnpm install && pnpm build from the project root.

2. Run: grep -rn "<img" --include="*.tsx" ./features | grep -v "alt=" | grep -v "node_modules"
3. **Expected:** No result for the search
4. **Actual:** 25 results are shows multiple <img> tags missing alt attributes appear across the affected files.
* The GitHub issue mentions only 14 violations out of 25, which is what I will focus on.
  
OR

2. Navigate to any of the affected files listed in the issue, for example: ./features/admin.application-templates.v1/components/application-template-card.tsx
3. Go to Line 176. 
4. **Expected:** <img> tag has an alt attribute.
5. **Actual:** <img> tag is missing the alt attribute, violating the react-doctor/alt-text accessibility rule

### Reproduction Evidence

- **Screenshots/logs:** <img width="1780" height="802" alt="image of grep result" src="https://github.com/user-attachments/assets/6e353a8f-171b-4777-8509-fdc1e7892c9b" />

- **My findings:** Confirmed all 14 violations across the 11 files listed in the GitHub issue and verified with the grep result file lines that they had a missing alt attribute for the `<img>` tags. The affected files are in the features folder and for template files or social login buttons like Apple, Facebook, etc. 

---

## Solution Approach

### Analysis

The root cause is that <img> tags were added to these components without alt attributes, violating WCAG 2.1 AA accessibility standards. It states to provide "Text Alternatives: Provide text alternatives for non-text content, such as images and multimedia". The react-doctor/alt-text ESLint rule enforces this requirement, but these instances were missed.

### Proposed Solution

Add appropriate alt attributes to each of the 14 affected <img> tags. For social login icons (Google, Apple, GitHub, Facebook, Microsoft) and other decorative images, use alt="". For images that convey meaningful information, add a descriptive alt="...".

### Implementation Plan

Using the UMPIRE framework (adapted):

**Understand:** 14 <img> tags across 11 files are missing alt attributes, causing accessibility errors that prevent screen reader users from understanding the UI.

**Match:** Other <img> tags in the codebase that correctly use alt="" for icons serve as the pattern to follow. For example, checking nearby components that handle images correctly.

**Plan:** 
1. Open each of the 11 affected files listed in the issue
2. Navigate to the specified line number
3. Determine if the image is decorative (icon/logo) → add alt=""
4. Determine if the image conveys meaning → add descriptive alt="description"
5. Run the grep command again to confirm zero remaining violations

**Implement:** https://github.com/Dhruvirana08/identity-apps/tree/fix-issue-27869

**Review:** Self-review for the following:
- Follow CONTRIBUTING.md conventions
- No unrelated files modified
- Commit message follows project conventions

**Evaluate:** Running the grep command after fixes should return 12 results instead of 25. All 14 violations resolved should reduce the error shown. Also, manually check all the listed files for <img> tags with an alt attribute.

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
