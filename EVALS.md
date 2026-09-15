# Retrieval smoke tests

These cases test routing, not implementation correctness.

| Structural query | Expected first card | Why |
|---|---|---|
| 固定有序任务；未领取部分连续；游标只向后；少量未完成任务回收并优先发放 | `task-allocation-with-reclaims.md` | Two independent frontiers plus immutable completion state. |
| 有序数组；反复寻找第一个大于阈值的位置 | `ordered-boundary-search.md` | Monotone predicate and repeated boundary lookup. |
| 百万条记录；反复按唯一 ID 判断是否存在 | `exact-key-lookup.md` | Repeated equality membership queries. |
| 数组频繁单点更新，同时查询区间和 | `range-query-update.md` | Dynamic range aggregation. |
| 当前路径数由前两个状态构成，相同状态被重复计算 | `dynamic-programming-recurrence.md` | Recurrence with overlapping subproblems. |
| 请求慢，但主要时间用于传输数 MB 图片 | `performance-validation.md` | Measure the I/O path before changing an in-memory algorithm. |

Minimal command:

```bash
rg -l "回收|游标|frontier" INDEX.md patterns
```

The result must include `INDEX.md` and `patterns/task-allocation-with-reclaims.md`.
