---
date: 2026-02-27
topic: claude-code-plugin-creation
---

# Claude Code Plugin 创建方法

## Plugin vs 独立配置

| 方式 | 适用场景 |
|------|----------|
| 独立配置 `.claude/` | 单项目、个人使用、快速实验 |
| Plugin | 团队共享、跨项目复用、版本化分发 |

## 创建步骤

### 1. 目录结构

```
my-plugin/
├── .claude-plugin/
│   └── plugin.json       # manifest（必须）
├── commands/             # 自定义命令
├── agents/               # 自定义 Agent
├── skills/               # Agent Skills
├── hooks/
│   └── hooks.json        # 事件钩子
├── .mcp.json             # MCP server
├── .lsp.json             # LSP server
└── settings.json         # 默认设置
```

> 注意：`commands/`、`skills/` 等目录必须在 plugin 根目录，不能放在 `.claude-plugin/` 内。

### 2. Manifest 文件

`.claude-plugin/plugin.json`:

```json
{
  "name": "my-plugin",
  "description": "插件描述",
  "version": "1.0.0",
  "author": { "name": "Your Name" }
}
```

`name` 字段作为 skill 命名空间前缀，如 `/my-plugin:hello`。

### 3. 添加 Skill

`skills/hello/SKILL.md`:

```markdown
---
description: Greet the user
---

Greet the user named "$ARGUMENTS" warmly.
```

- `$ARGUMENTS` 接收用户输入
- 调用方式：`/my-plugin:hello Alex`

### 4. 本地测试

```bash
# 单个插件
claude --plugin-dir ./my-plugin

# 多个插件
claude --plugin-dir ./plugin-one --plugin-dir ./plugin-two
```

## 其他功能

- **默认 Agent**：`settings.json` 中 `"agent": "agent-name"` 激活指定 agent
- **LSP**：`.lsp.json` 配置语言服务器
- **Hooks**：`hooks/hooks.json` 配置事件处理器

## 从独立配置迁移

```bash
cp -r .claude/commands my-plugin/
cp -r .claude/agents my-plugin/
cp -r .claude/skills my-plugin/
# hooks 从 settings.json 的 hooks 对象复制到 hooks/hooks.json
```

## 分发

- 本地：`--plugin-dir` 标志
- 团队：通过 marketplace，`/plugin install` 安装
- 官方提交：claude.ai/settings/plugins/submit
