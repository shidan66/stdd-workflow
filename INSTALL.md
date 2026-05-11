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

### 3. 复制指令文件和模板文件
使用git将 `https://github.com/shidan66/stdd-workflow.git` 下载到一个临时目录，下载后得到的文件夹路径记为`$STDD_HOME`；

**拷贝命令文件**

将`$STDD_HOME/commands/`下面所有的.md文件拷贝到当前项目的`.opencode/commands/` 目录下，如果当前项目下没有`.opencode/commands/`则先创建目录再拷贝。

**拷贝模板文件**

将`$STDD_HOME/schemas/`目录下面的子目录和文件拷贝到项目中的 `openspec/schemas/` 目录下，如果当前项目下没有`openspec/schemas/`则先创建目录再拷贝。

**清理$STDD_HOME目录**

删除$STDD_HOME目录及其下面的所有子目录和文件。

### 4. 修改项目中openspec文件，将stdd作为默认schema

修改当前项目中`openspec/config.yaml`，将schema改为stdd

### 5. 提醒用户退出后重新进入opencode
使用中文提醒用户退出后重新进入opencode