# AI-First Development Without the Tech Debt

AI coding tools can move your software forward at incredible speed — or quietly
bury your team in debt it spends the next year digging out of. Same tool, two
outcomes. The difference isn't the model; it's the practices around it.

This is the short version of how I work with AI tools on real production code,
and how I coach teams to do the same. It's opinionated on purpose.

---

## The core principle

**You are still the engineer. The AI is a very fast junior.**

A fast junior who has read everything and remembers nothing about your codebase,
your conventions, or yesterday's decision. It will produce plausible code at a
rate you can't review by skimming. Every practice below exists to keep *you* in
control of what actually lands.

The failure mode isn't "AI writes bad code." It's "AI writes *plausible* code
faster than anyone reviews it, and it accumulates." Debt by velocity.

---

## The practices

### 1. Give the AI your standards up front

Don't re-explain your conventions in every prompt. Put them in a `CLAUDE.md` (or
your tool's equivalent) at the repo root, or globally at `~/.claude/CLAUDE.md`.
Testing expectations, commit format, "always do X," "never do Y." The AI follows
them on every task instead of guessing.

→ Starter template:
[`lizpantalone-claude-em-dee.md`](../lizpantalone-claude-em-dee.md)

### 2. Keep changes small and reviewable

The smaller the change, the more completely you can actually review it. Ask for
one self-contained unit at a time. A 600-line AI diff you skim is debt; a 60-line
diff you understand is progress. Commit early and often — but every commit
substantive.

### 3. Review it like a junior's PR — because it is one

**Never merge code you haven't read and understood.** Read the diff. Ask "what
happens when this input is empty / this call fails / two of these run at once?"
If you can't answer, you're not done reviewing. The
[`principal-pr-reviewer`](../agents/principal-pr-reviewer.md) agent in this repo
automates a first pass, but the judgment stays yours.

### 4. Test all three levels

AI is great at the happy path and lazy about everything else. Make it cover
edge cases (empty, nil, boundaries) and corner cases (the API raises, the write
fails, the input is malformed). A test suite that only proves the code works when
everything goes right is how AI-written code rots.

→ [The Three-Level Testing Checklist](./testing-checklist.md)

### 5. Tie every change to its "why"

AI-generated code has no memory of *why* it exists. Six months later, neither
will you. Reference a ticket/issue on every commit, and write down what changed
and why — that's the context that lets the next person (or the next AI session)
make a safe change instead of a guess.

### 6. Keep the docs honest

When behavior changes, update the README and docs in the same change. Stale docs
are a tax every future task pays — and AI tools read your docs to orient
themselves, so stale docs actively mislead the next session.

### 7. Verify behavior, don't trust output

"It compiles" and "the tests it wrote pass" are not "it works." Run the thing.
Click the button. Hit the endpoint. AI confidently produces code that looks right
and is subtly wrong; only observing real behavior catches it.

### 8. Know when to slow down

Speed is the default; deliberation is the exception you choose on purpose.
Slow down — review harder, test more, get a second pair of eyes — whenever the
change touches **auth, money, personal data, deletion, or anything irreversible.**
That's where AI's plausible-but-wrong output does the most damage.

---

## The tech-debt smell test

Before you call an AI-assisted change "done," check:

- [ ] I **read and understood** every line that's landing
- [ ] The change is **small enough** that the above is actually true
- [ ] Tests cover **edge and corner cases**, not just the happy path
- [ ] I **ran it** and observed the real behavior
- [ ] The commit references its **ticket/issue** and explains *why*
- [ ] **Docs/README** reflect the new reality
- [ ] Nothing security-, money-, or data-sensitive slipped through on autopilot

If you can't tick these, you don't have working software yet — you have a
plausible draft.

---

## Want help putting this into practice?

This is exactly what I do — from building bespoke AI-first software to coaching
teams on adopting these practices without piling up debt.

**[Get in touch at lizpantalone.com →](https://lizpantalone.com)**

---

From [curated-ai-workflow-resources](https://github.com/lizpantalone/curated-ai-workflow-resources)
· by [Liz Pantalone](https://lizpantalone.com)
