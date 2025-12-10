# Shared Code Review Criteria

This file contains the standard review criteria, severity levels, and output format used by all code review agents.

## Review Criteria (Priority Order)

1. **Correctness**: Logic errors, unhandled edge cases, race conditions, incorrect API usage, data validation flaws
2. **Security**: Injection attacks, insecure data storage, insufficient access controls, secrets exposure, authentication/authorization flaws
3. **Efficiency**: Performance bottlenecks, unnecessary computations, memory leaks, inefficient algorithms or data structures
4. **Maintainability**: Code readability, modularity, adherence to language idioms and style guides
5. **Testing**: Test coverage, quality, edge case handling, integration and end-to-end test adequacy
6. **Error Handling**: Proper error handling, logging practices, observability mechanisms

## Severity Levels

Assign exactly one severity level to every finding:

| Level | Icon | Description | Action |
|-------|------|-------------|--------|
| Critical | 🔴 | Production failure, security breach, data corruption | Must fix before merge |
| High | 🟠 | Significant bugs or performance degradation | Should fix before merge |
| Medium | 🟡 | Best practice deviations, technical debt | Consider fixing |
| Low | 🟢 | Minor/stylistic (typos, formatting) | Author discretion |

### Severity Guidelines

- Typos, comments, docstrings: 🟢
- Hardcoded values to constants: 🟢
- Test file issues: 🟢 or 🟡
- Markdown file issues: 🟢 or 🟡
- Style guide violations: 🟡 or 🟢
- Performance bottlenecks: 🟠 or 🟡
- Logic errors causing incorrect behavior: 🔴 or 🟠
- Security vulnerabilities: 🔴 or 🟠

## Output Format

```markdown
## 📋 Code Review for PR #<NUMBER>

**PR Title**: <title>
**Author**: <author>
**Branch**: <head> → <base>

---

## 📊 Review Summary

[2-3 sentence high-level assessment of the PR's objective and overall quality]

---

## 🔍 Detailed Findings

### 🔴 Critical Issues (<count>)

#### <file_path>:<line_range>
**Issue**: <detailed explanation>

**Recommendation**:
```<language>
<suggested code fix>
```

---

### 🟠 High Priority Issues (<count>)

[Same format as above]

---

### 🟡 Medium Priority Issues (<count>)

[Same format as above]

---

### 🟢 Low Priority Issues (<count>)

[Same format as above]

---

## 💡 General Feedback

- [Positive highlights]
- [Recurring patterns]
- [Architectural suggestions]

---

## ✅ Next Steps

[Recommendations for how to proceed with the PR]
```

## Quality Rules

1. **Real Issues Only**: Only report verifiable bugs, vulnerabilities, or concrete improvements
2. **No Vague Comments**: Never ask authors to "check," "verify," or "confirm" without substance
3. **One Issue Per Finding**: Each comment should address a single, specific issue
4. **Actionable Suggestions**: Provide code fixes, not just descriptions of problems
5. **Accurate References**: File paths and line numbers must be correct based on the diff
6. **No Duplicates**: Comment once on first instance; summarize repeated issues in General Feedback
