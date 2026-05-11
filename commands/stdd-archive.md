---
description: 归档阶段 - 关联 OpenSpec archive，合并 spec 并归档全部制品
---

# STDD: 归档

## 目标

将变更归档到 OpenSpec archive，合并 spec 到主目录。

## 前提

- 已完成 `/stdd:verify` 阶段
- 所有验证通过

## 执行步骤

1. **确认归档**：询问用户确认是否归档

2. **运行 OpenSpec archive**：执行 `openspec archive <change-name>`

3. **确认 spec 合并**：OpenSpec 会自动：
   - 将 changes/<feature>/specs/ 中的增量 spec 合并到 openspec/specs/
   - 将整个 change 目录移动到 openspec/changes/archive/YYYY-MM-DD-<feature>/

4. **确认 brainstorm.md 归档**：检查 archive 目录中是否包含 brainstorm.md（整个 change 目录会被完整移动）

## 输出

- 归档完成的提示
- archive 路径
- 合并的 spec 数量