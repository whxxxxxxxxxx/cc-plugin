---
description: 将记忆文件升级为项目规则并保存到 ~/.claude/rules/
---

# 记忆升级

参数：$ARGUMENTS

## 操作步骤

1. 将 $ARGUMENTS 解析为单个文件名，例如 `2026-01-01-topic.md`
2. 从 `./.claude/sessions/<filename>` 读取文件
3. 将记忆内容转换为可重用的项目规则：
   - 提取可操作的指南、规范或约束
   - 以适合规则文件的祈使/指令风格重写
   - 删除不普遍适用的会话特定上下文
4. 根据主题生成简洁的规则名称（小写字母、中划线，最多 30 个字符，使用英文）
5. 确保 `~/.claude/rules/` 目录存在（如不存在则创建）
6. 将规则文件写入 `~/.claude/rules/<rule-name>.md`

## 规则文件格式

```markdown
---
name: <rule-name>
source-memory: <original-filename>
upgraded-at: YYYY-MM-DD
---

# <规则标题>

<转换为清晰、可操作的规则/指南的内容>
```

保存后，确认："规则已保存到 `~/.claude/rules/<rule-name>.md`"

询问用户是否要保留原始记忆文件或删除它。
