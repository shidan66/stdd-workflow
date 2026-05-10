# 安装指南

按照下面安装步骤进行安装；

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

将本项目的模板文件复制到项目中的 `stdd-templates/` 目录。

- 如果原项目中已有对应名字的模板文件，则忽略复制
- 如果原项目模板目录中没有对应名字的模板文件，则进行复制

复制命令：
```bash
# 创建目标项目的模板目录（如果不存在）
mkdir -p stdd-templates

# 复制模板文件（同名文件会被跳过）
for file in stdd-workflow/stdd-templates/*; do
  filename=$(basename "$file")
  if [ ! -f "stdd-templates/$filename" ]; then
    cp "$file" stdd-templates/
  fi
done
```