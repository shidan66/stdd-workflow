---
description: 需求规范 - 触发 brainstorming 技能，明确需求规格，生成 spec.md
---

# WF: 需求规范

## 目标

基于已明确的 proposal.md，将需求细化为正式的规格说明 spec.md。

## 前提

- 已完成 `/wf:init` 阶段
- proposal.md 包含完整的提案内容

## 执行步骤

1. **读取已有材料**：读取 proposal.md，理解需求提案内容

2. **触发 brainstorming 技能**：加载并使用 brainstorming 技能

3. **需求规范讨论（阶段2）**：
   - 针对每个 Capability 细化需求
   - 明确具体的功能需求（Requirements）
   - 描述用户场景（Scenarios）
   - 确定边界条件
   - 不确定处主动提问

4. **生成 spec.md**：在 specs/<capability>/spec.md 中按照 OpenSpec 规范填充：
```markdown
## ADDED Requirements

### Requirement: <需求名称>
<需求描述>

#### Scenario: <场景名>
- **WHEN** <条件>
- **THEN** <预期结果>

#### Scenario: <场景名>
- **WHEN** <条件>
- **THEN** <预期结果>
```

5. **更新 brainstorm.md**：在 "阶段2: 需求规范" 下记录问答过程

## 输出

- specs/<capability>/spec.md（需求规格）
- 更新的 brainstorm.md（包含阶段2的问答记录）
- 告诉用户可以进入 `/wf:design` 阶段