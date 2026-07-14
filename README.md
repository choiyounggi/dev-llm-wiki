# dev-llm-wiki

**English** | [한국어](README.ko.md)

A case-routed wiki of development best practices and edge cases, **written for LLM
agents to load as working context** — so an agent working on your task pulls in
exactly the guidance that applies, and nothing else.

Built on [Andrej Karpathy's LLM-wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f):
markdown pages an agent maintains, a schema that disciplines it, and
ingest/query/lint workflows that make knowledge compound instead of rot.

## Why this exists

Agents make fewer mistakes when the right practice for the *specific situation* is
in context — not a 5,000-word style guide, not a "top 10 tips" post. That takes
three properties most knowledge bases don't have:

1. **Case routing.** Every page declares *when it applies*. Indexes are maps of
   triggers, so an agent (or you) descends `INDEX.md` → domain → page and loads only
   what matches. No bulk context, no noise.
2. **Positive guidance.** Every directive is "in situation X, do Y". Prohibitions
   are only allowed when paired with their replacement — a bare "don't" leaves the
   next step to the reader's imagination, which for an LLM is how hallucinations start.
3. **Evidence discipline.** Every page cites sources and carries a confidence tag
   (`verified` / `field-tested` / `unverified`). Lint hunts unsourced claims, so
   plausible-sounding fabrications can't quietly become "knowledge".

## Use it with your agent

```bash
git clone https://github.com/choiyounggi/dev-llm-wiki.git
```

- **Claude Code / Codex / Cursor etc.**: the repo ships `AGENTS.md` (schema) and
  `CLAUDE.md`; opening the repo teaches the agent the routing protocol. Point your
  agent at it, or symlink the repo into your workspace and reference it.
- **Manual**: start at [INDEX.md](INDEX.md), follow the "route here when" lines.

Three operations (agent workflows in `skills/`):

| Operation | Use |
|-----------|-----|
| `skills/ingest` | Add knowledge — a lesson learned, an edge case, a sourced practice. Merges into existing pages, enforces sourcing and positive framing |
| `skills/query` | Answer a question from the wiki with citations; recurring syntheses get filed back as pages |
| `skills/lint` | Health check — unsourced claims, bare prohibitions, broken links, stale pages |
| `skills/plan` | For a capable model: make every design decision (wiki-grounded) and decompose work into ordered task files sized so a small model can execute each one with only the task + its mapped wiki pages |
| `skills/implement` | For the small model executing one planned task: load only what the task names, never improvise (missing decisions → BLOCKED report, not a guess), verify, report |

## Status

Seeded domain: **databases** (indexing, query optimization, schema design,
transactions — 15 pages). Other domains (backend, frontend, infrastructure, testing,
debugging, security, platforms, mobile) are scaffolded and grow by ingestion.

Contributions welcome: run the ingest workflow with your agent, or open a PR that
follows `templates/page.md` and the rules in `AGENTS.md`.
