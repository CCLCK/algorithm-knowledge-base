---
tags: [ordered-data, monotone-predicate, boundary, binary-search, b-tree]
---

# 有序边界查找

## 结构信号

- 数据已按目标键排序，或谓词随位置单调地从 false 变为 true。
- 目标是第一个、最后一个、下界、上界或插入位置。
- 同一有序数据会被多次查询。

## 候选

- **Binary search**：数组查询 `O(log n)`、额外空间 `O(1)`。
- **B-tree 类数据库索引**：适合持久化数据的等值、排序和范围访问；最终以查询计划为准。

## 淘汰条件

- 数据未排序且只有一次查询：先排序会产生 `O(n log n)` 成本，线性扫描可能更便宜。
- 谓词不单调：binary search 不能保证正确。
- 数组频繁中间插入：查询虽快，更新仍可能 `O(n)`。

## 最小验证

覆盖空输入、单元素、目标小于/大于全部元素、重复值、全 false、全 true 和半开区间边界。

## 来源

- [cp-algorithms: Binary Search](../external/cp-algorithms/num_methods/binary_search.md)
- [JavaScript Algorithms: Binary Search](../external/javascript-algorithms/algorithms/search/binary-search/README.md)
