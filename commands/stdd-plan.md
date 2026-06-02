---
description: 执行计划阶段 - 调用 writing-plans 技能，基于 tasks.md 生成执行计划 plan.md
---

# STDD: 执行计划

## 目标

调用 writing-plans 技能，基于 tasks.md 生成符合 Superpowers 规范的执行计划 plan.md，且所有任务尽量使用中文描述

## 前提

- 已完成 `/stdd-propose` 阶段
- tasks.md 包含原子任务清单
- proposal.md、spec.md、design.md 已生成

## 执行步骤
### 0. 概念对齐，明确TDD规范内容
1. 写测试用例（引用尚不存在的类/方法），创建最小桩代码（空类、返回 null/default 的方法）→ 让测试能 **编译通过**
2. 运行测试 → 测试 **执行失败**（断言不通过）
3. 实现业务逻辑
4. 运行测试 → 测试通过 →  🟢 GREEN
5. 重构

### 1. 调用 writing-plans 生成plan.md文件
根据task.md文件内容，参照模板`openspec/schemas/stdd/templates/plan.md`的格式，调用 /superpowers/writing-plans 技能, 
严格按照TDD规范生成任务执行计划并写入`openspec/changes/<name>/plan.md`文件
**注意：**必须确保所有任务都按照TDD规范步骤拆分 ，且所有任务尽量使用中文描述

### 2. 检查plan.md中是否按照TDD规范拆分执行计划
检查plan.md文件中是否所有任务都按照TDD规范拆分执行计划

### 3. 如有不符合TDD规范的执行计划则调整plan.md文件
如有不符合TDD规范的执行计划则调整plan.md文件，使得所有任务均满足TDD规范的执行步骤

## 输出

告诉用户：
- plan.md 已生成
- 下一步是 `/stdd-apply` 执行任务
