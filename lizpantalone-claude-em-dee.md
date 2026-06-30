<!--
  CLAUDE.md — starter template
  Author: Liz Pantalone
  Source: https://lizpantalone.com
  Free to use and adapt. Rename this file to CLAUDE.md and place it in your
  project root, or at ~/.claude/CLAUDE.md to apply it globally.
-->

# Testing expectations

When writing or updating tests, always cover all three levels:

1. **Happy path** — the normal, expected usage.
2. **Edge cases** — valid-but-unusual inputs: empty collections, nil optional fields, boundary values (min/max), unknown-but-handled inputs, deleted associations, fallback params, zero/negative values, etc.
3. **Corner cases** — error and failure paths: API raises, DB write fails, response missing expected fields, foreign-key violations, concurrent state, malformed input, upstream service returns unexpected shape, etc.

A test file with only happy-path coverage is incomplete. After writing the happy-path tests, pause and explicitly enumerate what could go wrong, then add tests for the ones that matter.

This applies to models, services, controllers, jobs, and background workers alike.

# Commit messages

Use [Conventional Commits](https://www.conventionalcommits.org/) formatting:

- Structure the subject line as `type(scope): description`, where `type` is one of `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, or `revert`, and `scope` is optional.
- The first line (the subject) must be **50 characters or fewer**.
- Wrap all subsequent lines (the body and footer) at **75 characters or fewer**.
- Separate the subject from the body with a blank line.
- Use the imperative mood in the description (e.g. "add", not "added" or "adds").
- Mark breaking changes with a `!` after the type/scope (e.g. `feat!:`) or a `BREAKING CHANGE:` footer.

## Commit granularity

Commit early and often, keeping each commit small — but every commit should be substantive.

- A commit should represent one meaningful, self-contained unit of change.
- Don't create commits for inconsequential changes (typo fixes, whitespace, minor wording tweaks) on their own — fold them into an adjacent, more substantive commit so they don't clutter the repository history.

## Ticket/issue references

Every commit must reference a ticket/issue number (e.g. in the footer as `Refs: PROJ-123` or `Closes #123`, or inline in the subject where the project convention calls for it).

- If a ticket/issue already exists for the work, tag its number.
- If no ticket/issue exists, **create one** in the project's tracking system before committing, then tag the new number.
  - Determine the appropriate tracking system from the project (e.g. GitHub Issues via `gh`, Jira, Linear, etc.). If it's ambiguous, ask which tracker to use.
  - In the ticket/issue description, explain **what** code is being changed and **why** — this is intended to serve as historical context reference for the future, so be specific about the motivation, not just the mechanics.

# Documentation

Keep documentation current with the code:

- Update the README, or other documentation elsewhere in the repo/codebase filetree, whenever a change makes it appropriate (new features, changed behavior, new setup/config steps, altered commands, etc.).
- Before submitting a PR for review, check the README for accuracy within the scope of the current PR — verify that anything the PR touches is still described correctly, and update it where it is now stale.
