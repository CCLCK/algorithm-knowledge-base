---
tags: [range-query, prefix-sum, fenwick-tree, segment-tree, read-write-ratio]
---

# 范围查询与更新

## 结构信号

- 在数组或有序键空间上反复查询区间和、最值或其他可合并统计量。
- 选择取决于查询与更新的比例，而不只取决于数据量。

## 候选

| 条件 | 结构 | 查询 | 单点更新 |
|---|---|---:|---:|
| 数据静态，区间和很多 | prefix sum | `O(1)` | `O(n)` 重建或维护 |
| 动态前缀/区间和 | Fenwick tree | `O(log n)` | `O(log n)` |
| 动态范围统计或更复杂合并 | segment tree | `O(log n)` | `O(log n)` |
| 查询很少或数据很小 | 直接扫描 | `O(n)` | `O(1)` |

Segment tree 的内存和实现复杂度更高；只有 Fenwick 或 prefix sum 不能表达所需合并时才采用。

## 最小验证

使用朴素数组作为 oracle，随机生成更新和查询序列做差分比较。覆盖空区间、单元素、全区间、首尾边界和负数。

## 来源

- [cp-algorithms: Fenwick Tree](../external/cp-algorithms/data_structures/fenwick.md)
- [cp-algorithms: Segment Tree](../external/cp-algorithms/data_structures/segment_tree.md)
