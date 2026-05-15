---
name: pr-review
description: Comprehensive pull request review - walks through commits, verifies test coverage, checks description accuracy, and identifies complex code patterns
---

# PR Review

Provides a comprehensive, commit-by-commit review of pull requests.

## What it does

1. **Fetches PR details** — title, description, all commits
2. **Analyzes each commit** — explains what the code changes do
3. **Identifies complexity** — flags clever code that may obscure intent
4. **Verifies test coverage** — ensures changes have adequate unit tests
5. **Validates description** — confirms PR description matches implementation
6. **Checks for deliverables** — if PR produces docs/images, verifies links in description

## Usage

```
/pr-review <github-url>
```

Or provide a PR URL and the skill will extract org, repo, and PR number.

### Examples

```
/pr-review https://github.com/owner/repo/pull/123
/pr-review owner/repo#123
```

## Requirements

- GitHub CLI (`gh`) installed and authenticated
- Valid pull request URL or owner/repo#number format

## Output

Structured review covering:
- **PR Overview** — title, description, author
- **Commit-by-commit breakdown**:
  - What changed and why
  - Code patterns and complexity notes
  - Test coverage analysis
- **Summary** — description accuracy, overall assessment, recommendations

## Technical Details

The skill uses the GitHub CLI to:
- Fetch PR metadata and description
- List all commits in the PR
- Show the diff for each commit
- Help identify test files and coverage gaps
