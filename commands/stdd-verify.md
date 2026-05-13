---
description: 审查验证阶段 - 调用 openspec verify 命令校验变更是否符合 OpenSpec 规范（无文件产出）
---

# STDD: 审查验证

## 目标

调用 openspec verify 命令校验变更是否符合 OpenSpec 规范。无文件产出。

## 前提

- 已完成 `/stdd-apply` 阶段
- 代码和测试已生成
- tasks.md 中所有任务标记为已完成

## 执行步骤

### 1. 运行 openspec verify

执行 `openspec verify <change-name>` 检查变更目录：

- 目录结构是否完整
- proposal.md 格式是否正确
- spec.md 是否符合规范
- design.md 是否符合规范
- tasks.md 格式是否正确（checkbox 格式）

### 2. 验证测试通过

确保测试全部通过：
- 运行测试命令
- 检查是否有测试失败

### 3. 验证覆盖率（可选）

如果有测试覆盖率工具，运行覆盖率检查。

### 4. 输出校验结果

向用户报告：
- 校验通过/失败
- 具体失败项（如有）
- 建议修复方案（如有）

## 输出

告诉用户：
- 校验结果（通过/失败）
- 失败项详情（如有）
- 下一步是 `/stdd-archive` 归档（如校验通过）
