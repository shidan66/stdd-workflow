---
description: 提案初始化 - 创建空的 proposal.md 文件，只包含一句话需求描述
---

# WF: 提案初始化

## 目标

创建 OpenSpec change 目录和空的 proposal.md 文件。

## 执行步骤

1. **获取功能名称**：询问用户想要创建的功能名称（英文，用于目录命名）

2. **调用 OpenSpec**：运行 `openspec new <feature-name>` 创建 change 目录

3. **清空内容**：将 proposal.md 内容简化，只保留一句话需求标题，其他内容留空等待 `/wf:clarify` 阶段填充

4. **创建 brainstorm.md**：在 change 目录下创建空的 brainstorm.md 文件，结构如下：

```markdown
# Brainstorm 记录

## 阶段1: 需求分析

## 阶段2: 设计确认
```

5. **创建空的 design.md**：创建空的 design.md 文件

6. **创建空的 tasks.md**：创建空的 tasks.md 文件

7. **创建空的 plan.md**：创建空的 plan.md 文件

## 输出

告诉用户：
- 创建的 change 目录路径
- 下一步是 `/wf:clarify` 进行需求明确