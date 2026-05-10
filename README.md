# WF Workflow

整合 OpenSpec 与 Superpowers，构建适合中大型项目开发的端到端研发工作流。

## 安装

将以下指令复制到 OpenCode 中执行：

```
请帮我安装 WF Workflow 工作流包：

1. 检查 OpenSpec 是否已安装（运行 openspec --version），如果没有则安装：npm install -g @fission-ai/openspec@latest

2. 检查 OpenCode 配置（~/.config/opencode/opencode.json）中是否已配置 Superpowers，如果没有则按照官方文档安装：
   Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md

3. 复制 src/commands/ 目录下的所有 .md 文件到 .opencode/commands/ 目录

完成后告诉我安装结果。
```

## 工作流命令

| 命令 | 说明 |
|------|------|
| `/wf:init` | 提案初始化 - 创建空的 proposal.md |
| `/wf:clarify` | 需求明确 - 触发 brainstorming 技能 |
| `/wf:design` | 设计 - 触发 brainstorming 技能 |
| `/wf:split` | 任务拆分 - 产出 tasks.md |
| `/wf:plan` | 执行计划 - 触发 writing-plans 技能 |
| `/wf:apply` | 编码实现 - 触发 tdd 技能 |
| `/wf:verify` | 审查验证 - 触发 verification 技能 |
| `/wf:archive` | 归档 - 关联 OpenSpec archive |

## 工作流阶段

```
wf:init → wf:clarify → wf:design → wf:split → wf:plan → wf:apply → wf:verify → wf:archive
```

## 制品结构

```
openspec/changes/<feature>/
├── proposal.md      (需求提案)
├── brainstorm.md   (问答记录，按阶段分类)
├── design.md        (设计方案)
├── tasks.md         (原子任务清单)
└── plan.md          (执行计划)
```

## 依赖

- **OpenSpec** - 规范框架
- **Superpowers** - 执行纪律（TDD、调试、审查等技能）

## 文档

- [设计文档](./docs/design.md) - 完整的设计方案