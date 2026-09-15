# Open Data Structures chapter map

`fulltext.md` is an immutable conversion snapshot. Use this map to read only the relevant line range.

| Lines | Chapter | Structural use |
|---:|---|---|
| 177–744 | 1. Introduction | Efficiency, interfaces, asymptotic analysis, correctness, time and space. |
| 745–1285 | 2. Array-Based Lists | Array stack, queue, deque, resizing, balancing and amortized cost. |
| 1286–1599 | 3. Linked Lists | Singly/doubly linked lists, queue operations, local insertion/removal. |
| 1600–1865 | 4. Skiplists | Ordered search with randomized levels. |
| 1866–2373 | 5. Hash Tables | Chaining, linear probing, hashing and hash codes. |
| 2374–2599 | 6. Binary Trees | Tree traversal and unbalanced binary search trees. |
| 2600–2915 | 7. Random Binary Search Trees | Randomized search trees and treaps. |
| 2916–3139 | 8. Scapegoat Trees | Partial rebuilding and amortized analysis. |
| 3140–3466 | 9. Red-Black Trees | Balanced ordered sets and update invariants. |
| 3467–3646 | 10. Heaps | Binary and meldable heaps; priority queue costs. |
| 3647–3975 | 11. Sorting Algorithms | Merge sort, quicksort, heap sort, counting/radix sort and lower bounds. |
| 3976–4231 | 12. Graphs | Graph representations, BFS and DFS. |
| 4232–4454 | 13. Integer Data Structures | Binary, x-fast and y-fast tries. |
| 4455–4784 | 14. External Memory Searching | Block stores, B-trees and amortized I/O cost. |

Example after cloning the repository:

```bash
sed -n '1866,2373p' external/open-data-structures/fulltext.md
```
