---
tags: [graph, dependency, bfs, dfs, topological-sort, shortest-path]
---

# 依赖图与遍历

## 结构信号

- 实体之间不是单一线性顺序，而是边表示依赖、可达、连接或成本。
- 需要回答是否可达、分层距离、执行顺序、环或最短成本。

## 候选

- **BFS**：无权图的可达性和最少边数，`O(V + E)`。
- **DFS**：连通、环检测和结构遍历，`O(V + E)`。
- **Topological sort**：有向无环依赖的合法执行顺序，`O(V + E)`；存在环时必须失败。
- **Dijkstra**：非负边权的单源最短路径；负权时不适用。

## 淘汰条件

- 关系实际是稳定的一维顺序：数组、索引或双指针通常更简单。
- 只需要精确键查找：图结构会增加无意义状态。

## 最小验证

覆盖孤立节点、重复边、自环、非连通图、依赖环和多条等长路径；最短路额外覆盖零权边并拒绝负权输入。

## 来源

- [cp-algorithms: Breadth First Search](../external/cp-algorithms/graph/breadth-first-search.md)
- [cp-algorithms: Depth First Search](../external/cp-algorithms/graph/depth-first-search.md)
- [cp-algorithms: Topological Sorting](../external/cp-algorithms/graph/topological-sort.md)
- [cp-algorithms: Dijkstra](../external/cp-algorithms/graph/dijkstra.md)
- [Open Data Structures: Graphs](../external/open-data-structures/CHAPTERS.md)
