# Repolex Knowledge Graph of gotcha/ipdb

RDF knowledge graph data for [gotcha/ipdb](https://github.com/gotcha/ipdb), parsed by [repolex](https://repolex.ai).

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
rlex download gotcha/ipdb
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── be12fe3b3a043f0bb0d0e9ee78b896287c361d05
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── be12fe3b3a043f0bb0d0e9ee78b896287c361d05
│           └── chunk-001.nq.gz
├── blob
│   ├── 088871b362b12421f81df47a1f2c3b7c2e872f17.nq.gz
│   ├── 0d136ebe0c8c42b1ac336c1d216bb99a328fcf7e.nq.gz
│   ├── 160fabdaf50a83abf392819e6e22ba773d3797a7.nq.gz
│   ├── 2516ae24e88c27ba6e3d63a18228165de5f74650.nq.gz
│   ├── 2b3b45036fd416869d53a4ff034217996923b32f.nq.gz
│   ├── 2e6b97774c961058d673199fa368094f4ca16a6d.nq.gz
│   ├── 3a96dab72b880e2d347cb388be9b5d1cdbb3a4b0.nq.gz
│   ├── 62b0a1f828cde568e449dc8c09f5090eb872af94.nq.gz
│   ├── 65cc3b4b255866911ebb253bb809d6591dba43cb.nq.gz
│   ├── 72bc19366db6b749d5ab8e8daf9a7d4d9e17e455.nq.gz
│   ├── 783708e12db1d6b1785992f6ac3ccc3c2c1ad0d0.nq.gz
│   ├── 7f57efb93d02373ba9ddcbb80bff505cff2f361c.nq.gz
│   ├── 933aa120987b6323ac8e0c1da995f157e990a83b.nq.gz
│   ├── b9a8d87c74188ae2c2ab98ea2ca3d1639579f778.nq.gz
│   ├── c4b649ab9f9985d2d1d381b2883381d26aca8345.nq.gz
│   ├── e43e58118079b6db6802cf8c83d83f9a89edebd2.nq.gz
│   ├── e4fc7e7bbf2c998160eddbe3639e754866bfe722.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── be12fe3b3a043f0bb0d0e9ee78b896287c361d05.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 26 files
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

[gotcha/ipdb](https://github.com/gotcha/ipdb)

---
*Parsed on 2026-10-18 by [repolex](https://repolex.ai)*
