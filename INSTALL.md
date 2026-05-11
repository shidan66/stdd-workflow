# 安装指南

按照下面安装步骤进行安装，安装过程尽量使用中文输出提示信息。

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

### 4. 复制模板文件

将本项目的`template/`下的`stdd`目录及其下面的文件复制到项目中的 `openspec/schema/` 目录下。
- 如果原项目中已有对应名字的模板文件，则忽略复制
- 如果原项目模板目录中没有对应名字的模板文件，则进行复制

### 5. 修改项目中openspec文件，将stdd作为默认schema

修改当前项目中`openspec/config.yaml`，将schema改为stdd

### 6. 提醒用户退出后重新进入opencode
使用中文提醒用户退出后重新进入opencode