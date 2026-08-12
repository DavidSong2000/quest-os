# Quest OS v1 schema

Quest OS v1 使用两个数据库。真实数据保存在用户自己的 Notion 中；本文只描述可复用结构。

## Projects

| Property | Type | Purpose |
| --- | --- | --- |
| Name | Title | 项目名称 |
| Status | Select | Idea、Active、Waiting、Paused、Done |
| Area | Text | 简单的领域标签；v1 不建立独立 Areas 数据库 |
| Outcome | Text | 项目完成标准 |
| Target Date | Date | 可选目标日期 |
| Tasks | Relation | 与 Tasks 的双向关系 |
| Progress | Rollup | 关联任务中 Status 为 Done 的比例 |

### Progress 手动配置

当前连接器不能可靠创建 Progress rollup。请在 Notion 界面中为 Projects 添加 Rollup 属性：

1. Relation 选择 `Tasks`。
2. Property 选择 `Status`。
3. Calculate 选择按分组百分比，并选择 `Done`。
4. 将显示格式设为百分比。

如果当前 Notion 界面不提供“按分组百分比”，暂时省略 Progress；不要为了替代它增加隐藏字段或复杂公式。

## Tasks

| Property | Type | Purpose |
| --- | --- | --- |
| Name | Title | 任务名称 |
| Status | Select | Inbox、Next、Doing、Waiting、Blocked、Done、Cancelled |
| Project | Relation | 关联唯一 Projects 数据库 |
| Do Date | Date | 计划处理日期，可为空 |
| Due Date | Date | 目标或截止日期，可为空 |
| Deadline Type | Select | Target、Hard |
| Priority | Select | Low、Medium、High |
| Done Criteria | Text | 可验证的完成条件 |
| Source | URL | 旧页面或外部资料链接 |

任务细节写在任务页面正文，不建立重复的大段文本属性。v1 不包含 Milestone 类型、子任务、自定义提醒等级或 Apple Alarm 同步。

## Views

Projects：

- Active Projects：Status 为 Active。
- All Projects：全部项目。

Tasks：

- Inbox：Status 为 Inbox。
- Today：Status 为 Next 或 Doing，且 Do Date 为今天或早于今天。
- Upcoming：Status 为 Next 或 Doing，且 Do Date 晚于今天。
- Waiting & Blocked：Status 为 Waiting 或 Blocked。

连接器已建立这些视图，但无法可靠表达 Today 和 Upcoming 的相对日期条件。请在 Notion 界面中补上上述 Do Date 过滤；不要增加辅助日期字段。

## Dashboard

根页面包含以下数据库链接视图：

- Active Projects
- Inbox
- Today
- Upcoming
- Waiting & Blocked

并保留 Projects 和 Tasks 完整数据库入口。

## Data boundary

- Quest OS 可以独立启动，不要求先整理旧 Notion。
- 知识库、论文笔记和历史项目原则上原地保留，通过 Source 链接引用。
- 只有仍需执行的活跃任务才考虑人工迁入 Tasks。
- 公开仓库不得保存个人 workspace、页面或数据库标识符。
