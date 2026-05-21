---
description: 编码实现阶段 - 调用 subagent-driven-development 技能，按照 plan.md 执行任务并更新 tasks.md
---

# STDD: 编码实现

## 目标

调用 subagent-driven-development 技能，根据 plan.md 文件，调用test-driven-development 执行任务（必须严格遵循TDD规范），完成后更新 tasks.md 标记已完成的任务。
注意：此阶段的输出内容应尽可能使用中文（专业术语或代码等除外）

## 前提

- 已完成 `/stdd-plan` 阶段
- plan.md 包含执行计划
- tasks.md 包含任务清单

## 执行步骤

### 0. 概念对齐，明确TDD规范内容
1. 写测试用例（引用尚不存在的类/方法），创建最小桩代码（空类、返回 null/default 的方法）→ 让测试能 **编译通过**
2. 运行测试 → 测试 **执行失败**（断言不通过）
3. 实现业务逻辑
4. 运行测试 → 测试通过 →  🟢 GREEN
5. 重构

### 1. 读取 plan.md

获取执行计划，并输出格式化清单

### 2. 按照subagent-driven-development方式 和 test-driven-development规范执行任务

必须严格按照/superpowers/subagent-driven-development方式执行任务
告诉所有子代理：每个任务的执行必须严格遵守TDD规范；如果子代理没有展示 RED→GREEN→REFACTOR 的过程，你不得接受提交；


### 3. 更新 tasks.md

任务执行完毕后，按照openspec规范同步更新tasks.md文件中任务进度


## 输出

告诉用户：
- 完成的任务数量
- 失败的任务（如有）
- 本次变更的单元测试覆盖率（如有）
- 下一步是 `/stdd-verify` 验证实现
