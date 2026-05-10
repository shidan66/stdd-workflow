---
description: 设计阶段 - 触发 brainstorming 技能，基于 proposal 和 brainstorm 阶段1 进行方案设计
---

# WF: 设计

## 目标

基于已明确的需求，进行技术方案设计。

## 前提

- 已完成 `/wf:clarify` 阶段
- proposal.md 包含详细需求
- brainstorm.md 包含阶段1的问答记录

## 执行步骤

1. **触发 brainstorming 技能**：加载并使用 brainstorming 技能

2. **读取已有材料**：
   - 读取 proposal.md（详细需求）
   - 读取 brainstorm.md（阶段1的问答记录）
   - 分析现有代码库结构

3. **方案设计**：设计以下内容：
   - 架构设计（模块划分、接口设计）
   - 数据结构设计
   - API 设计（如有需要）
   - 数据库 schema（如有需要）
   - 多种方案需要确认时主动提问

4. **更新 brainstorm.md**：在 "阶段2: 设计确认" 下记录设计过程中的问答

5. **写入 design.md**：将完整的设计方案写入 design.md，包含：
   - 设计目标
   - 技术选型及理由
   - 架构图或结构说明
   - 核心接口/模块设计
   - 数据模型
   - 待确认问题（如有）

## 输出

- design.md（完整设计方案）
- brainstorm.md（包含阶段2的问答记录）
- 告诉用户可以进入 `/wf:split` 阶段