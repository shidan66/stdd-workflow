---
description: 需求明确 - 触发 brainstorming 技能，分析需求文档和代码，产出 brainstorm.md 阶段1
---

# WF: 需求明确

## 目标

分析已有需求文档或代码，明确需求细节，填充 proposal.md 中的详细描述。

## 前提

- 已运行 `/wf:init` 创建 change 目录
- 当前工作目录在 change 目录下

## 执行步骤

1. **触发 brainstorming 技能**：加载并使用 brainstorming 技能

2. **收集现有材料**：
   - 读取 proposal.md（已有的一句话需求）
   - 查找是否有外部需求文档（ PRD、设计稿等）
   - 分析现有代码结构（如果项目已存在）

3. **需求分析**：通过对话方式明确以下内容：
   - 需求背景和目标
   - 功能详细描述
   - 用户场景
   - 边界条件
   - 不确定的地方主动提问

4. **填充 proposal.md**：将明确后的详细需求填充到 proposal.md 中

5. **更新 brainstorm.md**：在 "阶段1: 需求分析" 下记录问答过程

## 输出

- 更新的 proposal.md（包含详细需求描述）
- 更新的 brainstorm.md（包含阶段1的问答记录）
- 告诉用户可以进入 `/wf:design` 阶段