# atlas

Turn a stated need into a full system design by mining the Atlas knowledge graph.

Atlas is a knowledge graph of AI-agent stacks, products, capabilities, processes,
data models, and the relationships between them. This plugin makes that graph a
first-class design tool inside Gemini CLI: ask for a system and Atlas
mines the graph to turn the stated need into a layered, evidence-backed design.

## Installation — Gemini CLI

```bash
npm install -g @a5c-ai/atlas-gemini-cli
atlas-gemini-cli install --global
```

Restart Gemini CLI to pick up the installed plugin.

## What's Included

- **Skills**: atlas, atlas-graph-query
- **Commands**: (directory)
- **MCP**: the Atlas knowledge-graph server (`atlas`), wired natively into
  Gemini CLI's own MCP config — no manual setup.

## Atlas MCP

The plugin injects the Atlas MCP server into Gemini CLI's native MCP
config format automatically. By default it points at:

```
https://atlas-staging.a5c.ai/api/mcp
```

Override the endpoint at runtime with the `ATLAS_MCP_URL` environment variable.
Once the harness is running, the `mcp__atlas__atlas_public_*` tools (search,
record, neighbors, kinds, clusters, stats, wiki pages) are available to the
skills and commands.

## How it works

- The **`atlas` skill** turns a stated need into a layered system design by
  mining the graph — when to use Atlas, how to anchor a search, expand
  neighbors, and synthesize a design.
- The **`atlas-graph-query` skill** documents the MCP tool surface so any agent
  (sub-agents included) can query the graph without re-deriving conventions.
- The **commands** (`(directory)`) run interactive, graph-driven workflows —
  systems discovery, process mining, data mining, and nuance collection. They
  drive iterative, TDD-style runs whose orchestration is delegated to the
  Babysitter run lifecycle, so each phase is checkable and resumable.

> The commands use Babysitter purely as the orchestration runtime; the design
> work itself is driven by the Atlas graph via the MCP tools above.

## Verification

```bash
babysitter harness:discover --json | grep gemini
```
