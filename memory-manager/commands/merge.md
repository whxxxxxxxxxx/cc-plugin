---
description: 将 ./.claude/sessions/ 中的多个记忆文件合并为一个统一的记忆文件。
---

# 记忆合并

参数：$ARGUMENTS

## 操作步骤

1. 将 $ARGUMENTS 解析为逗号分隔的文件名列表，例如 `2026-01-01-topic.md,2026-01-02-other.md`
2. 从 `./.claude/sessions/<filename>` 读取每个文件
3. 分析所有内容并将其合并为一个连贯的记忆文档：
   - 删除重复信息
   - 按主题/类别组织
   - 保留最新版本的冲突事实
4. 生成一个简洁的主题 slug 来总结合并后的内容（小写字母、中划线，最多 30 个字符，使用英文）
5. 使用今天的日期作为新文件名：`YYYY-MM-DD-<merged-topic>.md`
6. 将合并后的文件写入 `./.claude/sessions/YYYY-MM-DD-<merged-topic>.md`

## 合并后文件的格式

```markdown
---
date: YYYY-MM-DD
topic: <merged-topic>
merged-from:
  - <source-file-1>
  - <source-file-2>
---

<合并去重后的内容>
```

保存后，确认："已将 N 个文件合并到 `.claude/sessions/YYYY-MM-DD-<merged-topic>.md`"

询问用户是否要删除原始源文件。
