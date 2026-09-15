---
tags: [cache, hot-path, repeated-read, lru, invalidation, source-of-truth]
---

# 热点读取与缓存

## 结构信号

- 同一昂贵计算或读取在结果未变化时被反复调用。
- 已测得该操作位于热路径，且命中率足以抵消缓存维护成本。
- 可以明确回答数据允许陈旧多久，以及谁是权威来源。

## 候选

- **进程内 memoization / bounded LRU**：单进程、键稳定、结果可重复计算时的最短路径。
- **Cache-aside**：应用读取权威存储，未命中时填充缓存。
- **预计算**：输入按批次变化、读取远多于写入时，在写入或离线阶段生成结果。

## 淘汰条件

- 请求几乎不重复，命中率低。
- 正确性要求每次读取最新值，但没有可靠失效机制。
- 真实瓶颈是网络传输体积、锁竞争或慢查询；缓存只会遮住根因。

## 不变量

- 权威数据只能有一个来源。
- 缓存键必须包含所有影响结果的输入和版本。
- 写入、删除、过期与失败后的行为必须明确；不得把无界缓存留给长期服务。

## 最小验证

记录命中率、未命中成本、内存上限和陈旧读取行为；在源数据更新后验证缓存按约定失效。

## 来源

- [System Design Primer: Cache](../external/system-design-primer/README.md#cache)
- [JavaScript Algorithms: LRU Cache](../external/javascript-algorithms/data-structures/lru-cache/README.md)
