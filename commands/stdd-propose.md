---
description: 提案生成阶段 - 基于 brainstorm.md 和用户输入生成 OpenSpec 文档（proposal.md + spec.md + design.md + tasks.md）
---

# STDD: 提案生成

## 目标

基于 brainstorm.md 和用户输入，一次性生成符合 OpenSpec 规范的 4 个文档：
- proposal.md（需求提案）
- spec.md（需求规格）
- design.md（技术设计）
- tasks.md（任务清单）
注意：此阶段的输出内容应尽可能使用中文（专业术语或代码等除外）

## 前提

- 已完成 `/stdd-explore` 阶段
- brainstorm.md 包含完整的 Q&A 记录
- 用户在命令后提供了功能名称和关键信息

## 执行步骤

### 1. 确认功能名称

根据前面brainstorm阶段的信息，或者当前阶段的输入信息，自动生成本次openspec change的候选名称（英文，用于目录命名），让用户确认且支持用户自己输入。


### 2. 检查自定义模板

依次检查项目目录下是否存在对应的自定义模板：

- `openspec/schemas/stdd/templates/proposal.md`
- `openspec/schemas/stdd/templates/spec.md`
- `openspec/schemas/stdd/templates/design.md`
- `openspec/schemas/stdd/templates/tasks.md`

如果存在，加载自定义模板；否则使用 OpenSpec 默认模板。

### 3. 生成 proposal.md

基于 brainstorm.md 中的讨论，按proposal.md模板生成符合openspec规范的proposal.md文件

### 4. 生成 spec.md
基于前面已有的信息，按spec.md模板生成符合openspec规范的spec.md文件
- 特别注意：spec.md文件的路径要符合openspec规范

### 5. 生成 design.md
基于前面已有的信息，按design.md模板生成符合openspec规范的design.md文件

### 6. 生成 tasks.md

基于前面已有的信息，按tasks.md模板生成符合openspec规范的tasks.md文件


## 输出

告诉用户：
- change 目录路径
- 生成的 4 个文档
- 使用的模板来源（自定义/默认）
- 下一步是 `/stdd-plan` 生成执行计划
