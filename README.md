# Quest OS

Quest OS 是一个基于 Notion 的极简个人任务系统模板。它只保留两个核心数据库：Projects 和 Tasks，并通过一个简单 Dashboard 汇总当前行动。

设计原则：

- KISS / YAGNI：先解决项目和任务管理，不预建复杂游戏化系统。
- 私人数据与开源模板分离：仓库只保存通用结构、规则和说明；真实项目、任务、页面 ID 与 Notion 链接留在个人 Notion 或被 Git 忽略的本地文件中。
- 旧资料优先链接：知识库、历史笔记和旧项目不因使用 Quest OS 而被强制迁移。
- 只有真正活跃的行动项才进入 Tasks。

## v1 组成

- Projects：记录项目状态、完成标准和目标日期。
- Tasks：所有可执行任务的唯一入口。
- Dashboard：Active Projects、Inbox、Today、Upcoming、Waiting & Blocked。
- 两层任务树：工作块作为父任务，真正可执行的动作作为叶子任务。

推荐交互方式是直接用自然语言告诉 Codex 要做什么。Codex 负责判断项目、工作块、任务、状态和关系；手机端主要用于查看、快速记入 Inbox 和把任务标为 Done。

字段与手动配置说明见 [docs/schema.md](docs/schema.md)。

## 私人实例

你可以给自己的 Notion 根页面取任何名字，例如“松松的冒险日志”。这个名称以及其中的真实内容不会进入公开仓库。

建议的边界：

- 公开仓库：模板设计、字段定义、使用规则、通用文档。
- 私人 Notion：真实 Projects、Tasks、笔记关系和生活数据。
- 本地私有状态：保存于 `state/*.local.md`，由 `.gitignore` 排除。

### 换电脑后继续使用

1. 从 GitHub 克隆 Quest OS 仓库，恢复公共规则和结构说明。
2. 登录原来的 Notion 账号，确认私人根页面和两个数据库仍在同一 workspace 中。
3. 在新电脑上重新授权 Notion connector，只授权需要访问的 workspace。
4. 让 Codex 按根页面名称以及 Projects、Tasks 的精确名称重新查找并验证结构。
5. 将重新发现的页面和数据库 ID 写入本机的 `state/notion.local.md`；该文件不会上传 GitHub。

Notion 中的真实数据由 Notion 云端保留，GitHub 不保存也不恢复这些数据。若需要防范误删或账号问题，应另行定期导出 Notion；这与换机接续是两套机制。

任务树最多两层，不继续扩展为复杂依赖图。目前不包含自动化同步、提醒桥接、后端、PWA、XP、等级、装备或成就系统。

## License

MIT
