---
tags: [dynamic-programming, recurrence, overlapping-subproblems, memoization, staircase]
---

# 递推与动态规划

## 结构信号

- 当前答案可以由规模更小的状态组合得到。
- 相同子状态会被多条递归路径重复计算。
- 状态和转移可以明确枚举，并存在可证明的计算顺序。

## 候选

- **Memoization**：只计算实际访问的状态，时间约为“状态数 × 每个状态的转移数”。
- **Bottom-up DP**：按依赖顺序填表，避免递归栈。
- **Rolling state**：只依赖前几个状态时，把空间从 `O(n)` 降到 `O(1)`。

“爬楼梯”只有在问题是按固定步长计算路径数或最优成本时才符合这些信号。若楼层代表网络节点、任务位置或可变约束，可能应建图或使用其他方法。

## 淘汰条件

- 子问题不重复：分治可能已经足够。
- 贪心选择具有可证明的交换性质：DP 可能是不必要的高成本。
- 状态定义包含完整历史，导致状态空间指数增长：先寻找更小的充分状态。

## 最小验证

先写指数级或小规模穷举 oracle，再与 DP 在随机小输入上比较。覆盖零状态、最小状态、不可达状态和非常大的 `n`。

## 来源

- [cp-algorithms: Introduction to Dynamic Programming](../external/cp-algorithms/dynamic_programming/intro-to-dp.md)
- [JavaScript Algorithms: Recursive Staircase](../external/javascript-algorithms/algorithms/uncategorized/recursive-staircase/README.md)
- [JavaScript Algorithms: Unique Paths](../external/javascript-algorithms/algorithms/uncategorized/unique-paths/README.md)
