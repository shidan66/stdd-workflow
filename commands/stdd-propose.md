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

## 前提

- 已完成 `/stdd-explore` 阶段
- brainstorm.md 包含完整的 Q&A 记录
- 用户在命令后提供了功能名称和关键信息

## 执行步骤

### 1. 获取功能名称

确认用户输入的功能名称（英文，用于目录命名）。

### 2. 读取已有材料

- 读取 brainstorm.md（需求讨论记录）
- 分析 Q&A 中已明确的需求
- 识别待确认但可以推断的部分

### 3. 检查自定义模板

依次检查项目目录下是否存在对应的自定义模板：

- `openspec/schemas/stdd/templates/proposal.md`
- `openspec/schemas/stdd/templates/spec.md`
- `openspec/schemas/stdd/templates/design.md`
- `openspec/schemas/stdd/templates/tasks.md`

如果存在，加载自定义模板；否则使用 OpenSpec/STDD 默认模板。

### 4. 生成 proposal.md

基于 brainstorm.md 中的讨论，提取：
- **Why**：解决的问题或机会
- **What Changes**：具体变更内容
- **Capabilities**：涉及的功能模块
- **Impact**：影响范围

### 5. 生成 spec.md

基于 brainstorm.md 中的详细讨论，生成完整的需求规格：
- **ADDED Requirements**：新增需求（每条 requirement 包含完整描述和 scenarios）
- **MODIFIED Requirements**：变更需求（如有）
- **REMOVED Requirements**：移除需求（如有）

格式要求：
- 每个 scenario 使用 `####` 标题（4 个井号）
- 使用 WHEN/THEN 格式描述场景
- SHALL/MUST 描述规范性要求

### 6. 生成 design.md

基于 brainstorm.md 中的设计讨论，生成技术方案：
- **Context**：背景和约束
- **Decisions**：技术选型及理由（备选方案对比）
- **数据模型**：相关数据模型
- **业务流程**：核心业务流程（如有）
- **Risks / Trade-offs**：已知风险
- **Migration Plan**：迁移计划（如适用）

### 7. 生成 tasks.md

基于 proposal.md、spec.md、design.md，拆分任务清单：
- 任务必须使用 `- [ ]` checkbox 格式
- 相关任务归入带编号的 `##` 分组
- 每个任务原子化，可独立完成
- 按依赖顺序排列

### 8. 更新 brainstorm.md

在 brainstorm.md 末尾标注文档生成状态：
```markdown
## 文档生成状态

- [x] proposal.md - 已生成
- [x] spec.md - 已生成
- [x] design.md - 已生成
- [x] tasks.md - 已生成
```

## 输出

告诉用户：
- change 目录路径
- 生成的 4 个文档
- 使用的模板来源（自定义/默认）
- 下一步是 `/stdd-plan` 生成执行计划
