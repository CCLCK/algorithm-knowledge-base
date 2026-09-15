---
tags: [exact-match, membership, deduplication, hash-map, index, bloom-filter]
---

# 精确键查找

## 结构信号

- 按稳定键反复判断“是否存在”或获取唯一记录。
- 查询以等值比较为主，不要求顺序、前驱、后继或范围结果。
- 查询次数足以使每次全表扫描成为成本。

## 候选

- **Hash map / set**：平均查询与更新 `O(1)`，适合内存中的精确键。
- **数据库索引**：数据由数据库持久化时，让索引和查询计划承担查找，不在应用层复制索引。
- **有序数组 + binary search**：查询 `O(log n)`；只适合静态或少更新数据，因为数组插入通常是 `O(n)`。
- **Bloom filter**：只适合廉价排除“不存在”；允许假阳性，不能返回记录，必须有权威存储复核。

## 淘汰条件

- 需要范围、排序或最近邻：转向有序索引。
- 只执行一次且数据很小：线性扫描通常更简单。
- 键会因大小写、编码或别名漂移：先定义规范化和唯一性，不要让哈希掩盖数据问题。

## 最小验证

覆盖空集合、缺失键、重复键、键规范化和大量冲突；数据库方案同时检查实际执行计划。

## 来源

- [JavaScript Algorithms: Hash Table](../external/javascript-algorithms/data-structures/hash-table/README.md)
- [JavaScript Algorithms: Bloom Filter](../external/javascript-algorithms/data-structures/bloom-filter/README.md)
- [MIT 6.006 Lecture 1](../external/mit-6.006-lecture-01/fulltext.md)
