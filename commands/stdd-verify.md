---
description: 审查验证阶段 - 触发 verification 技能，执行 OpenSpec verify + TDD 验证 + 覆盖率检查
---

# STDD: 审查验证

## 目标

验证实现是否满足需求，测试是否通过。

## 前提

- 已完成 `/stdd-apply` 阶段
- 代码和测试已生成

## 执行步骤

1. **检查自定义模板**：检查项目目录下是否存在 `openspec/schemas/stdd/templates/verify.md`
   - 如果存在，加载自定义模板
   - 如果不存在，使用 STDD 默认模板

2. **触发 verification-before-completion 技能**：加载并使用 verification-before-completion 技能

3. **OpenSpec 验证**：运行 `openspec verify` 检查：
   - 变更目录结构是否完整
   - proposal.md 格式是否正确
   - specs 目录是否合规（如果有）

4. **TDD 验证**：检查测试是否：
   - 测试全部通过
   - 测试覆盖了主要功能点

5. **覆盖率检查**：运行测试覆盖率工具（如有），报告覆盖率

6. **生成验证报告**：按照模板填充内容

   **STDD 默认模板**：
   ```markdown
   # 验证报告

   ## OpenSpec 验证
   - [ ] 目录结构完整
   - [ ] proposal.md 格式正确
   - [ ] specs 目录合规

   ## TDD 验证
   - [ ] 所有测试通过
   - [ ] 测试覆盖主要功能

   ## 覆盖率
   - 测试覆盖率: XX%
   ```

## 输出

- verify.md（验证报告）
- 使用的模板来源
- 告诉用户可以进入 `/stdd-archive` 阶段