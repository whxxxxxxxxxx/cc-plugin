---
description: 创建记忆文件并保存到 ./.claude/sessions/
---

# 记忆创建

用户想要创建以下内容的记忆：$ARGUMENTS

## 操作步骤

1. 分析 $ARGUMENTS 中提供的记忆内容，生成一个简洁的主题 slug（小写字母、中划线、无空格，最多 10 个字符）
2. 获取今天的日期，格式为 YYYY-MM-DD
3. 构建文件名：`YYYY-MM-DD-topic.md`
4. 确保目录 `./.claude/sessions/` 存在（如不存在则创建）
5. 将记忆文件写入 `./.claude/sessions/YYYY-MM-DD-topic.md`

## 记忆文件格式

```markdown
---
date: YYYY-MM-DD
topic: <topic>
---

<基于 $ARGUMENTS 总结和结构化的记忆内容>
```

内容要清晰简洁。总结关键事实、决策或值得记住的背景。

保存后，向用户确认："记忆已保存到 `.claude/sessions/YYYY-MM-DD-topic.md`"
