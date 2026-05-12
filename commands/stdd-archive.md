---
description: 归档阶段 - 调用 openspec archive 命令归档变更
---

# STDD: 归档

## 目标

调用 openspec archive 命令将变更归档到 OpenSpec archive。

## 前提

- 已完成 `/stdd-verify` 阶段
- openspec verify 校验通过

## 执行步骤

### 1. 确认归档

询问用户确认是否归档。

### 2. 运行 openspec archive

执行 `openspec archive <change-name>`：
- 将 specs/ 中的增量 spec 合并到 openspec/specs/
- 将整个 change 目录移动到 openspec/changes/archive/YYYY-MM-DD-<feature>/

### 3. 确认归档结果

- 归档路径
- 合并的 spec 数量

## 输出

告诉用户：
- 归档完成的提示
- archive 路径
- 合并的 spec 数量
