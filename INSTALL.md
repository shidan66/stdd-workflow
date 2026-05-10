# 安装指南

## 安装步骤详解

### 1. 安装 OpenSpec

如果没有安装 OpenSpec，运行：
```bash
npm install -g @fission-ai/openspec@latest
```

验证安装：
```bash
openspec --version
```

### 2. 安装 Superpowers

检查 OpenCode 配置（~/.config/opencode/opencode.json）是否已配置 Superpowers。

如果没有，按照官方文档安装：
https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md

### 3. 复制命令文件

将 `src/commands/` 目录下的所有 `.md` 文件复制到 `.opencode/commands/` 目录。

复制命令：
```bash
cp -r stdd-workflow/src/commands/* .opencode/commands/
```

## 验证安装

安装完成后，可以在 OpenCode 中输入以下命令验证：
- `/stdd:status` - 查看工作流状态
- `/stdd:propose` - 开始新提案

如果命令可用了，说明安装成功。