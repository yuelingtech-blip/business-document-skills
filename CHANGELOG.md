# 变更记录

## 0.1.2（未发布草稿，分支 optimize/2026-11-05）

本次只改分支 `optimize/2026-11-05`，未动主分支，未合并，未删除主分支现有文件，根目录的 zip 包未动。

### 改动

- 抽共用（P0-2）：两个 SKILL.md 里重复的“共用编辑标准”抽成唯一一份 `source/common/editing-core.md`，并复制到两个 skill 的 `references/common/editing-core.md`；两个 SKILL.md 只剩入口、交付物和专属规则的差异，原共用段落改为指向共用文件的短指针加五条不可动摇摘要。
- 源码入库（P0-1，在仓库内可行的部分）：新建 `source/` 作为唯一维护源，含共用文件、两个 skill 的专属 SKILL 与参考文件，以及 `source/BUILD.md`（从 source/ 生成 skills/ 的 5 步复制关系）。原 PowerShell 构建脚本不在仓库内，本次没有编造其内容。
- 参考文件专属化：checklist 拆开——PPT 版保留“页面与文档”，Word 版改为“文档结构与排版”（节结构、标题级别、分页、脚注、交叉引用、修订），Word 清单里不再有“页数、页序、母版、隐藏页、动画”这类 PPT 检查项；domains 拆开——PPT 版去掉“非 PPT 文档”一节，Word 版该节改名为“Word 文档”；examples 拆开——Word 版的信息密度例和截图例改为 Word 场景（拆表、原 DOCX 样式与脚注验证）。
- 路由表（P1-1）：两个 SKILL.md 开头新增“参考文件路由”表，诊断、精修、新稿、短文本各读哪几个参考文件、默认不读哪几个，渐进加载。
- 不接任务（P1-4）：两个 SKILL.md 开头各补 3 条“不接的任务”示例（PPT 不接纯邮件/纯 Word/代码图片视频；Word 不接逐页 PPT/PPTX 输出/代码图片视频），混合任务先拆步或指定主入口。
- 版本（P1-2）：两个 SKILL.md 的 metadata 版本同步为 0.1.2；preferences.md 的版本行同步为 0.1.2。README、VALIDATION 的 0.1.1 版本行未动，待发布时统一同步，避免分支草稿冒充已发布版本。
- 通用安装（P2-1）：INSTALL.md 新增“通用安装（其他宿主）”一节（文件夹结构、不要只复制 SKILL.md、同名版本先备份比对），不写未经实机验证的隐藏路径。

### 影响的 skill

- business-ppt-editor：SKILL.md（路由表、不接任务、共用指针、版本 0.1.2）、references/checklist.md、domains.md、common/editing-core.md（新增）、preferences.md（版本行）。
- business-word-editor：SKILL.md（同上）、references/checklist.md、domains.md、examples.md、common/editing-core.md（新增）、preferences.md（版本行）。

### 本次在仓库内可做的验收（已做）

- YAML frontmatter：两个 SKILL.md 的 frontmatter 均含 name、description、metadata.version，且版本均为 0.1.2；用脚本解析 frontmatter 的三个必填字段通过。
- 引用存在性：两个 SKILL.md 里引用的全部 `references/*.md`（含新增的 `references/common/editing-core.md`）在各自 skill 的 `references/` 里都存在；`source/` 下的 SKILL 引用与之一致。
- 共用一致性：两个 skill 的 `references/common/editing-core.md` 与 `source/common/editing-core.md` 内容相同；共用文件里的相对链接已改为 `../` 形式，从 `references/common/` 位置可正确指向同级参考文件。
- 专属化检查：Word 版 checklist 不再含“页数、页序、母版、隐藏页、动画”；PPT 版 domains 不再含“非 PPT 文档”一节。

### 明确未完成、不要谎称通过的验收

- WorkBuddy 实机导入：未做。需要 WorkBuddy 客户端实际导入两个 workbuddy.zip，本次无法代做。
- 真实 PPTX/DOCX 端到端修改与视觉/编辑性验收：未做。需要真实 Office 文件与渲染环境，本次无法代做。
- 原 PowerShell 脚本的全部校验复现：未做。原脚本不在仓库内，本次只给出了等价的 5 步复制关系（见 source/BUILD.md）。

### 待 Ling 决定的事（本次未擅自决定）

- 许可：不要擅自加 LICENSE、不要选定开源协议。待 Ling 决定：写自用声明，还是补 LICENSE 并确认作者信息。
- 根目录 zip 包是否迁到 GitHub Releases：MCP 工具做不到 Releases 操作，留待 Ling 决定；迁移完成前不要删除现有 zip。
- 是否合并本分支、提 PR：本分支已就绪可提 PR，提 PR 与合并的操作留待 Ling 在 GitHub 上确认（见分支汇总）。
- 实机验收：WorkBuddy 导入与真实文件端到端验收需 Ling 或有对应环境的宿主完成，验收通过后再发布 0.1.2。
