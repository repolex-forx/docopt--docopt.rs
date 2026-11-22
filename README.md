# Repolex Knowledge Graph of docopt/docopt.rs

RDF knowledge graph data for [docopt/docopt.rs](https://github.com/docopt/docopt.rs), parsed by [repolex](https://repolex.ai).

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
rlex download docopt/docopt.rs
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1a02d9760417429688e76ed278707e2872d011d1
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 1a02d9760417429688e76ed278707e2872d011d1.nq.gz
│   └── repolex
│       └── 1a02d9760417429688e76ed278707e2872d011d1
│           └── chunk-001.nq.gz
├── blob
│   ├── 03314f77b5aa454994bf08c40943f4012964eb0a.nq.gz
│   ├── 0666206868c4ef523bb6905013fdb35fca6394e2.nq.gz
│   ├── 0c6e64e4117bc7c77443280b151ecf5780bb72e1.nq.gz
│   ├── 10786f1983cb8e2d77a4bfc213334c1515bd17e1.nq.gz
│   ├── 189ba620c4a80bfd92e0a4f44aaefac2ce023541.nq.gz
│   ├── 22991941f74a2a6fae223632fd1679b59af97cd8.nq.gz
│   ├── 256b815e0bec2c9995b2bf334f662d5b39fbf6f4.nq.gz
│   ├── 271d388badfb7bc045fa459a6b600f3a7f7a3e09.nq.gz
│   ├── 2d8ada0ebdb7abb5bf7169deb65c8d1abce6451f.nq.gz
│   ├── 30ededbf02e03c0ca20f00fbb8059480690a96ae.nq.gz
│   ├── 3b0a5dc09c1e16357459ddc9182a50f360f3cdba.nq.gz
│   ├── 493db2ba2bd0c29ea0ced3649a7bb830dc4e5274.nq.gz
│   ├── 50f849dfbe5f221d90251f3416bfb1200864b429.nq.gz
│   ├── 59eea67a1a47080d412c5f0f87590ac462e2c54c.nq.gz
│   ├── 64253451d22ae325b6854d3104acec049ad30d23.nq.gz
│   ├── 6464bd16ec4e75c30ac7816d8af26dc23dd4acdd.nq.gz
│   ├── 64d2ec820d757c8cb8092ef74e5bc1bd64d027b8.nq.gz
│   ├── 6803419d5d2f1a5f55b7a40bb2a2e0c552960401.nq.gz
│   ├── 682bf00d28ea6ae2cc76d95e0d58076cc4a19790.nq.gz
│   ├── 68a49daad8ff7e35068f2b7a97d643aab440eaec.nq.gz
│   ├── 77bf47fbb33f7adf249c46229a7ffb8caa0b086a.nq.gz
│   ├── 8b2b47fc95b3bc932dcce6f4d61902050e281da2.nq.gz
│   ├── 8d8a3f38f2033fb4fd5cce0072ff5016d09a3456.nq.gz
│   ├── 902f926f940b6d1106f50153cd2914682b25a1c0.nq.gz
│   ├── 9033a20d3372dbe2f0d4188609c3f834657c693e.nq.gz
│   ├── 9e1b75403dbedcbe911d8525a05525dfbf0762b6.nq.gz
│   ├── 9f4f783471fb11543750bb5c901173132d22c00f.nq.gz
│   ├── a3b6d054be1f5e0740afab6d504ed574b32270b5.nq.gz
│   ├── a8b7585ae84ac39759ce6fee24fa0e3ae3d1cbec.nq.gz
│   ├── b42edf7579a644f790c1f9b4d462441e87ce26f9.nq.gz
│   ├── bb9c20a094e41b7632d63bcff20c0b4b95e80777.nq.gz
│   ├── e3bb1f6fc87ca209028b0a4db34e7ba45f4ada3b.nq.gz
│   ├── e972d882f0245f64553f699ab9433ed619799eaf.nq.gz
│   └── ed84508b0df45ac90fea5297e47ca0b0a3a1d83e.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 1a02d9760417429688e76ed278707e2872d011d1.nq.gz
├── filetree
│   └── 1a02d9760417429688e76ed278707e2872d011d1.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 44 files
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

[docopt/docopt.rs](https://github.com/docopt/docopt.rs)

---
*Parsed on 2026-11-22 by [repolex](https://repolex.ai)*
