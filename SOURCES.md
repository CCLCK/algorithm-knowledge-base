# Source registry

Retrieved on 2026-09-15. Third-party snapshots are kept unchanged except where an entry explicitly records conversion.

| Source | Local scope | Upstream revision | License | Why included |
|---|---|---|---|---|
| [cp-algorithms](https://github.com/cp-algorithms/cp-algorithms) | `external/cp-algorithms/` | `a83398769aff7011f52a4ad0c67d4051718cdcb8` | CC BY-SA 4.0 | Complete unmodified Markdown source tree and its media: searching, dynamic programming, graphs, scheduling, queues, range structures and related algorithms. |
| [JavaScript Algorithms and Data Structures](https://github.com/trekhleb/javascript-algorithms) | `external/javascript-algorithms/` | `85293e3e2b88f4d2ce330d956b139cf628aa1e82` | MIT | Explanatory `README.md` files and their images; implementation and test code are intentionally omitted to reduce retrieval noise. |
| [System Design Primer](https://github.com/donnemartin/system-design-primer) | `external/system-design-primer/` | `ae9bbd7b02d90b9866215de185217d33f39ab733` | CC BY 4.0 | Engineering trade-offs for caching, queues, indexing, consistency and scaling. |
| [MIT 6.006 Spring 2020, Lecture 1](https://live.ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/477c78e0af2df61fa205bcc6cb613ceb_MIT6_006S20_lec1.pdf) | `external/mit-6.006-lecture-01/` | Source SHA-256 `8f2f9c1ce1b63313344c86491870e487da796de71b3312ea05b681a00a5b2de5` | CC BY-NC-SA 4.0 | Formal problem, correctness and efficiency workflow. The official PDF, converted Markdown and table images are preserved. |

## Reference-only sources

These sources are useful but are not copied into the repository because their format, license, or size does not justify another snapshot.

- [Open Data Structures](https://opendatastructures.org/) — CC BY; comprehensive data-structure textbook with HTML, PDF and source. Its 326-page PDF was valid but the configured conversion API returned `remote_pdf_rejected`, so the repository links to the maintained upstream instead of introducing a second conversion path.
- [The Algorithm Design Manual repository](https://www.algorist.com/algorist.html) — useful inverse taxonomy for identifying problem families.
- [Introduction to Algorithms, Fourth Edition](https://mitpress.mit.edu/9780262046305/introduction-to-algorithms/) — rigorous verification reference; no redistributable full-text snapshot is included.
- [Princeton Algorithms, Analysis of Algorithms](https://algs4.cs.princeton.edu/14analysis/) — experimental cost models and doubling tests.
- [SQLite Query Planner](https://www.sqlite.org/queryplanner.html) and [PostgreSQL EXPLAIN](https://www.postgresql.org/docs/current/using-explain.html) — implementation-stage verification for database access paths.

## Source handling rule

Only copy material whose upstream license permits public redistribution and adaptation. For any new source, record the canonical URL, exact revision or file hash, license, retrieval date, local scope, and whether the content was modified or converted.
