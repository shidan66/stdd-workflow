---
description: 任务拆分阶段 - 基于 proposal、design、brainstorm 进行原子任务拆分
---

# WF: 任务拆分

## 目标

将需求拆分为原子性的任务清单。

## 前提

- 已完成 `/wf:design` 阶段
- proposal.md 包含详细需求
- design.md 包含技术方案
- brainstorm.md 包含完整问答记录

## 执行步骤

1. **读取已有材料**：
   - 读取 proposal.md
   - 读取 design.md
   - 读取 brainstorm.md

2. **任务拆分**：基于上述材料，拆分任务，原则：
   - **原子性**：每个任务可独立完成
   - **独立性**：任务间无依赖或依赖清晰
   - **自我闭环**：每个任务有明确的输入和输出

3. **写入 tasks.md**：将任务清单写入 tasks.md，格式：
```markdown
# Tasks

- [ ] Task 1: 任务描述
- [ ] Task 2: 任务描述
- [ ] Task 3: 任务描述
```

## 输出

- tasks.md（原子任务清单）
- 告诉用户可以进入 `/wf:plan` 阶段