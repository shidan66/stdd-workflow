---
description: 审查验证阶段 - 触发 verification 技能，执行 OpenSpec verify + TDD 验证 + 覆盖率检查
---

# STDD: 审查验证

## 目标

验证实现是否满足需求，测试是否通过。

## 前提

- 已完成 `/stdd:apply` 阶段
- 代码和测试已生成

## 执行步骤

1. **触发 verification-before-completion 技能**：加载并使用 verification-before-completion 技能

2. **OpenSpec 验证**：运行 `openspec verify` 检查：
   - 变更目录结构是否完整
   - proposal.md 格式是否正确
   - specs 目录是否合规（如果有）

3. **TDD 验证**：检查测试是否：
   - 测试全部通过
   - 测试覆盖了主要功能点

4. **覆盖率检查**：运行测试覆盖率工具（如有），报告覆盖率

5. **生成验证报告**：写入 verify.md：
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
- 告诉用户可以进入 `/stdd:archive` 阶段