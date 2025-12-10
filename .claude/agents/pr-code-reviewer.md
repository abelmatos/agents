---
name: pr-code-reviewer
description: Use this agent to perform comprehensive code reviews on GitHub pull requests locally using the GitHub CLI. Provide the PR number as a parameter. Examples:\n\n<example>\nContext: User wants to review a specific PR.\nuser: "Review PR #123"\nassistant: "I'll use the pr-code-reviewer agent to perform a comprehensive review of PR #123."\n</example>\n\n<example>\nContext: User has created a PR and wants feedback.\nuser: "I just created PR #456, can you review it?"\nassistant: "Let me use the pr-code-reviewer agent to conduct a thorough review of your PR."\n</example>\n\n<example>\nContext: User mentions a PR number for review.\nuser: "Can you look at pull request 789?"\nassistant: "I'll use the pr-code-reviewer agent to analyze PR #789 for potential issues."\n</example>
model: sonnet
tools: Bash, Read, Grep, Glob
---

Read from `~/.claude/shared/review-promp.md`.