# 构建说明：从 source/ 生成 skills/

版本：0.1.2（未发布草稿，分支 optimize/2026-11-05）。

## 唯一维护源

手工改动只改 `source/`，不要直接改 `skills/`：

- `source/common/editing-core.md`：两个 skill 共用的编辑标准（语气、默认决策、开始工作、精修方法、交付），唯一一份。
- `source/common/preferences.md`、`research.md`、`file-preservation.md`：两个 skill 共用的参考文件。
- `source/business-ppt-editor/`：PPT 入口专属内容（SKILL.md、checklist、domains、examples）。
- `source/business-word-editor/`：Word 入口专属内容（同上）。

## 生成步骤

1. 把 `source/business-ppt-editor/SKILL.md`、`source/business-word-editor/SKILL.md` 分别复制到 `skills/` 下同名位置。
2. 把 `source/business-ppt-editor/references/`、`source/business-word-editor/references/` 下的专属文件（checklist、domains、examples）复制到 `skills/` 下同名位置。
3. 把 `source/common/preferences.md`、`research.md`、`file-preservation.md` 各复制一份到两个 skill 的 `references/`。
4. 把 `source/common/editing-core.md` 复制到两个 skill 的 `references/common/editing-core.md`。
5. 核对：两个 skill 的 `references/common/editing-core.md` 内容相同；SKILL.md 里引用的每个 `references/*.md` 在该 skill 的 `references/` 里都存在；SKILL.md 的 metadata 版本与本次发版一致。

注意：checklist 的“内容”和“处理失败”两节在两个 skill 里文字相同，改动时必须同时改两个 checklist 文件；“页面与文档”（PPT）与“文档结构与排版”（Word）两节为专属内容，不要互相复制。未来可进一步把 checklist 的共用两节抽成独立文件，本次未做。

## 未复现的部分

原 PowerShell 构建脚本 `Build-Packages.ps1` 不在仓库内（只在 0.1.1 的总包 zip 里），本次没有编造其内容；上面的 5 步是等价的手工/脚本化构建流程，脚本化时按此复制关系实现即可，不要求复现原脚本的全部校验。

## 本次未做的事

- 根目录的 5 个 zip 包未删除：迁到 GitHub Releases 需要 Releases 操作，MCP 工具做不到，留待 Ling 决定（见 CHANGELOG）。
- WorkBuddy 实机导入、真实 PPTX/DOCX 端到端验收未做：需要宿主客户端与真实文件，本次无法代做，见 CHANGELOG。
