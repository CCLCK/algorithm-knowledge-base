---
tags: [task-allocation, cursor, two-frontiers, reclaim, idempotency, queue]
---

# 固定任务分配与回收

## 结构信号

- 全部任务形成不可变的全局顺序。
- 从未领取的任务构成一个连续后缀，可由 `fresh_cursor` 指向首项。
- 已领取任务可能部分完成，未完成部分需要回收并优先再次分配。
- 已完成任务永远不能重新发放。

## 最小表示

维护两个前沿，而不是每次扫描全部任务：

1. `fresh_cursor`：首个从未领取的任务，只向后移动。
2. `reclaim_frontier`：回收任务的首项。

如果回收顺序就是“最近回收优先”或明确的链式顺序，用 `next[]` 链或 deque，可在 `O(1)` 取出和插入。如果规则要求“编号最小的回收任务优先”，用 min-heap，取出和插入为 `O(log r)`，其中 `r` 是待回收数量。

任务状态仍是权威事实：`available → owned → completed`；回收只允许 `owned → available`，不能覆盖 `completed`。

## 正确性不变量

- 一次成功领取中，同一任务最多出现一次。
- `fresh_cursor` 之前的任务不等于“已完成”；它们可能已领取、回收或完成，必须由状态区分。
- 提交和完成状态具有幂等键；重复请求不能生成第二份完成记录。
- 分配任务、写入所有者和推进指针必须在同一事务或原子条件更新中完成。

## 边界测试

空任务集、批量大于剩余量、最后一项、部分完成后回收、重复回收、回收后再次放弃、过期所有者、两个并发领取者、提交与回收同时发生、全部完成。

## 复杂度

- 新任务：每项 `O(1)` 均摊。
- 链式回收：每项 `O(1)`。
- 按优先级回收：每项 `O(log r)`。
- 状态持久化成本由实际数据库事务决定。

## 来源

- [JavaScript Algorithms: Queue](../external/javascript-algorithms/data-structures/queue/README.md)
- [JavaScript Algorithms: Deque](../external/javascript-algorithms/data-structures/deque/README.md)
- [JavaScript Algorithms: Priority Queue](../external/javascript-algorithms/data-structures/priority-queue/README.md)
- [MIT 6.006: problem, correctness and efficiency](../external/mit-6.006-lecture-01/fulltext.md)
