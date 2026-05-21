---
description: 查看当前工作流状态，检测执行阶段，支持从中断点继续执行
---

# STDD: 状态查看

## 目标

1. 查看当前工作流执行到哪个阶段
2. 异常中断后可从断点继续，不需要重复已完成的讨论

## 执行步骤

### 1. 检测当前阶段
**重要：** 每次操作必须重新检查 change 目录下实际的文件，不能未检查凭记忆回复
重新检查 change 目录下的文件，确定工作流阶段：

| 阶段 | 检测依据                                                               |
|------|--------------------------------------------------------------------|
| 未开始 | 不存在 brainstorm.md                                                  |
| stdd-explore | brainstorm.md 存在，有 Q&A 记录                                          |
| stdd-propose | proposal.md, <change name>/specs/spec.md, design.md, tasks.md 全部存在 |
| stdd-plan | plan.md 存在                                                         |
| stdd-apply | tasks.md 有已完成标记 `[x]`                                              |
| stdd-verify | 已运行 openspec verify                                                |
| stdd-archive | change 目录已在 archive 中                                              |

### 2. 显示状态

输出当前阶段信息：
```
当前阶段: stdd-propose (提案生成)

已完成:
- stdd-explore ✓ (需求探索)

待完成:
- stdd-plan
- stdd-apply
- stdd-verify
- stdd-archive
```

### 3. 恢复继续（如果有请求）

如果用户要求从断点继续：

**a) 读取 brainstorm.md 分析已完成的讨论**

识别：
- 已完成的问题（有 Q 有 A）
- 已问未答的问题（有 Q 无 A 或 A 不完整）
- 未讨论的新问题（从上下文推断）

**b) 从断点继续**

- 先处理已问未答的问题
- 再继续新问题的讨论
- 不重复已完成的问答

**c) 更新 brainstorm.md**

格式：
```markdown
## 需求讨论

### Q: [问题]
A: [回答]

### Q: [新问题]
<!-- 无答案，等待回答 -->
```

## 输出

- 当前阶段信息
- 可继续执行的提示
- 如需继续，询问用户是否要继续
