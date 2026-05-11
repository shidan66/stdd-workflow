---
description: 设计阶段 - 触发 brainstorming 技能，基于 proposal 和 spec.md 进行方案设计
---

# STDD: 需求设计

## 目标

基于已明确的需求规格，进行技术方案设计。

## 前提

- 已完成 `/stdd-spec` 阶段
- proposal.md 包含完整提案
- spec.md 包含需求规格
- brainstorm.md 包含阶段2的问答记录

## 执行步骤

1. **读取已有材料**：
   - 读取 proposal.md（需求提案）
   - 读取 spec.md（需求规格）
   - 分析现有代码库结构

2. **检查自定义模板**：检查项目目录下是否存在 `openspec/schemas/stdd/templates/design.md`
   - 如果存在，加载自定义模板
   - 如果不存在，使用 OpenSpec 默认模板

3. **触发 /superpowers/brainstorming 技能**：加载并使用 brainstorming 技能

4. **设计方案讨论（阶段3）**：
   - 架构设计（模块划分、接口设计）
   - 数据结构设计
   - API 设计（如有需要）
   - 数据库 schema（如有需要）
   - 多种方案需要确认时主动提问

5. **生成 design.md**：优先按照模板填充，如果没有模板，默认按照下面内容填充：
   - 设计目标
   - 技术选型及理由
   - 架构图或结构说明
   - 核心接口/模块设计
   - 数据模型
   - 待确认问题（如有）

6. **更新 brainstorm.md**：在 "阶段3: 需求设计" 下记录问答过程

## 输出

- design.md（完整设计方案）
- 更新的 brainstorm.md（包含阶段3的问答记录）
- 使用的模板来源
- 告诉用户可以进入 `/stdd-tasks` 阶段