---
description: 需求探索阶段 - 触发 brainstorming 技能，详细讨论需求并记录 Q&A
---

# STDD: 需求探索

## 目标

通过 brainstorming 技能详细讨论需求，尽可能全面地询问本次需求中不明确的问题，Q&A 记录保存进 brainstorm.md。


## 执行步骤

### 1. 确认功能名称

根据`/stdd-explore`后面的输入的内容，自动生成本次openspec change的候选名称（英文，用于目录命名），让用户确认且支持用户自己输入
注意：
- 如果`/stdd-explore`后面的没有输入任何内容，主动提问让用户输入变更名称

### 2. 创建变更目录
```bash
openspec new change "<name>"
```
创建变更根目录，目录路径为 `openspec/changes/<name>/`

### 3. 创建brainstorm.md
检查项目目录下是否存在 `openspec/schemas/stdd/templates/brainstorm.md`，
- 如果存在，创建brainstorm.md并使用模板初始化文件
- 不存在，则创建新的空白brainstorm.md

### 4. 触发 brainstorming 技能

按 brainstorming 技能流程进行，尽可能详细的讨论，目标是要能根据头脑风暴的信息，支撑后续生成openspec规范中的proposal.md/spec.md/design.md/tasks.md这些文件
注意：
- 不确定的地方必须要询问得到明确的回复，不能想当然的瞎猜
- 只能提问需求相关的问题，提问完成后直接结束brainstorming，不要引导用户立即进入design或者其他阶段

### 5. 更新 brainstorm.md

将前面讨论的问题原始信息写入brainstrom.md

## 输出

告诉用户：
- brainstorm.md 已初始化
- 使用的模板来源（自定义/STDD 默认）
- 下一步是 `/stdd-propose` 生成 OpenSpec 文档
