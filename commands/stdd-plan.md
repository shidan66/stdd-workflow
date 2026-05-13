---
description: 执行计划阶段 - 调用 writing-plans 技能，基于 tasks.md 生成执行计划 plan.md
---

# STDD: 执行计划

## 目标

调用 writing-plans 技能，基于 tasks.md 生成符合 Superpowers 规范的执行计划 plan.md。

## 前提

- 已完成 `/stdd-propose` 阶段
- tasks.md 包含原子任务清单
- proposal.md、spec.md、design.md 已生成

## 执行步骤

### 1. 检查自定义模板

检查项目目录下是否存在 `openspec/schemas/stdd/templates/plan.md`：
- 如果存在，加载自定义模板
- 如果不存在，使用 STDD 默认模板

### 2. 加载 writing-plans 技能

调用 writing-plans 技能获取规范的 plan 格式要求。

### 3. 读取 tasks.md

获取任务清单，分析：
- 任务依赖关系
- 可并行执行的任务
- 串行执行的任务
- 关键路径

### 4. 生成 plan.md

按照 writing-plans 技能规范生成执行计划：

```markdown
# [Feature Name] Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** [One sentence describing what this builds]

**Architecture:** [2-3 sentences about approach]

**Tech Stack:** [Key technologies/libraries]

---

## 任务依赖图

## 执行顺序

### 阶段1: [可并行任务组]
- [ ] Task 1.1
- [ ] Task 1.2

### 阶段2: [依赖阶段1的任务组]
- [ ] Task 2.1 (依赖 Task 1.1)

## TDD 规范
每个任务执行流程：
1. 写测试用例
2. 运行测试（预期失败）
3. 写实现代码
4. 运行测试（预期通过）
5. 重构

## 具体任务步骤

### Task 1.1: [任务名称]

**Files:**
- Create: `exact/path/to/file.py`
- Modify: `exact/path/to/existing.py:123-145`
- Test: `tests/exact/path/to/test.py`

**Step 1: Write the failing test**
```python
def test_specific_behavior():
    result = function(input)
    assert result == expected
```

**Step 2: Run test to verify it fails**
Run: `pytest tests/path/test.py::test_name -v`
Expected: FAIL with "function not defined"

**Step 3: Write minimal implementation**
```python
def function(input):
    return expected
```

**Step 4: Run test to verify it passes**
Run: `pytest tests/path/test.py::test_name -v`
Expected: PASS

**Step 5: Commit**
```bash
git add tests/path/test.py src/path/file.py
git commit -m "feat: add specific feature"
```
```

## 输出

告诉用户：
- plan.md 已生成
- 使用的模板来源（自定义/默认）
- 下一步是 `/stdd-apply` 执行任务
