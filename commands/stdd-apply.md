---
description: 编码实现阶段 - 触发 using-git-worktrees 创建隔离空间，触发 tdd 技能执行
---

# stdd: 编码实现

## 目标

在隔离的 git worktree 中执行任务，避免影响主空间代码。

## 前提

- 已完成 `/stdd-plan` 阶段
- plan.md 包含执行计划

## 执行步骤

1. **触发 /superpowers/using-git-worktrees 技能**：加载并使用 using-git-worktrees 技能
   - 在新的 worktree 中执行任务
   - 避免污染主空间的代码

2. **读取 plan.md**：获取执行计划

3. **触发 /superpowers/test-driven-development 技能**：加载并使用 test-driven-development 技能

4. **按顺序执行任务**：对于每个任务：
   - 标记任务开始
   - 编写测试用例
   - 运行测试（预期失败）
   - 编写实现代码
   - 运行测试（预期通过）
   - 重构（如需要）
   - 标记任务完成

5. **任务依赖处理**：

   **独立任务（无依赖）**：
   - 一个任务失败后，记录失败原因
   - 继续执行下一个独立任务
   - 不阻塞其他独立任务的执行

   **依赖任务（有依赖）**：
   - 如果前置任务失败，后置依赖任务自动标记为失败
   - 不再执行依赖该失败任务的后续任务
   - 记录失败原因和被阻塞的任务

6. **更新 tasks.md**：标记已完成/失败的任务

## 输出

- worktree 中的代码文件（实现代码）
- worktree 中的测试文件（测试用例）
- 更新的 tasks.md（标记完成/失败的任务）
- 告诉用户可以进入 `/stdd-verify` 阶段