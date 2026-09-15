# Structural routing index

先写出业务的结构签名，再进入模式卡。故事名称只能帮助理解，不能作为选择算法的证据。

## 最小结构签名

- 数据实体及稳定标识是什么？
- 核心操作是精确查找、范围查找、顺序消费、优先选择、聚合还是依赖遍历？
- 数据是否有序；顺序是否会变化？
- 状态能否回退、重复或被并发修改？
- 数据规模 `n`、每次结果规模 `k`、调用频率和读写比例是多少？
- 必须保持哪些不变量；失败或重试后如何恢复？

## 按结构信号检索

| 结构信号 | 首选模式卡 | 常见候选 |
|---|---|---|
| 重复进行等值查找、判重或成员判断 | [精确键查找](patterns/exact-key-lookup.md) | hash map/set、数据库索引、Bloom filter |
| 数据有序，寻找第一个满足条件的位置或边界 | [有序边界查找](patterns/ordered-boundary-search.md) | binary search、B-tree index |
| 两个位置只向前移动；元素最多被访问常数次 | [单调双指针扫描](patterns/monotonic-two-pointer-scan.md) | two pointers、sliding window、fast/slow pointer |
| 固定任务序列顺序发放，同时存在少量回收任务 | [任务分配与回收](patterns/task-allocation-with-reclaims.md) | fresh cursor + reclaim frontier、deque、min-heap |
| 按到达顺序、两端或优先级反复取下一项 | [队列、双端队列与优先队列](patterns/queue-deque-priority.md) | queue、deque、heap、monotonic deque |
| 静态或动态数组上反复做区间聚合 | [范围查询与更新](patterns/range-query-update.md) | prefix sum、Fenwick tree、segment tree |
| 实体之间存在依赖、连通关系或带权路径 | [依赖图与遍历](patterns/dependency-graph-traversal.md) | BFS、DFS、topological sort、Dijkstra |
| 状态由较小状态递推，子问题重复出现 | [递推与动态规划](patterns/dynamic-programming-recurrence.md) | memoization、bottom-up DP、rolling state |
| 同一昂贵读取反复发生且允许定义明确的新鲜度 | [热点读取与缓存](patterns/caching-hot-reads.md) | request cache、LRU、cache-aside |
| 已有候选优化，但尚未证明真实收益 | [性能验证](patterns/performance-validation.md) | operation counter、doubling test、EXPLAIN、benchmark |

## 选择规则

1. 先判断朴素方法是否已经满足实际预算；满足则停止。
2. 每次最多保留三个候选，并写出各自的成立条件。
3. 优先选择状态最少、标准库或平台已提供、且能用一个小测试证明的方案。
4. 算法复杂度不能替代数据库事务、并发一致性或网络与磁盘测量。
