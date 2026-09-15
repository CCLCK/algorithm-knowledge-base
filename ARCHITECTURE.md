# Architecture baseline

- **Need:** give an Agent a stable, inspectable source for mapping business structures to candidate algorithms.
- **Lifetime and scale:** long-lived reference repository; initially tens of pattern cards and fewer than 300 source documents.
- **Smallest complete design:** static Markdown, one routing index, original pattern cards, immutable third-party snapshots, and one source registry.
- **Canonical state:** `INDEX.md` is the only active routing catalogue; `SOURCES.md` is the only source registry.
- **Proving check:** a task-allocation scenario must route from structural signals to the two-frontier/reclaim pattern and expose its invariants and boundary tests.
- **Upgrade trigger:** consider hybrid or vector retrieval only after the corpus exceeds roughly 300 documents or measured retrieval evaluations show repeated misses that structured tags and `rg` cannot fix.

No runtime, framework, database, site generator, or package dependency is part of this baseline.
