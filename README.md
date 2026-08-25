# Agentic AI Orchestration Platform

> **Status: in active development.** The figures below are **targets, not measurements.**
> See [CLAIMS.md](CLAIMS.md) for what has actually been measured, on what hardware, at which commit.

Multi-agent runtime with a plan-retrieve-act-critique loop, full tool-call traces, and a 150-case eval harness.

**Target outcome:** `87% success · 150 eval cases`

## What this is

A task submitted over HTTP runs a single tool-calling agent to completion, and every decision it made is queryable afterwards.

Full project spec, milestone plan and progress tracking live in the programme document:
`Desktop/Projects/PROGRAM.md` → section `03 · Agentic AI Orchestration Platform`.

## Stack

- Python 3.12 + uv
- FastAPI + Pydantic v2
- Anthropic Python SDK (claude-opus-5 tool calling, prompt caching)
- SQLAlchemy 2 + Alembic
- PostgreSQL 16
- Weaviate (local) with a Pinecone backend behind one store interface
- WebSockets (native FastAPI)
- React 19 + Vite + TypeScript
- Docker Compose (WSL2 backend)
- pytest + ruff + mypy
- GitHub Actions

## Roadmap

- [ ] **M1. Walking skeleton: one agent, one trace** — A task submitted over HTTP runs a single tool-calling agent to completion, and every decision it made is queryable afterwards.
- [ ] **M2. Live trace console over WebSockets** — You can watch a run happen — every model decision and tool call appears in a browser as it is emitted, not after the fact.
- [ ] **M3. Knowledge plane and a retrieve tool that cites** — The agent can ground answers in a real corpus, and every retrieved chunk is attributable back to a source span from the trace alone.
- [ ] **M4. The four-agent loop** — Planner, retriever, executor and critic take real turns over shared task state under explicit tool contracts and a hard step budget.
- [ ] **M5. Sandboxed execution and bounded recovery** — A tool call that fails is captured as structured evidence, the critic proposes a correction, and retries stop exactly where policy says they stop.
- [ ] **M6. Evaluation harness and a smoke suite** — Any change to a prompt or the loop can be scored the same way twice, with cost and per-stage failure attribution attached.
- [ ] **M7. core-150 and the number** — A frozen 150-case suite with a calibrated grader produces a success rate you would defend to someone who has read the code.
- [ ] **M8. Replay, checkpoints and governance** — Any historical run can be reconstructed exactly, and nothing sensitive ever reaches the record.
- [ ] **M9. Ship it: one-command bring-up, CI, and page parity** — A stranger can clone the repo, run the four commands the portfolio page advertises verbatim, and get the system the page describes.

## Running it

Not yet runnable — see the roadmap above. Build instructions land with M2.

## Licence

MIT — see [LICENSE](LICENSE).
