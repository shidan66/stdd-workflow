---
description: 执行计划阶段 - 调用 writing-plans 技能，基于 tasks.md 生成执行计划 plan.md
---

# STDD: 执行计划

## 目标

调用 writing-plans 技能，基于 tasks.md 生成符合 Superpowers 规范的执行计划 plan.md。

## 前提

- 已完成 `/stdd-propose` 阶段
- tasks.md 包含原子任务清单
- proposal.md、spec.md、design.md 已生成

## 执行步骤

### 1. 调用 writing-plans 生成plan.md文件
根据task.md文件内容，调用 /superpowers/writing-plans 技能, 生成任务执行计划并写入plan.md文件


## 输出

告诉用户：
- plan.md 已生成
- 下一步是 `/stdd-apply` 执行任务
