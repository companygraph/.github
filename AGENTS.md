<!-- conventions · v1.19.0 -->
Shared conventions of the robertblust, guestgraph and companygraph organizations live in
`conventions/`, vendored from robertblust/conventions at the release `conventions.json`
names. Read them before writing or committing anything here.

- `conventions/WRITING.md` — how we write: one voice, three registers, English and German.
- `conventions/WORKING.md` — how we work with git and GitHub.
- `conventions/REPOSITORIES.md` — the family: what each repository is and what pins what.
- `conventions/WRITER.md`, `conventions/TRANSLATOR.md`, `conventions/GLOSSARY.md` — the two roles that
  make a text, and the terms they keep.

Everything below this block is this repository's own. `sh conventions/conventions-sync check`
says whether the copy matches the release, `sync` brings it to the release the pin names, and
`sh conventions/conventions-check` holds this repository's own Markdown to `WRITING.md`, and
`sh conventions/conventions-format` to its one form, which `fix` writes. Edit a shared file in
robertblust/conventions, never here.
<!-- end conventions -->

# companygraph/.github — working conventions

This repository holds the organization profile shown on github.com/companygraph:
`profile/README.md`. That is its entire contents.

## The one rule that matters

**A second repository links, never restates.**

The sibling organization's profile once said "Core in development" while two slices had
shipped, because it restated a roadmap that lives in another repository. Nothing detected it —
no CI in one repository can validate prose in another, and the profile is the page a
first-time visitor reads before anything else.

The lesson is about restating, not about owning. Two facts a first-time visitor needs before
they open any repository are owned here and linked from `meta-model`: what has shipped and what
comes next, and which repository holds what and what each takes from the others. Everything else
has an owner elsewhere and is linked, never repeated:

| Fact | Owner |
| --- | --- |
| What has shipped, what is next, what is deferred | **here**, `profile/README.md` — `meta-model`'s README links to it |
| Which repository holds what, and what pins what | **here**, `profile/README.md` — the diagram |
| What the model is, how to instantiate it, what a pack is | `meta-model`'s `README.md` |
| The types, their schemas, the rules a graph must obey | `meta-model`'s `core/` and `CONVENTIONS.md` |
| What was decided and what was rejected | `meta-model`'s `docs/superpowers/specs/` |
| The pitch | companygraph.io |
| The talk | `companygraph.github.io`, at `talks/` — served at companygraph.io/talks/ |

**What is owned here is owned here alone.** A roadmap or a repository map copied back into a
README is the same drift in the other direction, and just as invisible.

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
  it may not restate the terms, and it may never imply a hosted product, a license fee or a
  paid edition of the model. The meta-model and its tooling are open source forever, which
  is the claim that makes the rest credible.

## Editing

`profile/README.md` renders on the org page. There is no build and no preview — GitHub renders
it directly, so check github.com/companygraph after pushing.

Keep it short. It competes with the repository list directly beneath it.

**A roadmap item's number is cited from other repositories**, so a new item is appended and no
item is renumbered. `meta-model`'s README points at item 5 for the tooling, and its specs and
plans cite items 2 and 3; renumbering to put a subject in the place it belongs breaks every one
of those silently, because no check in this repository can see them. The order of the list is
therefore the order things were written, not the order they shipped.

## Checks

One job, required by the ruleset on `main`: `conventions`, called from robertblust/conventions
at the pinned tag and shown by GitHub as `conventions / conventions`. There is nothing else to
check: the profile has no build and no suite. Everything about how to write and how to work
with git is in `conventions/`; this file is only what is this repository's own.
