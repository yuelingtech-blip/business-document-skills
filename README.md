# 商业 PPT 与 Word 写作 Skill

两个独立入口，整合研究、分析、写作、精简、去 AI 味和文件审核。版本 0.1.1。

| Skill | 用途 |
|---|---|
| `business-ppt-editor` | 汇报、市场研究、BP 演示、逐页文案、已有 PPT 精修 |
| `business-word-editor` | 报告、方案、BP 正文、纪要、商务邮件和工作消息 |

共同语气：直接、自然、具体，把事情和条件讲清楚。不用“商业闭环、战略目标、赋能、生态”等大词包装普通业务。有必要的专业概念保留，不补造事实。

已有文件默认延续原页、数据、品牌和可编辑对象，不无必要重绘。实际检索和 Office 编辑依赖运行软件已有能力。

## Codex Windows

将 `skills/` 下需要的完整 Skill 文件夹复制到 `%USERPROFILE%\.agents\skills\`，或项目的 `.agents\skills\`。不要只复制 SKILL.md；已有同名版本先检查差异，不直接覆盖。

```text
使用 business-ppt-editor 修改这份PPT，保留原页和数据，按我常用语气改文字，不堆大词。
```

```text
使用 business-word-editor 整理会议纪要，保留条件、分歧、负责人和期限。
```

## WorkBuddy

在“技能 → 添加技能 → 上传技能”中导入 仓库根目录对应的 `-workbuddy.zip`。一个 ZIP 就是一个完整 Skill，不要上传整个仓库 ZIP。

## 维护

- `skills/`：可直接复制的 Codex 技能。
- 根目录的四个 ZIP：两个技能各自的 Codex 与 WorkBuddy 安装包。
- `business-document-skills-v0.1.1-github.zip`：完整维护包，解压后含 `source/` 和 `Build-Packages.ps1`。
- 完整维护包中的构建脚本仅本地生成和校验，不联网、不安装、不改全局配置。
- `INSTALL.md`、`VALIDATION.md`：安装说明和验证范围。

维护时先解压完整维护包，修改 source 后，在解压目录的 Windows PowerShell 中运行：

```powershell
.\Build-Packages.ps1 -OutputDirectory (Join-Path $PWD 'packages-next')
```

再将新输出的 `codex/` 下两个文件夹同步到 `skills/`。脚本拒绝覆盖已有输出；遵守本机执行策略，不需要降低全局保护。

已检查包结构、引用、编码和跨平台规则一致性。未做 WorkBuddy 实机导入或真实 Office 文件端到端验收。不保证 AI 检测分数，不用于伪造来源。

不含原始聊天记录、客户资料、业务财务数据或凭证，教学案例均为虚构。未附开源许可，公开分发前由所有者决定许可。
