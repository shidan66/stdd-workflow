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
从 proposal.md 的 Capabilities 中提取所有 capability 名称并分别生成对应文件：
- **New Capabilities** 中的每一项，创建 specs/<capability-name>/spec.md，内容使用 ## ADDED Requirements
- **Modified Capabilities** 中的每一项，创建 specs/<capability-name>/spec.md，内容使用 ## MODIFIED Requirements
- **Removed Capabilities** 中的每一项（如有），创建 specs/<capability-name>/spec.md，内容使用 ## REMOVED Requirements
注意：文件必须放在 specs/ 子目录下，不是 change 根目录。 capability-name 使用 kebab-case 格式（如test-capability-name）。
路径示例： openspec/changes/<change-name>/specs/test-capability-name/spec.md
基于 brainstorm.md 中的详细讨论，生成完整的需求规格，优先按照加载的模板中的格式填充对应内容。
如无模板，按如下格式：
- **ADDED Requirements**：新增需求（每条 requirement 包含完整描述和 scenarios）
- **MODIFIED Requirements**：变更需求（如有）
- **REMOVED Requirements**：移除需求（如有）

格式要求：
- 每个 scenario 使用 `####` 标题（4 个井号）
- 使用 WHEN/THEN 格式描述场景
- 正文和标题都要使用 SHALL/MUST 描述规范性要求

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
