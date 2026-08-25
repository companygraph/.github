# CompanyGraph

**The open-source meta-model for operating a company.** → [**companygraph.io**](https://companygraph.io)

A company's knowledge is scattered across wikis, decks, tickets and chat threads — each with its own structure, its own half-truth, and nothing that can check any of it. CompanyGraph is the structure that knowledge takes instead: one Markdown file per entity, in folders named for their type, with schemas saying what each type carries. People can read it, and agents can rely on it.

It is not invented. It is the generalisation of a model that already works in two places that never knew about each other — a multi-person company, and a company of one. Both arrived at the same shape.

## 🧭 Where to start

| Repository | What it is |
|---|---|
| [**meta-model**](https://github.com/companygraph/meta-model) | The vocabulary: core types, one schema per type, the conventions that make a graph of Markdown files checkable, and a worked example |
| [**companygraph.github.io**](https://github.com/companygraph/companygraph.github.io) | The site at [companygraph.io](https://companygraph.io) — landing page, the [talk](https://companygraph.io/talks/intro/), billing and privacy |

**New here?** The [ten-minute introduction](https://companygraph.io/talks/intro/) is the
fastest way in: why a company's knowledge lives everywhere and nowhere, what two companies
that never met both arrived at, and what is written today. DE · EN.

## 🧱 Principles

- **One Markdown file per entity** — frontmatter for the fields, a Markdown body for the prose. A document holding many entities as headings has no name to reference any of them by
- **An entity is a file when it owns nothing, and a folder when it owns collections of its own** — one mechanism, not two
- **The canonical name of an entity is its H1** — not a `name` field, not the filename, and no fallback chain between them
- **Every reference is by canonical name, never by path** — moving a file breaks nothing, and renaming an entity breaks loudly rather than quietly
- **Schemas are Markdown, enforced by agents** — not a stage on the way to JSON Schema
- **Apache 2.0** — the meta-model is open source and stays that way

Core defines a type without obliging you to populate it: a company of one has no `group`, and the type stays in core, unused. A **pack** is for vocabulary a kind of company would not have at all — [what a pack is →](https://github.com/companygraph/meta-model#packs)

## 🗺️ Where we are

Whatever the model says today. What has shipped, what is next, and what was deliberately deferred all live with the code, in the same commit as the thing they describe:
[**roadmap →**](https://github.com/companygraph/meta-model#roadmap)

[companygraph.io](https://companygraph.io) is the home page. The meta-model and its tooling are open source and stay that way; consulting is the one thing that costs money — [how it is billed →](https://companygraph.io/billing/)

---

*Built spec-first in the open. Early days — star [meta-model](https://github.com/companygraph/meta-model) to follow along.*
