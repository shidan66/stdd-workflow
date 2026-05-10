# WF 工作流整合设计方案

## 概述

整合 OpenSpec 与 Superpowers，构建适合中大型项目开发的端到端研发工作流。

**核心理念**：
- OpenSpec 承载"规范框架"（提案、设计、任务、归档）
- Superpowers 承载"执行纪律"（TDD、调试、审查）
- 两者通过 OpenCode 的 slash 命令和技能触发机制无缝衔接

---

## 工作流阶段与命令

```
[提案初始化] → /wf:init → proposal.md (一句话)
      ↓
[需求明确]   → /wf:clarify → brainstorm.md (阶段1) + 填充 proposal.md
      ↓
[设计]       → /wf:design → design.md + brainstorm.md (阶段2)
      ↓
[任务拆分]   → /wf:split → tasks.md
      ↓
[执行计划]   → /wf:plan → plan.md
      ↓
[编码实现]   → /wf:apply → 代码 + 测试
      ↓
[审查验证]   → /wf:verify → 验证报告
      ↓
[归档]       → /wf:archive → archive/ (合并 spec + 保留全部制品)
```

---

## 命令详解

### /wf:init

- **作用**：提案初始化
- **产出**：`openspec/changes/<feature>/proposal.md`
- **内容**：仅一句话需求，其他留空等待 clarify 阶段填充
- **触发技能**：无
- **关联 OpenSpec 命令**：`/opsx:new` (openspec new)

### /wf:clarify

- **作用**：需求明确
- **产出**：`brainstorm.md` (阶段1: 需求分析)
- **额外**：填充 proposal.md 中的详细需求描述
- **触发技能**：brainstorming
- **执行内容**：
  - 分析已有需求文档/代码
  - 不确定处主动提问
  - 产出问答记录

### /wf:design

- **作用**：设计方案
- **产出**：`design.md` + `brainstorm.md` (阶段2: 设计确认)
- **触发技能**：brainstorming
- **执行内容**：
  - 基于 proposal + brainstorm(阶段1) 进行方案设计
  - 多种方案需要确认时主动提问

### /wf:split

- **作用**：任务拆分
- **产出**：`tasks.md` (原子任务清单)
- **触发技能**：无
- **拆分原则**：原子性、独立性、自我闭环

### /wf:plan

- **作用**：执行计划
- **产出**：`plan.md`
- **触发技能**：writing-plans
- **执行内容**：
  - 分析 tasks.md
  - 整理执行顺序、依赖关系、串并行
  - 每个任务按 TDD 规范落地

### /wf:apply

- **作用**：编码实现
- **产出**：代码文件 + 测试用例
- **触发技能**：test-driven-development
- **执行方式**：按 plan 顺序连续执行
- **每个任务执行流程**：写测试 → 写实现 → 重构

### /wf:verify

- **作用**：审查验证
- **产出**：验证报告
- **触发技能**：verification-before-completion
- **验证内容**：
  - 关联 OpenSpec verify：验证文件格式完整性
  - TDD 验证：测试是否通过
  - 覆盖率：检查测试覆盖率

### /wf:archive

- **作用**：归档
- **产出**：`openspec/changes/archive/YYYY-MM-DD-<feature>/`
- **关联**：OpenSpec archive
- **执行内容**：
  - 将增量 spec 合并到主 spec 目录
  - 移动整个 change 目录到 archive
  - **保留制品**：proposal + design + tasks + plan + brainstorm

---

## 制品结构

```
openspec/changes/<feature>/
├── proposal.md      (需求提案，含详细描述)
├── brainstorm.md   (问答记录，按阶段分类)
│   ├── 阶段1: 需求分析
│   └── 阶段2: 设计确认
├── design.md        (设计方案)
├── tasks.md         (原子任务清单)
└── plan.md          (执行计划)

openspec/changes/archive/YYYY-MM-DD-<feature>/
    (归档时完整保留上述所有文件)
```

---

## 触发机制

**所有阶段采用手动触发**：只有输入对应指令才进入对应阶段工作。

| 阶段 | 触发命令 | 自动触发技能 |
|------|----------|--------------|
| 提案初始化 | /wf:init | - |
| 需求明确 | /wf:clarify | brainstorming |
| 设计 | /wf:design | brainstorming |
| 任务拆分 | /wf:split | - |
| 执行计划 | /wf:plan | writing-plans |
| 编码实现 | /wf:apply | tdd |
| 审查验证 | /wf:verify | verification |
| 归档 | /wf:archive | - |

---

## 与 OpenSpec 原生命令的关系

| WF 命令 | 关联的 OpenSpec 命令 | 附加工作 |
|---------|---------------------|----------|
| /wf:init | /opsx:new | 仅创建空 proposal |
| /wf:clarify | - | 触发 brainstorming 技能 |
| /wf:design | - | 触发 brainstorming 技能 |
| /wf:split | - | 纯任务拆分 |
| /wf:plan | - | 触发 writing-plans 技能 |
| /wf:apply | - | 触发 tdd 技能 |
| /wf:verify | /opsx:verify | + TDD 验证 + 覆盖率检查 |
| /wf:archive | /opsx:archive | 确保 brainstorm.md 归档 |

---

## 适用场景

- **中型项目**：1-3 个月，2-5 人
- **大型项目**：3-6 个月，5-10 人

---

## 阶段依赖关系

```
wf:init → wf:clarify → wf:design → wf:split → wf:plan → wf:apply → wf:verify → wf:archive
```

每个阶段完成后才能进入下一阶段。