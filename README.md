# AI Configurations

This repository contains AI configuration files for Claude Code, including custom agents, slash commands, and shared resources for PR workflows.

## Contents

```
.claude/
├── agents/           # Custom agent configurations
├── commands/         # Custom slash commands
└── shared/           # Shared prompts and criteria
.agents/              # Output directory for generated content
```

## Prerequisites

- [GitHub CLI](https://cli.github.com/) (`gh`) - Required for PR review and description agents
- [Gemini CLI](https://github.com/google-gemini/gemini-cli) - Required for Gemini-based agents

## Agents

### pr-code-reviewer
Performs comprehensive code reviews on GitHub pull requests using the GitHub CLI.

```
Review PR #123
```

### pr-description-generator
Analyzes the current git branch and creates a PR description following your repository's template (`.github/pull_request_template.md`).

```
Generate a PR description for my current branch
```

Output saved to: `.agents/{branch-name}/pr_description_{branch-name}.md`

### gemini-cli-pipe
Delegates tasks to Gemini CLI for code analysis, documentation generation, or brainstorming.

```
Ask Gemini to review this function for bugs
```

### gemini-review-pr
Performs PR code reviews using Gemini CLI with shared review criteria.

```
Have Gemini review PR #456
```

## Slash Commands

### `/pr`
Launches the PR description generator for your current branch.

### `/review-pr <number>`
Runs both Claude and Gemini PR reviews **in parallel**, saving outputs to:
- `.agents/review/{pr-number}/review.md` (Claude)
- `.agents/review/{pr-number}/review-gemini.md` (Gemini)

### `/git-branch-commit-pr <task>`
Complete git workflow automation:
1. Fetches remotes and creates a branch from `origin/main`
2. Uses branch naming convention: `<type>/LM-XXXX-<description>`
3. Executes the requested task
4. Commits with conventional commit format
5. Pushes and creates a draft PR

## Shared Resources

| File | Description |
|------|-------------|
| `review-criteria.md` | Standard review criteria, severity levels (🔴🟠🟡🟢), and output format |
| `review-prompt.md` | Base prompt for PR review agents with execution workflow |

## Usage

Copy the `.claude/` directory to your home directory or project root:

```bash
cp -r .claude ~/
```

Or symlink for easier updates:

```bash
ln -s /path/to/this/repo/.claude ~/.claude
```
