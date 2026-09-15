---
tags: [complexity, benchmark, operation-counter, doubling-test, explain, query-plan]
---

# 性能验证

## 先证明值得优化

记录真实的 `n`、结果规模 `k`、调用次数、读写比例、增长率和延迟预算。一次性小输入或由网络、磁盘主导的路径，通常不值得先改数据结构。

## 三层证据

1. **复杂度模型**：指出朴素方案的主导操作和候选方案的查询、更新、空间成本。
2. **与机器无关的检查**：为循环或扫描添加操作计数器；在递增 `n` 上确认增长阶。
3. **真实系统检查**：数据库使用 `EXPLAIN`/查询计划，I/O 路径做端到端测量，缓存记录命中率。

## 最小验证

- 保留一个明显正确的朴素实现作为小输入 oracle。
- 在随机输入上比较优化实现与 oracle。
- 使用倍增规模观察时间或操作数比例，不从玩具数据外推生产性能。
- 同时测量冷启动、热缓存、最坏输入和并发场景中真正相关的一项。

## 停止条件

候选方案达到预算且没有增加不可接受的一致性或维护成本后停止。更低的渐进复杂度不自动代表更快的实际实现。

## 来源

- [MIT 6.006 Lecture 1: Efficiency](../external/mit-6.006-lecture-01/fulltext.md#efficiency)
- [Princeton: Analysis of Algorithms](https://algs4.cs.princeton.edu/14analysis/)
- [SQLite Query Planner](https://www.sqlite.org/queryplanner.html)
- [PostgreSQL: Using EXPLAIN](https://www.postgresql.org/docs/current/using-explain.html)
- [Open Data Structures: Introduction and cost model](../external/open-data-structures/CHAPTERS.md)
