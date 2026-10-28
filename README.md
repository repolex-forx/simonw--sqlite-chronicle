# Repolex Knowledge Graph of simonw/sqlite-chronicle

RDF knowledge graph data for [simonw/sqlite-chronicle](https://github.com/simonw/sqlite-chronicle), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download simonw/sqlite-chronicle
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── ee8d2a1db5090d14279f0acb56b5d46a5c50e44c
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── ee8d2a1db5090d14279f0acb56b5d46a5c50e44c
│           └── chunk-001.nq.gz
├── blob
│   ├── 02a916d4bbed1720f974b78b2400b71ca85eb686.nq.gz
│   ├── 152886dd75604a6b45c24795792c004fa0d55096.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 47745894697f9ac8a5f7eb27156fa373c92c3742.nq.gz
│   ├── 4da36f4e2eb817a8448f42b9131f9779bb858f89.nq.gz
│   ├── 72dd813218cdc8a87c7dc75f04e3cf5aa2b51754.nq.gz
│   ├── 7ae3fe97e80d8db843bea5820cd4b79e6a397666.nq.gz
│   ├── 80ca58ed5d74ee7d088ecaca7ddae7d72f404d57.nq.gz
│   ├── 96cafb6fe78d31c36eb051241e56b3e0bf9836e3.nq.gz
│   ├── 9ea765863e82622e551fd50a5bef1116ada177f5.nq.gz
│   ├── bfc17776c84de21c679b43dd4cbbb5a04c88df25.nq.gz
│   ├── d0d5ce3ee8fa6494d61b4f902ee7d8de943e1b36.nq.gz
│   ├── d655cea0ef87da4cecdb23d13b000ff1bc40543c.nq.gz
│   ├── d6f0c5142e5a1ffb223a6f406af9c98e0172ba74.nq.gz
│   ├── dac6ebb41c57997e09f6c1be952fbe25d628fca7.nq.gz
│   └── dca69cd76c2f4cbb59cc80ecfae0e0959d609411.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── ee8d2a1db5090d14279f0acb56b5d46a5c50e44c.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 24 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[simonw/sqlite-chronicle](https://github.com/simonw/sqlite-chronicle)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
