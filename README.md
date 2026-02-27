# Claude Code Plugin Marketplace

Claude Code 插件市场，提供记忆管理相关的插件。

## 已有的插件

### memory-manager

Claude Code 记忆管理插件，用于创建、加载、合并和升级记忆文件。

#### 功能

- **创建记忆** (`/memory create`) - 创建新的记忆文件
- **加载记忆** (`/memory load`) - 加载已有的记忆文件
- **合并记忆** (`/memory merge`) - 合并多个记忆文件
- **升级记忆** (`/memory upgrade`) - 升级旧版本的记忆文件

## 安装方法

### 1. 添加插件市场

首先，添加此插件市场到你的 Claude Code：

```
/plugin marketplace add 你的用户名/cc-plugin
```

### 2. 安装插件

添加市场后，安装具体的插件：

```
/plugin install memory-manager
```

### 3. 使用插件

安装完成后，可以使用以下命令：

```
/memory create
/memory load
/memory merge
/memory upgrade
```

## 贡献

欢迎提交 Pull Request 来添加更多插件！
