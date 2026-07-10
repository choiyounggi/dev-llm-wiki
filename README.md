# dev-llm-wiki

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

## Status

Seeded domain: **databases** (indexing, query optimization, schema design,
transactions — 15 pages). Other domains (backend, frontend, infrastructure, testing,
debugging, security, platforms, mobile) are scaffolded and grow by ingestion.

Contributions welcome: run the ingest workflow with your agent, or open a PR that
follows `templates/page.md` and the rules in `AGENTS.md`.

---

## 한국어 안내

**dev-llm-wiki**는 LLM 에이전트가 작업 컨텍스트로 로드하도록 설계된, 케이스
라우팅형 개발 베스트 프랙티스·엣지케이스 위키입니다.
[Karpathy의 LLM 위키 패턴](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
위에 세 가지 규율을 얹었습니다:

1. **케이스 라우팅** — 모든 페이지는 "언제 적용되는가"를 선언합니다. 에이전트는
   `INDEX.md` → 도메인 인덱스 → 페이지로 타고 내려가 **해당되는 페이지만** 로드
   합니다. 불필요한 컨텍스트가 섞이지 않습니다.
2. **긍정 유도형 지침** — 모든 지침은 "상황 X에서는 Y를 하라" 형식입니다.
   금지("하지 마라")는 반드시 대체 행동과 짝을 이룰 때만 허용됩니다. 대체 없는
   금지는 다음 행동을 상상에 맡기게 되고, 그것이 할루시네이션의 시작점이기
   때문입니다.
3. **근거 규율** — 모든 페이지는 출처를 인용하고 신뢰도 태그(`verified` /
   `field-tested` / `unverified`)를 가집니다. lint가 무출처 주장을 추적하므로
   그럴듯한 지어낸 지식이 위키에 스며들지 못합니다.

**사용법**: 레포를 clone하면 `AGENTS.md`(스키마)가 에이전트에게 라우팅 규약을
가르칩니다. 지식 추가는 `skills/ingest`, 질의는 `skills/query`, 건강 점검은
`skills/lint` 워크플로우로 — 쓸수록 지식이 복리로 쌓이는 구조입니다.

현재 **databases** 도메인 15페이지가 시드되어 있고, 나머지 도메인은 골격 상태로
ingest를 통해 성장합니다.
