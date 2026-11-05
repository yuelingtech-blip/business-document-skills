# 安装与使用

版本 0.1.1。仅两个技能，按交付对象选一个即可：商业 PPT、商业 Word 与文字。每个独立携带研究、写作、去 AI 味和审核规则，无需互相依赖。当前仅生成可审阅安装包，未安装到用户全局目录，未上传市场。

## WorkBuddy

1. 打开左侧“专家·技能·连接器”，选择“技能”。
2. 选择“添加技能 → 上传技能”。
3. 按需导入 `business-ppt-editor-v0.1.1-workbuddy.zip` 和/或 `business-word-editor-v0.1.1-workbuddy.zip`。不要上传整个交付总包。
4. 在“已安装”中确认启用。新建对话，用自然语言说明任务，必要时在界面选择对应技能。

入口按 [WorkBuddy 官方客户端文档](https://www.codebuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market) 编写。元数据参考 [WorkBuddy 开放平台规范](https://open.workbuddy.cn/docs/skill)。本包包含其列为必填的描述、双语简介、版本、作者字段；`author: Local Custom` 是本地自用占位标识，不代表已确认公开发布作者。公开上架前应由用户确认作者信息。

导入包选择 ZIP 根目录直接包含 `SKILL.md` 和 `references/`，避免嵌套总包。这是本版的打包选择；官方页面未完整规定所有客户端版本的 ZIP 层级处理。本次没有在 WorkBuddy 实机导入验证，若提示层级/元数据错误，应根据实际提示调整封装，保持正文不变，不宣称已安装成功。不采用未经本机验证的隐藏技能路径。

## Codex Windows

使用 完整维护包中的 `packages/codex/` 中两个完整文件夹，或解压对应 `-codex.zip`。将需要的文件夹放入：

- 当前官方用户级路径：`%USERPROFILE%\.agents\skills\`。
- 团队/项目内使用：项目的 `.agents\skills\`。

例如用户级目标为 `%USERPROFILE%\.agents\skills\business-ppt-editor\SKILL.md`，同级有 `references\`。不要只复制 SKILL.md。

路径依据 [OpenAI 官方 Build skills 文档](https://learn.chatgpt.com/docs/build-skills)。当前会话也列出了旧式 `.codex\skills` 下的现有技能；为新包提供当前官方 `.agents\skills` 路径，不把旧路径列为新安装首选。不要同名装在多个路径，以免重复出现。若目标已存在，先保留原版本并检查差异，不直接覆盖。界面未出现时重启/新开会话再确认。

这次没有写入上述全局路径。此交付是直接 Skill 文件夹的个人试用包，不是公开插件市场上架包。需要团队公开分发时再考虑官方插件封装。

## 日常调用

PPT 示例：

> 使用 business-ppt-editor。根据这些资料做泰国汽车市场汇报，供管理层判断渠道投入。沿用我给的参考版，先检查数据统计期与口径，再生成逐页内容和可编辑 PPT。

> 使用 business-ppt-editor。修改这份 PPT：保留页数、页序、数据和版式，去空话，修正标题与证据不匹配的地方。

Word/商业文字示例：

> 使用 business-word-editor。把这份会议转写整理成简洁纪要，保留商务条件、分歧、责任人和期限，不确定内容列待核。

> 使用 business-word-editor。根据往来材料写英文供应商回复：必要条件不变，期限可以谈。只给可直接使用的邮件正文。

> 使用 business-word-editor。把这些资料写成管理层研究报告，追溯原始来源，区分事实、判断和建议，输出可编辑 Word。

自然语言任务也可触发，但自动匹配由宿主决定。Word 入口也负责邮件和消息，不必为了短文本安装第三个技能。宿主缺少编辑或检索能力时，技能会交付能可靠完成的文本、逐页建议和待核说明。

## 通用安装（其他宿主）

Codex 与 WorkBuddy 之外的宿主，按 skill 文件夹结构安装，不按某个客户端的隐藏路径猜测：

- 一个完整 skill 就是一个文件夹，内含 `SKILL.md` 和 `references/`（含 `references/common/editing-core.md`），缺一不可；不要只复制 `SKILL.md`。
- 把整个 skill 文件夹复制到宿主的技能目录（以宿主当前文档为准），不要同时在多个路径装同名 skill，以免重复触发。
- 目标已有同名版本时，先备份原版本，再比对差异，不直接覆盖。
- 本节未经在该宿主实机验证的路径不在此列；若宿主报错，按其报错调整封装，不宣称已安装成功。

## 修改和重新打包

`source/` 是唯一维护源：两个流程文件 + `common/editing-core.md` + 共用参考文件。两版入口和两平台包由 `Build-Packages.ps1` 生成，不手工分别修改四份成品。

在 Windows PowerShell 中进入此文件夹后执行：

```powershell
.\Build-Packages.ps1 -OutputDirectory (Join-Path $PWD 'packages-next')
```

脚本拒绝覆盖已有目标，输出位置必须在本包目录内；不用更改全局执行策略。如本机策略阻止脚本，先按组织政策处理或采用手工复制，不降低全局安全设置。脚本仅本地生成和校验包，不联网、不安装、不改用户配置。

修订版本时同步修改构建脚本中的版本、偏好记录及发布说明。本版的跨宿主差异仅入口元数据和 WorkBuddy 的资源引用索引；主体规则和参考内容保持一致。

## 验证范围

已做的结构检查见“验证与验收.md”。本版不能宣称已通过实际 Office 文件保真或 WorkBuddy 客户端安装测试。导入后先用一份副本验收，出现数据、编辑性或版式问题按实际失败收窄修复。
