---
description: 任务拆分阶段 - 基于 proposal、design、brainstorm 进行原子任务拆分
---

# STDD: 任务拆分

## 目标

将需求拆分为原子性的任务清单。

## 前提

- 已完成 `/stdd:design` 阶段
- proposal.md 包含详细需求
- design.md 包含技术方案
- brainstorm.md 包含完整问答记录

## 执行步骤

1. **读取已有材料**：
   - 读取 proposal.md
   - 读取 design.md
   - 读取 brainstorm.md

2. **检查自定义模板**：检查项目目录下是否存在 `stdd-templates/tasks.md`
   - 如果存在，加载自定义模板
   - 如果不存在，使用 OpenSpec 默认模板

3. **任务拆分**：基于上述材料，拆分任务，原则：
   - **原子性**：每个任务可独立完成
   - **独立性**：任务间无依赖或依赖清晰
   - **自我闭环**：每个任务有明确的输入和输出

4. **写入 tasks.md**：按照模板填充内容

   **OpenSpec 默认模板**：
   ```markdown
   ## 1. <!-- Task Group Name -->

   - [ ] 1.1 <!-- Task description -->
   - [ ] 1.2 <!-- Task description -->

   ## 2. <!-- Task Group Name -->

   - [ ] 2.1 <!-- Task description -->
   - [ ] 2.2 <!-- Task description -->
   ```

## 输出

- tasks.md（原子任务清单）
- 使用的模板来源
- 告诉用户可以进入 `/stdd:plan` 阶段