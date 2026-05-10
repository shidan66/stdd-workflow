# STDD Workflow

整合 OpenSpec 与 Superpowers，构建适合中大型项目开发的端到端研发工作流。

## 安装

将以下指令复制到 OpenCode 中执行：

```
请帮我安装 STDD Workflow 工作流包：

1. 检查 OpenSpec 是否已安装（运行 openspec --version），如果没有则安装：npm install -g @fission-ai/openspec@latest

2. 检查 OpenCode 配置（~/.config/opencode/opencode.json）中是否已配置 Superpowers，如果没有则按照官方文档安装：
   Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md

3. 复制 src/commands/ 目录下的所有 .md 文件到 .opencode/commands/ 目录

完成后告诉我安装结果。
```

## 工作流命令

| 命令 | 说明 | 产出 |
|------|------|------|
| `/stdd:status` | 状态查看 | - |
| `/stdd:propose` | 提案初始化 | proposal.md |
| `/stdd:spec` | 需求规范 | spec.md |
| `/stdd:design` | 需求设计 | design.md |
| `/stdd:tasks` | 任务拆分 | tasks.md |
| `/stdd:plan` | 执行计划 | plan.md |
| `/stdd:apply` | 编码实现 | 代码 |
| `/stdd:verify` | 审查验证 | verify.md |
| `/stdd:archive` | 归档 | archive/ |

## 工作流阶段

```
stdd:propose → stdd:spec → stdd:design → stdd:tasks → stdd:plan → stdd:apply → stdd:verify → stdd:archive
```

## 制品结构

```
openspec/changes/<feature>/
├── proposal.md           (需求提案，符合 OpenSpec 规范)
├── specs/
│   └── <capability>/
│       └── spec.md       (需求规格，delta spec)
├── brainstorm.md        (问答记录，3个阶段)
│   ├── 阶段1: 需求提案
│   ├── 阶段2: 需求规范
│   └── 阶段3: 需求设计
├── design.md             (设计方案)
├── tasks.md             (原子任务清单)
├── plan.md              (执行计划)
└── verify.md            (验证报告)
```

## 自定义模板

支持在项目目录下创建 `stdd-templates/` 目录自定义各阶段的文件格式。

### 目录结构

```
项目目录/
└── stdd-templates/          (可选)
    ├── proposal.md          (可选)
    ├── spec.md             (可选)
    ├── design.md           (可选)
    ├── tasks.md            (可选)
    ├── brainstorm.md       (可选)
    ├── plan.md             (可选)
    └── verify.md           (可选)
```

### 优先级规则

| 文件 | 优先级 |
|------|--------|
| proposal.md | 项目模板 > OpenSpec 默认 |
| spec.md | 项目模板 > OpenSpec 默认 |
| design.md | 项目模板 > OpenSpec 默认 |
| tasks.md | 项目模板 > OpenSpec 默认 |
| brainstorm.md | 项目模板 > STDD 默认 |
| plan.md | 项目模板 > STDD 默认 |
| verify.md | 项目模板 > STDD 默认 |

如果项目目录下没有对应的模板文件，则使用默认格式生成。

## 依赖

- **OpenSpec** - 规范框架
- **Superpowers** - 执行纪律（TDD、调试、审查等技能）

## 文档