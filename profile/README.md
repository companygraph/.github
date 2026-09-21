# CompanyGraph

**The open-source meta-model for operating a company.** → [**companygraph.io**](https://companygraph.io)

A company's knowledge is scattered across wikis, decks, tickets and chat threads — each with its own structure, its own half-truth, and nothing that can check any of it. CompanyGraph is the structure that knowledge takes instead: one Markdown file per entity, in folders named for their type, with schemas saying what each type carries. People can read it, and agents can rely on it.

It is not invented. It is the generalization of a model that already works in two places that never knew about each other — a multi-person company, and a company of one. Both arrived at the same shape.

## 🧭 Where to start

| Repository | What it is |
| --- | --- |
| [**meta-model**](https://github.com/companygraph/meta-model) | The vocabulary: core types, one schema per type, the conventions that make a graph of Markdown files checkable, and a worked example |
| [**mcp-server**](https://github.com/companygraph/mcp-server) | A read-only MCP server over any instance: an agent asks which types a company declares, what one entity says and what evidence a claim rests on, and every answer is what the model says at one commit |
| [**companygraph.github.io**](https://github.com/companygraph/companygraph.github.io) | The site at [companygraph.io](https://companygraph.io) — landing page, the [talk](https://companygraph.io/talks/intro/), billing and privacy |

**New here?** The [twelve-minute introduction](https://companygraph.io/talks/intro/) is the fastest way in: why a company's knowledge lives everywhere and nowhere, what two companies that never met both arrived at, and what is written today. DE · EN.

## 🧩 How it fits together

One repository defines the vocabulary; everything else takes it. An instance is a folder of Markdown that vendors `core/` at a release and records which one, so a graph written last year still says what it meant. A site pins the repository it renders by commit, so a page and the model it was built from move together on purpose.

```mermaid
flowchart TB
    subgraph cg["companygraph"]
        MM["<b>meta-model</b><br/>the vocabulary: core types,<br/>one schema each, the conventions"]
        SITE["<b>companygraph.io</b><br/>landing, model pages, the talk"]
        MCP["<b>mcp-server</b><br/>read-only MCP<br/>over any instance"]
        TOOL["<b>tooling</b><br/>npx companygraph<br/><i>designed, not built</i>"]
    end

    subgraph rb["robertblust"]
        MENTAL["<b>mental-model</b><br/>the reference instance:<br/>one company, described"]
        BLUST["<b>blust.ch</b><br/>profile and model pages"]
        MCPD["<b>mcp.blust.ch</b><br/>the server, deployed<br/>on the reference instance"]
    end

    MM -- "core vendored at a release" --> MENTAL
    MM -- "pinned by commit · builds the model pages" --> SITE
    MENTAL -- "pinned by commit · builds the model pages" --> BLUST
    MM -- "the instance parser, by tag" --> BLUST
    MM -- "the instance parser, by tag" --> MCP
    MCP -- "pinned by tag" --> MCPD
    MENTAL -- "pinned by commit · parsed into a snapshot" --> MCPD
    TOOL -. "will scaffold and check an instance" .-> MENTAL
```

The meta-model is the only thing anything else depends on, and it depends on nothing. That is what lets an instance live in a repository of its own, under its own license, on a machine that never runs any of this.

## 🧱 Principles

- **One Markdown file per entity** — frontmatter for the fields, a Markdown body for the prose. A document holding many entities as headings has no name to reference any of them by
- **An entity is a file when it owns nothing, and a folder when it owns collections of its own** — one mechanism, not two
- **The canonical name of an entity is its H1** — not a `name` field, not the filename, and no fallback chain between them
- **Every reference is by canonical name, never by path** — moving a file breaks nothing, and renaming an entity breaks loudly rather than quietly
- **Schemas are Markdown, read by agents and by the checker alike** — not a stage on the way to JSON Schema, and no second format kept for the checker
- **Apache 2.0** — the meta-model is open source and stays that way

Core defines a type without obliging you to populate it: a company that does not group what its people have achieved writes no `achievement-kind`, and the type stays in core either way. A **pack** is for vocabulary a kind of company would not have at all — [what a pack is →](https://github.com/companygraph/meta-model#packs)

## 🗺️ Where we are

1. ✅ **The person cluster** — `profile`, `experience`, `skill`, `proficiency-level` and
   `value`, the conventions that make them checkable, and a worked example. One person
   described completely, rather than every type partially.
2. ✅ **The reference instance** — a real company described in this vocabulary:
   [`robertblust/mental-model`](https://github.com/robertblust/mental-model), a company of
   one, laid out by hand as the tooling will lay one out. What it taught is §7 of
   [its spec](https://github.com/companygraph/meta-model/blob/main/docs/superpowers/specs/2026-08-26-reference-instance-design.md).
3. **The rest of core** — `identity` and `vision` shipped in 0.4.1, which is what let an
   instance name the company it describes and say where it is going, `experience-kind` in
   0.6.0, `surface` in 0.16.0, then direction's `strategic-objective` and `strategy` in
   0.21.0, organization's `role` in 0.23.0, operation's `process` and `phase` in 0.25.0 and
   `achievement-kind` in 0.28.0; still ahead are `kpi`, `brand-element`, `group`, the `gate`
   and `rule` that complete operation, and the whole of market, obligation and domain.
4. **Packs** — the mechanism above, deliberately undesigned until a second kind of company
   asks for one.
5. **Tooling** — designed, not built:
   [its design](https://github.com/companygraph/meta-model/blob/main/docs/superpowers/specs/2026-08-25-companygraph-tooling-design.md).
   A separate repository, `companygraph/tooling`, Node with no dependencies, run as
   `npx companygraph` in the manner of [spec-kit](https://github.com/github/spec-kit):
   `init` scaffolds an instance from a bundled or fetched release of this repository,
   `add` writes an entity from its schema, `check` runs the mechanical part of the
   conventions, `upgrade` brings a vendored core to a newer release — and it installs the
   agent skills for validating an instance, adding to it, exporting it as a loadable skill and
   producing the content of a surface. Its
   half of the contract lives here: `core/manifest.json` naming a version and a shape, and
   a tag on every release.
6. ✅ **The checker** — the checks that are about an instance rather than about the meta-model
   ship as `companygraph-meta-model/checks`, and an instance runs them through a reusable
   workflow at the release its manifest names. They read the schemas from the core your
   instance vendored, never from the core in the package, so the Markdown schemas are their
   source of truth — safe because the meta-model's own suite holds every schema to its fixed
   shape. What they cannot read, a schema's writing rules, stays with an agent. The tooling's
   `check` will run these same checks.
7. ✅ **The MCP server** — [`companygraph/mcp-server`](https://github.com/companygraph/mcp-server),
   the way an agent reaches a model without being handed the files. It asks which types a
   company declares, what one entity says and what evidence a claim rests on, read-only, and
   every answer is what the model says at one commit. It parses a snapshot with the meta-model's
   own parser, so a new type in core arrives without a change to the server and it knows no
   instance's names or facts. The reference instance runs it at
   [mcp.blust.ch](https://mcp.blust.ch/mcp), published to the MCP Registry as
   `ch.blust/mental-model`. It shipped before the tooling above it, which is why a model can be
   read by an agent today and still has to be set up by hand.

[companygraph.io](https://companygraph.io) is the home page. The meta-model and its tooling are open source and stay that way; consulting is the one thing that costs money — [how it is billed →](https://companygraph.io/billing/)

---

*Built spec-first in the open. Early days — star [meta-model](https://github.com/companygraph/meta-model) to follow along.*
