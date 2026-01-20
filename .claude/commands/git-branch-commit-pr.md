# Git Branch, Commit & PR Workflow

## Arguments

$ARGUMENTS

## Pre-flight

1. Verify no uncommitted changes that would conflict
2. Fetch all remotes: `git fetch --all`
3. Create branch from latest main: `git checkout -b <branch> origin/main`

## Branch Naming

Use format: `<type>/LM-XXXX-<short-description>`

- Types: `feature/`, `fix/`, `chore/`, `ops/`
- Extract Jira reference from arguments (e.g., LM-1234)
- Example: `feature/LM-1234-keycloak-update-prod`

## Execute Task

Complete the work described in the arguments.

## Commit

1. Group related changes into logical commits
2. Use conventional commit format:
   - `ops(env):` for deployment changes (env = dev/test/prod)
   - `feat:` for new features
   - `fix:` for bug fixes
   - `chore:` for maintenance
3. Include Jira reference in commit message (e.g., `LM-XXXX`)

## Push & PR

1. Push branch: `git push -u origin <branch>`
2. Find PR template in repo: `.github/pull_request_template.md`
3. Create draft PR using `gh pr create --draft` with:
   - Title matching main commit message
   - Body following the repo's PR template structure
   - Jira link: `https://likemagic.atlassian.net/browse/LM-XXXX`