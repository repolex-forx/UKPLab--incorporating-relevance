# Repolex Knowledge Graph of UKPLab/incorporating-relevance

RDF knowledge graph data for [UKPLab/incorporating-relevance](https://github.com/UKPLab/incorporating-relevance), parsed by [repolex](https://repolex.ai).

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
rlex download UKPLab/incorporating-relevance
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 454a5c7585649aefd1d3f91b58bf6feee2d2d0d9
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 454a5c7585649aefd1d3f91b58bf6feee2d2d0d9
│           └── chunk-001.nq.gz
├── blob
│   ├── 0218d4a0984ff64003441706b86ea0e8c836f3d5.nq.gz
│   ├── 0a63c3616f9b1ea42ec251f2b66b20ab707ed709.nq.gz
│   ├── 0e1ff3498c502e63cfc660500bd496552cdbcb3e.nq.gz
│   ├── 0f2ac6aeb2d693ea293c169d5af9fb2e9d16ed5f.nq.gz
│   ├── 22ec31eb9a262690cea41b5bb17693d5424475ae.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 26f4dab50c27ddfbe2eab6b71e6a6ce16318fcad.nq.gz
│   ├── 2e7990d55efeb5c22f9e0fb49d47073a60a0b7cd.nq.gz
│   ├── 326c8d85c3f2998f57ff08a6221d376257d8b755.nq.gz
│   ├── 350481765c827e1b552a56ef2991ebc263c94dc9.nq.gz
│   ├── 3e78956e38805ee6aa5b0216dafddc86f9796b40.nq.gz
│   ├── 435079faa2d19e38bc332a84799856ba618d2764.nq.gz
│   ├── 4526b2af58619ed0426ea1e7ff9a495d1f59e715.nq.gz
│   ├── 620f5ee4025f7dc599f545279db6aa65fa11bb64.nq.gz
│   ├── 6783c63aefd7fb84fcc3b2c6998defd034b45454.nq.gz
│   ├── 69cff6167af431e3818795d207f437b63178b676.nq.gz
│   ├── 6ccf9477560488b02a0d3acc67bc93f377a0fef4.nq.gz
│   ├── 6f0b46b609161edd8e7c63fbcb8fac2ed418f4c7.nq.gz
│   ├── 77b60d8c8ba8cbad9d0d457e0a06444d15204c46.nq.gz
│   ├── 831e7ea9aa6b3a3657002d4ac622d8d0f9499299.nq.gz
│   ├── 8475f29367899de0d7b2217ed3acda781ec21453.nq.gz
│   ├── 894a4202b594c80e057a424192f8be5a35953028.nq.gz
│   ├── 8a5b307848c915a5ac326314a449ee0e612e9e09.nq.gz
│   ├── 91af37bf1eea2680e413be79e1b8ee1c1b179752.nq.gz
│   ├── 9b57fc819f65f0e29dd69b0573707a2640a7a825.nq.gz
│   ├── 9e63f2fc215a905e5def3406f9746a324f7508bc.nq.gz
│   ├── aa990a1822c6d224f7ebf286f7b5ded211c3429e.nq.gz
│   ├── ac5e9f376d958e985af1a5e0daed7a7c029fc496.nq.gz
│   ├── b20ec8a1aaca05ad7194c2735167f89dfe181bfb.nq.gz
│   ├── b55c08180ad12f1873d5cdda83f4abe61eccb27e.nq.gz
│   ├── c0a193d3bc61ced6f41e2b69613a0c26da078f52.nq.gz
│   ├── d0d299454ce30274c847a676444a3a3257bac15e.nq.gz
│   ├── e13624273a939ce77a514dfa48aa9bd0a0c07c97.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ed1406067a5baecc32bb0ae8dca215332fe646bf.nq.gz
│   ├── f19fb0b3b06393111ca64502fab16545304c4764.nq.gz
│   └── f62fb91eec1d3056dca7cde2e8370fed542e7ca7.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 454a5c7585649aefd1d3f91b58bf6feee2d2d0d9.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 44 files
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

[UKPLab/incorporating-relevance](https://github.com/UKPLab/incorporating-relevance)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
