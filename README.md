# Curated AI Workflow Resources

A small, curated collection of resources for working effectively with AI coding
tools — the same conventions and templates I use in real projects to get faster,
more consistent results without piling up tech debt.

Maintained by [Liz Pantalone](https://lizpantalone.com).

## Resources

### `lizpantalone-claude-em-dee.md` — CLAUDE.md starter template

An opinionated [`CLAUDE.md`](https://docs.claude.com/en/docs/claude-code/memory)
that gives Claude Code (and similar AI coding assistants) clear standards to
follow on every task:

- **Testing expectations** — happy path, edge cases, and corner cases on every test file
- **Conventional Commits** — 50-char subject, 75-char body, with type/scope structure
- **Ticket/issue references** — every commit tied to a tracked issue, created if one doesn't exist
- **Commit granularity** — small, substantive commits with trivial changes folded in
- **Documentation** — keep the README accurate and current with each change

**How to use it:**

1. Download [`lizpantalone-claude-em-dee.md`](./lizpantalone-claude-em-dee.md).
2. Rename it to `CLAUDE.md`.
3. Place it in your **project root** (applies to that repo), or at
   **`~/.claude/CLAUDE.md`** (applies globally to all your projects).
4. Tweak it to fit your team — it's a starting point, not gospel.

You can also download it directly from
[lizpantalone.com/resources](https://lizpantalone.com/resources).

## License

[MIT](./LICENSE) — free to use, adapt, and share. Attribution appreciated but
not required.
