---
tags: [fifo, deque, priority-queue, heap, monotonic-queue]
---

# 队列、双端队列与优先队列

## 根据操作选结构

- 只按到达顺序取出：FIFO queue，端点操作通常 `O(1)`。
- 两端都要插入或取出：deque，端点操作通常 `O(1)`。
- 每次取当前最小或最大优先级：heap-backed priority queue，插入和取出通常 `O(log n)`。
- 固定窗口中反复求最小或最大且窗口单调移动：monotonic deque，整体 `O(n)`。

## 常见误判

- 业务名称叫“任务队列”不代表必须用消息队列；进程内选择下一项可能只需标准库 deque。
- “回收任务优先”仍缺少次序定义：按回收时间可用 deque，按编号或截止时间应使用 heap 或有序索引。
- 如果需要任意位置删除，普通 heap 或 deque 都不能自动提供 `O(1)` 删除。

## 最小验证

写出允许的操作表，并为每项标注目标复杂度。覆盖相同优先级、空结构、重复入队和删除后重入。

## 来源

- [JavaScript Algorithms: Queue](../external/javascript-algorithms/data-structures/queue/README.md)
- [JavaScript Algorithms: Deque](../external/javascript-algorithms/data-structures/deque/README.md)
- [JavaScript Algorithms: Priority Queue](../external/javascript-algorithms/data-structures/priority-queue/README.md)
- [JavaScript Algorithms: Heap](../external/javascript-algorithms/data-structures/heap/README.md)
- [cp-algorithms: Stack and Queue Modification](../external/cp-algorithms/data_structures/stack_queue_modification.md)
- [Open Data Structures: Array-Based Lists and Heaps](../external/open-data-structures/CHAPTERS.md)
