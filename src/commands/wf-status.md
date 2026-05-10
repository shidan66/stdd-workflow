---
description: 查看当前工作流状态，检测执行阶段，支持从中断点继续执行
---

# WF: 状态查看

## 目标

1. 查看当前工作流执行到哪个阶段
2. 异常中断后可从断点继续，不需要重复已完成的讨论

## 执行步骤

### 1. 检测当前阶段

检查 change 目录下的文件，确定工作流阶段：

| 阶段 | 检测依据 |
|------|----------|
| 未开始 | 不存在 proposal.md |
| wf:propose | proposal.md 有完整内容，brainstorm.md 阶段1有内容 |
| wf:spec | spec.md 存在，brainstorm.md 阶段2有内容 |
| wf:design | design.md 有内容，brainstorm.md 阶段3有内容 |
| wf:tasks | tasks.md 有内容 |
| wf:plan | plan.md 有内容 |
| wf:apply | tasks.md 有已完成标记 [x] |
| wf:verify | verify.md 存在 |
| wf:archive | change 目录已在 archive 中 |

### 2. 显示状态

输出当前阶段信息：
```
当前阶段: wf:spec (需求规范)

已完成:
- wf:propose ✓ (需求提案)

待完成:
- wf:design
- wf:tasks
- wf:plan
- wf:apply
- wf:verify
- wf:archive
```

### 3. 恢复继续（如果有请求）

如果用户要求从断点继续：

**a) 读取 brainstorm.md 分析已完成的讨论**

遍历 brainstorm.md 的三个阶段（需求提案、需求规范、需求设计），识别：
- 已完成的问题（有 Q 有 A）
- 已问未答的问题（有 Q 无 A 或 A 不完整）
- 未讨论的新问题（从上下文推断）

**b) 从断点继续**

- 先处理已问未答的问题
- 再继续新问题的讨论
- 不重复已完成的问答

**c) 更新 brainstorm.md**

- 每次讨论后立即更新文件
- 格式：
```markdown
## 阶段1: 需求提案

### Q: [问题]
A: [回答]

### Q: [新问题]
<!-- 无答案，等待回答 -->
```

## 输出

- 当前阶段信息
- 可继续执行的提示
- 如需继续，询问用户是否要继续