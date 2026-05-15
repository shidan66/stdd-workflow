---
description: 需求探索阶段 - 触发 brainstorming 技能，详细讨论需求并记录 Q&A
---

# STDD: 需求探索

## 目标

通过 brainstorming 技能详细讨论需求，尽可能全面地询问本次需求中不明确的问题，Q&A 记录保存进 brainstorm.md。


## 执行步骤

### 1. 创建 brainstorm.md

检查项目目录下是否存在 `openspec/schemas/stdd/templates/brainstorm.md`，
- 如果存在，创建brainstorm.md并使用模板初始化文件
- 不存在，则创建新的空白brainstorm.md

### 2. 触发 brainstorming 技能

加载并使用 /superpowers/brainstorming 技能进行需求讨论。

### 3. 需求讨论

按 brainstorming 技能流程进行，尽可能详细的讨论，目标是要能根据头脑风暴的信息，支撑后续生成openspec规范中的proposal.md/spec.md/design.md/tasks.md这些文件
注意：不确定的地方必须要询问得到明确的回复，不能想当然的瞎猜

### 4. 更新 brainstorm.md

讨论过程中实时原样记录 Q&A：
```markdown
### Q: [问题]
A: [回答]

### Q: [问题]
<!-- 待回答 -->
```

## 输出

告诉用户：
- brainstorm.md 已初始化
- 使用的模板来源（自定义/STDD 默认）
- 下一步是 `/stdd-propose` 生成 OpenSpec 文档
