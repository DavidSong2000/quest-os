# Quest OS contributor rules

## Notion safety boundary

- 所有任务只写入唯一的 Tasks 数据库。
- 所有项目只写入唯一的 Projects 数据库。
- 写入前按精确名称或已确认的 ID 查找，不得创建重复数据库。
- 只允许在用户明确指定的 Quest OS 根页面内创建或修改内容。
- 不得修改 Quest OS 之外的 Notion 页面、数据库或属性。
- 未经用户明确确认，不得迁移、移动、重命名、归档或删除旧内容。
- 描述不完整但值得保留的任务可以进入 Inbox。
- 日期不确定时保持为空，不得编造硬截止日期。
- 旧知识库和历史资料优先通过 Source 链接，不默认迁入任务系统。
- 需要分块时只使用两层结构：工作块作为父任务，叶子任务必须是可执行动作。
- 不得把项目、工作块和叶子任务继续递归成复杂依赖树。
- Dashboard 的行动视图优先只显示存在 Parent Task 的叶子任务，避免父子同时出现造成重复感。

## Public/private boundary

- 公开仓库只保存可复用的结构、规则、文档和无私人含义的示例。
- 不得提交真实 workspace ID、Notion 页面或数据库 ID、私人页面 URL、访问凭据或真实个人任务。
- 本地私人状态仅保存到 `state/*.local.md` 或其他已忽略的 private 目录。
- 修改 `.gitignore` 时必须继续保护上述私人内容。

## Scope

- 遵循 KISS 和 YAGNI。
- v1 只维护 Projects、Tasks、两层任务关系和 Dashboard。
- 不为未确认需求增加数据库、字段、自动化或游戏化机制。
- Apple Alarm、外部日历和提醒同步不属于 v1。
