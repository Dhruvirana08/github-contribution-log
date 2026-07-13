# github-contribution-log
GitHub contribution log for CodePath Summer - AI 301

# Contribution [1]: [[React Doctor] alt-text: Missing alt attribute (14 occurrences)]

**Contribution Number:** [1]  
**Student:** [Dhruvi Rana]  
**Issue:** #27869 - [[GitHub issue link](https://github.com/wso2/product-is/issues/27869)]
**Status:** [Phase IV - In-Progress]

**Working branch:** [https://github.com/Dhruvirana08/identity-apps/tree/fix-issue-27869]

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

### Manual Testing

[What you tested manually and results]

- Ran `grep -rn "<img" --include="*.tsx" ./features | grep -v "alt=" | grep -v "node_modules"` before and after the fix to confirm affected instances were resolved. Most fixed files no longer appear in the output; 3 files still appear as false positives because their `alt` attribute is on a separate line from the `<img>` tag in multi-line JSX (grep only checks the line containing `<img` itself) — manually confirmed `alt` is correctly present in each of these 3 files by inspecting the source directly.
- Ran `pnpm build` and started both `apps/console` and `apps/myaccount` locally to confirm no build or runtime errors were introduced.
- Ran `npx eslint` scoped to only the changed files, which returned 0 errors (pre-existing unrelated warnings only).
- Did not perform a full manual screen reader or DevTools pass across every changed instance, given the scope of the change spans multiple files across unrelated flows in a large monorepo; the fix itself is a low-risk, static attribute change with no logic or rendering behavior altered.

---

## Implementation Notes

### Week [3-4] Progress

[What you built this week, challenges faced, decisions made]

**What I built:**
- Added missing `alt` attributes to `<img>` elements across all files listed in the affected files section of issue #27869
- Used `alt=""` for decorative icons that sit next to a visible text label (Typography component) already describing the image (e.g. social login icons in execution-factory), and a descriptive `alt` value for standalone images with no adjacent label (e.g. `alt={ \`${selected?.name} preview\` }` in feature-preview-modal.tsx)
- Verified changes via `grep -rn "<img"` before/after, `pnpm build`, running both apps locally, and `npx eslint` scoped to only the changed files (0 new errors)

**Challenges faced:**
- Deciding whether an image was decorative or meaningful wasn't always obvious — had to check each component's surrounding JSX to see if a visible text label already conveyed the same information
- Several of the changed components weren't directly reachable in the running app; they're rendered through factory/mapping components several layers removed from the UI, so tracing the actual variable/prop flow to find the right screen manually took longer than expected. Wasn't able to visually confirm every instance in DevTools as a result — relied on build/lint verification and source-level review instead for those cases
- The initial `grep` check for missing `alt` attributes gave false positives on files using multi-line JSX, since it only checks the line containing `<img` itself; had to manually re-verify those 3 files individually

### Code Changes

- **Files modified:** All files mentioned in the affected files section of this log
- **Commits this week:**
- 94eea0c: fix: add missing alt attribute to files in admin.flow-builder-core.v1
- 2cbd799: fix: add missing alt attribute to application-template-card.tsx in admin.application-templates.v1
- 2949689: fix: add missing alt attribute to feature-preview-modal.tsx in admin.core.v1
- 640a8e8: fix: add missing alt attribute to button-adapter.tsx in admin.flow-builder-core.v1
- 5cce89e: fix: add missing alt attribute to sign-in-box-node.tsx in admin.login-flow-builder.v1
- ba8f246: fix: add missing alt attribute to push-provider-card.tsx in admin.push-providers.v1

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted: https://github.com/wso2/identity-apps/pull/10509]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

- There were 14 <img> elements across the features/ directory missing the alt attribute, which impacts screen reader users and is required for WCAG 2.1 AA compliance (per this repo's accessibility guidelines on supporting screen readers with semantic HTML). This PR adds alt attributes across the affected files:

-> alt="" for decorative icons that sit alongside a visible text label already describing the image (e.g. social login icons paired with their provider name) — this explicitly signals to assistive technology to skip the image, rather than leaving it to fall back to inconsistent or unhelpful behavior across different screen readers when alt is omitted entirely.
-> A descriptive alt value for standalone images that convey information on their own, with no adjacent text label (e.g. template/feature preview images), using the relevant item name where available.

**Maintainer Feedback:**
- [7/11/2026]: [The reviewer commented that alt attributes need to have some value assigned to it, instead of them being none.]
- [7/12/2026]: [I plan to add the alt values to the attributes based on the file and context available. I might ask a clarification question about if this should be done for all attributes or if I should follow some guidelines for implementing.]

**Status:** [**Review Provided, waiting for modification from me**]
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
