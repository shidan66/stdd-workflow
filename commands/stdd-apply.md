---
description: 编码实现阶段 - 调用 subagent-driven-development 技能，按照 plan.md 执行任务并更新 tasks.md
---

# STDD: 编码实现

## 目标

调用 subagent-driven-development 技能，按照 plan.md 执行任务，完成后更新 tasks.md 标记已完成的任务。

## 前提

- 已完成 `/stdd-plan` 阶段
- plan.md 包含执行计划
- tasks.md 包含任务清单

## 执行步骤

### 1. 加载 subagent-driven-development 技能

调用 subagent-driven-development 技能获取执行规范。

### 2. 读取 plan.md

获取执行计划，包括：
- 任务依赖图
- 执行顺序（阶段划分）
- 每个任务的具体步骤

### 3. 按阶段执行任务

对于每个任务：

**a) 标记任务开始**
- 在 tasks.md 中找到对应任务
- 将 `- [ ]` 改为 `- [/]`（进行中）

**b) 按照 plan.md 执行**
- 写测试用例
- 运行测试（预期失败）
- 写实现代码
- 运行测试（预期通过）
- 重构（如需要）

**c) 标记任务完成**
- 将 `- [/]` 改为 `- [x]`（已完成）
- 记录任何需要关注的问题

### 4. 处理任务依赖

**独立任务（无依赖）**：
- 一个任务失败后，记录失败原因
- 继续执行下一个独立任务
- 不阻塞其他独立任务

**依赖任务（有依赖）**：
- 如果前置任务失败，后置依赖任务自动标记失败
- 不再执行依赖该失败任务的后续任务
- 记录失败原因和被阻塞的任务

### 5. 更新 tasks.md

实时更新任务状态：
```markdown
## 1. Setup

- [x] 1.1 Create new module structure
- [x] 1.2 Add dependencies to package.json

## 2. Core Implementation

- [/] 2.1 Implement data export function
- [ ] 2.2 Add CSV formatting utilities
```

## 输出

告诉用户：
- 完成的任务数量
- 失败的任务（如有）
- 下一步是 `/stdd-verify` 验证实现
