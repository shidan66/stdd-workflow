# STDD Workflow

整合 OpenSpec 与 Superpowers，构建适合中大型项目开发的端到端研发工作流。

## 安装

将以下指令复制到 OpenCode 中执行：

```
Fetch and follow instructions from https://github.com/shidan66/stdd-workflow/blob/main/INSTALL.md
```

## 工作流命令

| 命令 | 说明 | 产出 |
|------|------|------|
| `/stdd-status` | 状态查看 | - |
| `/stdd-explore` | 需求探索 | brainstorm.md |
| `/stdd-propose` | 提案生成 | proposal.md + spec.md + design.md + tasks.md |
| `/stdd-plan` | 执行计划 | plan.md |
| `/stdd-apply` | 编码实现 | 代码（更新 tasks.md） |
| `/stdd-verify` | 审查验证 | 校验结果（无文件产出） |
| `/stdd-archive` | 归档 | archive/ |

## 工作流阶段

```
stdd-explore → stdd-propose → stdd-plan → stdd-apply → stdd-verify → stdd-archive
```

| 阶段 | 说明 | 调用技能 |
|------|------|----------|
| **explore** | 需求探索，详细讨论 Q&A | brainstorming |
| **propose** | 生成 OpenSpec 文档 | - |
| **plan** | 生成执行计划 | writing-plans |
| **apply** | 按计划执行任务 | subagent-driven-development |
| **verify** | 校验是否符合规范 | openspec verify |
| **archive** | 归档变更 | openspec archive |

## 制品结构

```
openspec/changes/<feature>/
├── brainstorm.md       (explore 阶段 - Q&A 记录)
├── proposal.md        (propose 阶段 - 需求提案)
├── spec.md             (propose 阶段 - 需求规格)
├── design.md          (propose 阶段 - 技术设计)
├── tasks.md           (propose 阶段 - 任务清单)
├── plan.md            (plan 阶段 - 执行计划)
└── (verify 阶段 - 无文件产出，仅 OpenSpec verify 校验)
```

## 自定义模板

支持在项目目录下创建 `openspec/schemas/stdd/` 目录自定义各阶段的文件格式。

### 目录结构

```
项目目录/openspec/schemas/stdd/
├── schema.yaml
└── templates/              (可选)
    ├── brainstorm.md      (explore 阶段)
    ├── proposal.md        (propose 阶段)
    ├── spec.md           (propose 阶段)
    ├── design.md         (propose 阶段)
    ├── tasks.md          (propose 阶段)
    └── plan.md           (plan 阶段)
```

## 依赖

- **OpenSpec** - 规范框架
- **Superpowers** - 执行纪律（brainstorming、writing-plans、subagent-driven-development 等技能）
