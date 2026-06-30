# Claude Code Subagents

Custom [subagents](https://docs.claude.com/en/docs/claude-code/sub-agents) for
[Claude Code](https://claude.com/claude-code) — specialized reviewers you can
invoke for focused, high-quality passes over your code.

| Agent | What it does |
|-------|--------------|
| [`principal-pr-reviewer`](./principal-pr-reviewer.md) | Principal-engineer-level PR review with inline comments and a final verdict (Approve / Request Changes / Comment). |
| [`branch-security-auditor`](./branch-security-auditor.md) | AppSec review of the changes on a branch vs. its base (the diff) — injection, authz, secrets, config, and more. |
| [`repo-pentest-auditor`](./repo-pentest-auditor.md) | Comprehensive, adversarial penetration test across the **entire** repository, with an OWASP/CWE-mapped report. |

## Install

Copy the agent file into your agents directory:

- **Globally (all projects):** `~/.claude/agents/`
- **Per project:** `<your-repo>/.claude/agents/`

```bash
# example: install the PR reviewer globally
curl -o ~/.claude/agents/principal-pr-reviewer.md \
  https://raw.githubusercontent.com/lizpantalone/curated-ai-workflow-resources/main/agents/principal-pr-reviewer.md
```

Then invoke it from Claude Code, e.g. *"review this PR with the principal-pr-reviewer agent."*

## Notes

- The `model` field in each agent's frontmatter is a sensible default — change it
  to whatever tier you prefer.
- The two security agents include an **optional** "Codebase Intelligence" step:
  if your repo is wired to a codebase-intelligence / knowledge MCP tool, they'll
  use it to cut false positives; if not, they fall back to reading the code
  directly. No external service is required.
- These are review/advisory agents — they report findings and leave the fixes to
  you.
