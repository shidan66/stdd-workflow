---
description: 提案初始化 - 生成符合 OpenSpec 规范的 proposal.md，触发 brainstorming 明确需求提案
---

# STDD: 提案初始化

## 目标

创建 OpenSpec change 目录，生成完整的 proposal.md。

## 执行步骤

1. **获取功能名称**：询问用户想要创建的功能名称（英文，用于目录命名）

2. **调用 OpenSpec**：运行 `openspec new <feature-name>` 创建 change 目录

3. **检查自定义模板**：检查项目目录下是否存在 `stdd-templates/proposal.md`
   - 如果存在，加载自定义模板
   - 如果不存在，使用 OpenSpec 默认模板

4. **触发 brainstorming 技能**：加载并使用 brainstorming 技能

5. **需求提案讨论（阶段1）**：
   - 询问用户需求背景（为什么做）
   - 询问具体改变（做什么）
   - 确认涉及的功能模块（Capabilities）
   - 确认影响范围（Impact）

6. **生成 proposal.md**：按照模板填充内容

   **OpenSpec 默认模板**：
   ```markdown
   ## Why
   <!-- 动机 -->

   ## What Changes
   <!-- 具体改变 -->

   ## Capabilities
   ### New Capabilities
   - <name>: <描述>

   ### Modified Capabilities
   - <existing-name>: <变更>

   ## Impact
   <!-- 影响范围 -->
   ```

7. **检查自定义模板**：检查项目目录下是否存在 `stdd-templates/brainstorm.md`
   - 如果存在，加载自定义模板
   - 如果不存在，使用 STDD 默认模板

8. **创建 brainstorm.md**（默认模板）：
   ```markdown
   # Brainstorm 记录

   ## 阶段1: 需求提案
   <!-- 问答记录 -->

   ## 阶段2: 需求规范

   ## 阶段3: 需求设计
   ```

9. **创建空的 specs 目录**：为后续 spec.md 准备

10. **创建空的 design.md**（检查 stdd-templates/design.md 是否存在）

11. **创建空的 tasks.md**（检查 stdd-templates/tasks.md 是否存在）

12. **创建空的 plan.md**

## 输出

告诉用户：
- 创建的 change 目录路径
- proposal.md 已生成完整内容
- 使用的模板来源（自定义/OpenSpec 默认）
- 下一步是 `/stdd:spec` 进行需求规范明确