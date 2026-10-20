# Repolex Knowledge Graph of pre-commit/pygrep-hooks

RDF knowledge graph data for [pre-commit/pygrep-hooks](https://github.com/pre-commit/pygrep-hooks), parsed by [repolex](https://repolex.ai).

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
rlex download pre-commit/pygrep-hooks
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── bc3cc02ec801748199091b05f6289790e328b665
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── bc3cc02ec801748199091b05f6289790e328b665
│           └── chunk-001.nq.gz
├── blob
│   ├── 022e3dc72b1c03413ff61d9b530af66bc7e9d847.nq.gz
│   ├── 0d20b6487c61e7d1bde93acf4a14b7a89083a16d.nq.gz
│   ├── 27271818d621a2bc4d2150f1d22a1edc7a4f3f89.nq.gz
│   ├── 6cee8165d63da453a392f95b8b1d71c4f9b309b9.nq.gz
│   ├── ac7dd263b587bc5c2c87f7359c0d66fa30a9ceba.nq.gz
│   ├── b7af5ef213084fe100c5bb755659ef68c14dae5b.nq.gz
│   └── dc9dc20a7bebba97e123cd670a49a4184025bf20.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── bc3cc02ec801748199091b05f6289790e328b665.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 15 files
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

[pre-commit/pygrep-hooks](https://github.com/pre-commit/pygrep-hooks)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
