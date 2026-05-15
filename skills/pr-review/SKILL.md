---
name: pr-review
description: Comprehensive pull request review - walks through commits, verifies test coverage, checks description accuracy, and identifies complex code patterns
---

# PR Review

Provides a comprehensive, commit-by-commit review of pull requests with a focus on code clarity, test coverage, and description accuracy.

## Workflow

When invoked with `/pr-review <url>`, follow this process:

### 1. Parse and Fetch PR Data

Start by extracting the PR URL. Accept formats like:
- `https://github.com/owner/repo/pull/123`
- `owner/repo#123`
- `owner/repo/pull/123`

Use GitHub CLI to fetch:
```bash
gh pr view <pr-number> --repo <owner>/<repo> --json title,body,author,commits,files
```

### 2. PR Overview

Display:
- **Title**: PR title
- **Description**: Full PR description as written
- **Author**: Who submitted it
- **Files changed**: Count of files, additions/deletions summary
- **Branch**: Target branch (usually main/master)

### 3. Analyze Each Commit

For each commit in the PR (in order):

#### a. Commit Overview
- Show the commit hash (short) and message
- Display what files changed in this commit

#### b. Code Explanation
- Read the diff for this commit
- Explain **in clear, plain terms** what the code is doing
- Focus on the "why" — what problem does this solve?
- Explain the logic flow without using jargon

#### c. Identify Complexity
Look for code patterns that are **clever but potentially obscure**:
- Clever one-liners that could be clearer
- Non-obvious algorithmic choices
- Conditional logic that's hard to follow at first glance
- Regex or complex data transformations
- Nested abstractions or indirection

Flag these with: *"This pattern is clever but could be clearer..."*

#### d. Test Coverage Check
- Look for test files that were added/modified in this commit
- Check if the tests cover the new/changed functionality
- Flag if logic changes lack corresponding test updates
- Look for edge cases that aren't tested
- Flag if test coverage seems insufficient for the scope of change

### 4. Validate PR Description

After reviewing all commits:
- Does the PR description accurately summarize what was implemented?
- Does it mention all significant changes?
- Is the description more detailed than the commit messages warrant?
- Are there implementation details that contradict the description?

### 5. Check for Deliverables

If the PR involves any of these, verify:
- **Documents** (README, guides, specs) → confirm they're linked/referenced in description
- **Images** (diagrams, screenshots, mockups) → confirm they're linked in description
- **Generated outputs** (reports, builds, artifacts) → confirm examples/links in description
- **API changes** → confirm documentation is updated and linked
- **Database changes** → confirm migration docs are linked

Specifically look for: "See [link]", "generated at [link]", "example: [link]"

### 6. Summary & Recommendations

Provide a final assessment:
- **Overall quality**: Is this well-implemented?
- **Description accuracy**: Does it match the code?
- **Test coverage**: Is it adequate?
- **Code clarity**: Are there concerning patterns?
- **Completeness**: Are deliverables documented?

### 7. Specific Checks

Always verify:
- ✓ No commented-out code without explanation
- ✓ No debug logging or console.log statements left in
- ✓ No TODO comments without context or issue number
- ✓ Variable names are clear and descriptive
- ✓ Functions have reasonable complexity (not doing too many things)
- ✓ Error handling is appropriate
- ✓ No secrets or credentials in the code

## Usage

```
/pr-review <github-url>
```

### Examples

```
/pr-review https://github.com/owner/repo/pull/123
/pr-review owner/repo#456
```

## Requirements

- GitHub CLI (`gh`) installed and authenticated
- Access to the repository (public repos don't require auth)

## Output Format

Structure your review as:

```
# PR Review: [Title]

## Overview
[PR details]

## Commit-by-Commit Analysis

### Commit 1: [message]
**What it does:** [explanation]
**Complexity notes:** [any clever patterns]
**Test coverage:** [status]

### Commit 2: [message]
...

## Validation
- **Description accuracy:** ✓/✗ [notes]
- **Test coverage:** ✓/✗ [notes]
- **Code clarity:** ✓/✗ [notes]
- **Deliverables:** ✓/✗ [notes]

## Recommendations
[Any issues or suggestions]
```
