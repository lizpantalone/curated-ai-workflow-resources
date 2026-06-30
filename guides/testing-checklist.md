# The Three-Level Testing Checklist

Most test files only cover the happy path. That's how bugs ship: the code works
when everything goes right, and falls over the first time reality doesn't
cooperate. A complete test file covers **three levels**. After you write the
happy-path tests, stop and explicitly enumerate what could go wrong — then add
tests for the ones that matter.

This applies to **models, services, controllers, jobs, and background workers
alike.**

---

## 1. Happy path

The normal, expected usage — the thing the code is *for*.

- [ ] The primary success case produces the expected result
- [ ] The main side effects happen (record created, email enqueued, event fired)
- [ ] The return value / response shape is what callers expect

## 2. Edge cases

Valid-but-unusual inputs. The code *should* handle these, and often silently
doesn't.

- [ ] **Empty collections** — `[]`, `{}`, no matching records
- [ ] **Nil / optional fields** — absent optional params, null associations
- [ ] **Boundary values** — min/max, zero, the first and last item, off-by-one limits
- [ ] **Negative / zero numbers** where positive is assumed
- [ ] **Unknown-but-handled inputs** — an enum value you fall back on, a default branch
- [ ] **Deleted / missing associations** — the parent was removed, the foreign record is gone
- [ ] **Fallback params / defaults** — behavior when the caller omits something
- [ ] **Duplicate or repeated input** — idempotency, re-submission

## 3. Corner cases

Error and failure paths. This is where robustness lives.

- [ ] **External API raises / times out** — the upstream call fails
- [ ] **DB write fails** — validation error, constraint violation, deadlock
- [ ] **Foreign-key / uniqueness violations**
- [ ] **Response missing expected fields** — upstream returns an unexpected shape
- [ ] **Malformed input** — wrong type, unparseable, oversized
- [ ] **Concurrent state** — two requests racing on the same record (TOCTOU)
- [ ] **Permission / auth failures** — the actor isn't allowed to do this
- [ ] **Partial failure** — step 2 of 3 fails; is step 1 rolled back or orphaned?

---

## The habit

> A test file with only happy-path coverage is incomplete.

The discipline isn't memorizing this list — it's the **pause**. After the happy
path, ask: *"What could go wrong here?"* Write down the answers. Test the ones
that would actually hurt in production. Skip the ones that can't happen, and say
why in a comment so the next person knows you considered it.

---

From [curated-ai-workflow-resources](https://github.com/lizpantalone/curated-ai-workflow-resources)
· by [Liz Pantalone](https://lizpantalone.com)
