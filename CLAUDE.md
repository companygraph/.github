# companygraph/.github — working conventions

This repository holds the organisation profile shown on github.com/companygraph:
`profile/README.md`. That is its entire contents.

## The one rule that matters

**A second repository links, never restates.**

The sibling organisation's profile once said "Core in development" while two slices had
shipped, because it restated a roadmap that lives in another repository. Nothing detected it —
no CI in one repository can validate prose in another, and the profile is the page a
first-time visitor reads before anything else.

So the profile carries positioning and links, and nothing that has an owner elsewhere:

| Fact | Owner — link to it |
|---|---|
| What the model is, how to instantiate it, what a pack is | `meta-model`'s `README.md` |
| Roadmap, status, what is deferred | `meta-model`'s `README.md#roadmap` |
| The types, their schemas, the rules a graph must obey | `meta-model`'s `core/` and `CONVENTIONS.md` |
| What was decided and what was rejected | `meta-model`'s `docs/superpowers/specs/` |
| The pitch | companygraph.io |
| The talk | `companygraph.github.io`, at `talks/` — served at companygraph.io/talks/ |

Before adding a sentence here, ask what would have to change if the answer changed. If the
answer is "a file in another repository", link to it instead.

**The design principles are the exception, and only because they are the stable half.** They
restate `meta-model`'s `## Design principles` deliberately: a visitor who reads this page and
leaves should know what the model claims. They change when the model's shape changes, which is
rare and loud — unlike a roadmap, which changes every release. If they ever do change, both
copies move in the same session or the exception is not worth keeping.

## What this page must not say

- **No type count and no type list.** The model ships a slice today and moves fast; any
  number here is wrong within a release. That sentence belongs in `meta-model`'s `README`,
  which ships in the same commit as the type it counts.
- **No claim that a pack exists.** The mechanism is deliberately undesigned until a second
  kind of company asks for one. Saying what a pack *is* is positioning and belongs here;
  implying one ships is not.
- **Nothing identifying the companies the model was extracted from.** The structural claim —
  two independent instances converged on the same shape — stands without naming either.
- **No rate, and no hosted service.** The commercial model is consulting, billed time and
  material, and it is stated once — on `companygraph.io/billing`. This page may link there;
  it may not restate the terms, and it may never imply a hosted product, a licence fee or a
  paid edition of the model. The meta-model and its tooling are open source forever, which
  is the claim that makes the rest credible.

## Editing

`profile/README.md` renders on the org page. There is no build and no preview — GitHub renders
it directly, so check github.com/companygraph after pushing.

Keep it short. It competes with the repository list directly beneath it.

## Process

- Commits happen when the user asks; suggest a message, don't auto-commit.
