---
description: 需求探索阶段 - 触发 brainstorming 技能，详细讨论需求并记录 Q&A
---

# STDD: 需求探索

## 目标

通过 brainstorming 技能详细讨论需求，尽可能全面地询问不明确的问题，Q&A 记录保存进 brainstorm.md。

## 执行步骤

### 1. 获取功能名称

询问用户想要创建的功能名称（英文，用于目录命名）。

### 2. 创建 change 目录

运行 `openspec new change <feature-name>` 创建 change 目录。

### 3. 检查自定义模板

检查项目目录下是否存在 `openspec/schemas/stdd/templates/brainstorm.md`：
- 如果存在，加载自定义模板
- 如果不存在，使用 STDD 默认模板

### 4. 创建 brainstorm.md

使用模板初始化文件，默认模板：
```markdown
# Brainstorm 记录

## 需求讨论
<!-- Q&A 记录 -->

## 待确认问题
<!-- 待回答的问题 -->
```

### 5. 触发 brainstorming 技能

加载并使用 brainstorming 技能进行需求讨论。

### 6. 需求讨论

按 brainstorming 技能流程进行：
- **理解想法**：询问需求背景、目标、约束
- **探索方案**：提出 2-3 种方案并讨论利弊
- **逐步验证**：分节呈现设计，确认每部分

### 7. 更新 brainstorm.md

讨论过程中实时记录 Q&A：
```markdown
### Q: [问题]
A: [回答]

### Q: [问题]
<!-- 待回答 -->
```

## 输出

告诉用户：
- 创建的 change 目录路径
- brainstorm.md 已初始化
- 使用的模板来源（自定义/STDD 默认）
- 下一步是 `/stdd-propose` 生成 OpenSpec 文档
