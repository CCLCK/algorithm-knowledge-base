---
tags: [two-pointers, monotone, cursor, sliding-window, cycle-detection]
---

# 单调双指针扫描

## 结构信号

- 数据存在稳定顺序。
- 两个位置代表不同边界或不同速度，并且只能单调向前。
- 每个元素最多被一个或两个指针访问常数次。

## 候选

- **左右边界 / sliding window**：窗口扩大和缩小时两个边界都不后退，通常为 `O(n)`。
- **两路合并**：两个有序序列各维护一个当前位置，通常为 `O(n + m)`。
- **快慢指针**：适合链式状态中的环检测或中点定位，空间 `O(1)`。
- **持久化 cursor**：跨请求顺序消费固定数据时，把“下一个未处理位置”作为权威状态。

## 淘汰条件

- 状态可任意回退，或元素会重新插入指针之前。
- 每一步需要全局最小值或可变优先级；这通常需要 heap 或有序索引。
- 数据顺序本身不稳定。

## 最小验证

证明每个指针从不后退，并用访问计数器验证总移动次数不超过输入规模的常数倍。覆盖空输入、指针相遇、末端和重复值。

## 来源

- [cp-algorithms: Tortoise and Hare](../external/cp-algorithms/others/tortoise_and_hare.md)
- [JavaScript Algorithms: Deque](../external/javascript-algorithms/data-structures/deque/README.md)
