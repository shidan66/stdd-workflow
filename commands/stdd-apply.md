---
description: 编码实现阶段 - 调用 subagent-driven-development 技能，按照 plan.md 执行任务并更新 tasks.md
---

# STDD: 编码实现

## 目标

调用 subagent-driven-development 技能，按照 plan.md 执行任务，完成后更新 tasks.md 标记已完成的任务。
注意：此阶段的输出内容应尽可能使用中文（专业术语或代码等除外）

## 前提

- 已完成 `/stdd-plan` 阶段
- plan.md 包含执行计划
- tasks.md 包含任务清单

## 执行步骤

### 1. 读取 plan.md

获取执行计划，分析任务依赖关系确定执行顺序，并按照顺序格式化输出清单

### 2. 按阶段执行任务

注意：
- 必须按照subagent-driven-development方式执行任务
- 对于每个任务，必须严格按照TDD规范执行，禁止先写生产代码
- 单元测试要尽可能完善

### 3. 更新 tasks.md

任务执行完毕后，按照openspec规范同步更新tasks.md文件中任务进度


## 输出

告诉用户：
- 完成的任务数量
- 失败的任务（如有）
- 下一步是 `/stdd-verify` 验证实现
