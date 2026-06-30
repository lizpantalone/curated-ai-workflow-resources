# Curated AI Workflow Resources

A small, curated collection of resources for working effectively with AI coding
tools — the same conventions and templates I use in real projects to get faster,
more consistent results without piling up tech debt.

Maintained by [Liz Pantalone](https://lizpantalone.com).

## Resources

### 📄 CLAUDE.md starter template — [`lizpantalone-claude-em-dee.md`](./lizpantalone-claude-em-dee.md)

An opinionated [`CLAUDE.md`](https://docs.claude.com/en/docs/claude-code/memory)
that gives Claude Code (and similar AI coding assistants) clear standards to
follow on every task: testing expectations (happy / edge / corner cases),
Conventional Commits, ticket references, commit granularity, and documentation
upkeep. Download it, rename to `CLAUDE.md`, and drop it in your project root or
at `~/.claude/CLAUDE.md` for all projects. Also downloadable at
[lizpantalone.com/resources](https://lizpantalone.com/resources).

### 📘 Guides — [`guides/`](./guides)

| Guide | What it is |
|-------|-----------|
| [AI-First Development Without the Tech Debt](./guides/ai-first-development.md) | An opinionated field guide on using AI coding tools at speed without accumulating debt. |
| [The Three-Level Testing Checklist](./guides/testing-checklist.md) | Happy / edge / corner-case coverage as a usable checklist — for humans and AI alike. |

### 🤖 Agents — [`agents/`](./agents)

Custom [Claude Code subagents](https://docs.claude.com/en/docs/claude-code/sub-agents)
for focused review passes. See the [agents README](./agents/README.md) to install.

| Agent | What it does |
|-------|-----------|
| [`principal-pr-reviewer`](./agents/principal-pr-reviewer.md) | Principal-level PR review with inline comments and a verdict. |
| [`branch-security-auditor`](./agents/branch-security-auditor.md) | AppSec review of a branch's diff vs. its base. |
| [`repo-pentest-auditor`](./agents/repo-pentest-auditor.md) | Full-repository penetration test with an OWASP/CWE report. |

### 🧰 Templates — [`templates/`](./templates)

| Template | What it is |
|----------|-----------|
| [`commit-template.gitmessage`](./templates/commit-template.gitmessage) | A Conventional Commits git message template. Install with `git config --global commit.template`. |

## Work with Liz

Want to hire Liz to help your team adopt AI the right way — shipping faster
without piling up tech debt? That's exactly what I do, from bespoke builds to
team coaching and training. **[Get in touch at lizpantalone.com](https://lizpantalone.com).**

## License

[MIT](./LICENSE) — free to use, adapt, and share. Attribution appreciated but
not required.
