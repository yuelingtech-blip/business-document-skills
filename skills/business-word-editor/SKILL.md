---
name: business-word-editor
description: 起草和修改商业Word文档、报告、方案、纪要、BP正文、商务邮件和工作消息，整合资料研究、分析、写作、精简、去AI味、双语校准及排版审核；不处理PPT页面制作。
metadata:
  version: "0.1.2"
---

# 商业 Word 与文字工作台

一个入口完成商业报告、研究分析、BP 正文、方案、汇报、会议纪要、商务邮件及工作消息的研究、组织、起草、改写、翻译校准、去 AI 味和文件排版。Word 指文档与商业文字入口，不要求每次产出 DOCX。用户要邮件就给邮件，要简短消息就给可直接使用的正文。起草不代表授权发送。

使用本包内部规则和宿主已有工具，不要求用户再拼接写作、研究、审核技能。研究按需读取 [资料研究与业务分析](references/research.md)；依据任务读取 [用户偏好](references/preferences.md)、[场景规则](references/domains.md) 和 [示例](references/examples.md)。

## 参考文件路由：按任务读，不全读

| 任务 | 先读 | 需要时再读 | 默认不读 |
| --- | --- | --- | --- |
| 诊断问题 | references/checklist.md | references/examples.md | references/research.md（除非诊断涉及数据来源） |
| 保留式精修已有 Word | references/file-preservation.md、references/checklist.md | references/preferences.md、references/domains.md、references/examples.md | references/research.md |
| 从零起草 / 研究型文档 | references/research.md、references/domains.md、references/preferences.md、references/examples.md | references/file-preservation.md | 无 |
| 纪要、邮件、短消息 | references/examples.md、references/preferences.md | references/checklist.md | references/research.md、references/file-preservation.md（拿到原文件后再读） |

共用编辑标准见 [共用编辑标准](references/common/editing-core.md)，任何任务都要先读它。

## 本 skill 不接的任务

- 逐页 PPT 制作、改 PPT 版式、修 PPT 图表、做演示备注：用 business-ppt-editor。
- 只要 PPT 大纲转逐页文案且要出 PPTX：用 business-ppt-editor，本 skill 只给文字稿。
- 代码调试、图片生成、视频制作：不属于本 skill，另找对应工具。

混合任务先拆成 PPT 和 Word 两步，或由用户指定以一个入口为主，另一个只给文本建议，不要两个入口同时改同一份材料。


## 按实际文种工作

- **研究报告/方案/BP**：明确给谁看、要支持哪个判断或行动。先组织证据和逻辑，区分事实、解释、建议与待核假设。不要固定塞满执行摘要、五大优势、生态闭环和宏大展望；章节由问题决定。
- **已有 Word**：沿用用户已有结构、格式及术语，优先修改具体段落。没有授权不把修改扩成全篇重写。执行前读取 [文件保护](references/file-preservation.md)。
- **会议纪要**：去除转写重复，将决定、分歧、待核和待办分开。保留金额、比例、条件、责任人和原有期限；转写口径冲突不可擅自统一。例如每年车辆额度与达标兑现数量不一致，应列待核而非择一删除。相对日期只有会议日期明确时才转换。
- **商务邮件/回复**：提取沟通目的、对方关切、我方必要条件、可谈条件和希望对方做的下一步。保留当前任务的谈判边界。感谢/确认收悉类邮件直接简洁写，不附冗长策略分析；用户要求谈判策略时再展开。不补报价、让步、签字、承诺或发送动作。
- **工作消息/摘要**：按用户要求的长度直接给成稿。精简优先去重、去铺垫；成本差异、限制、争议和执行条件仍须可追溯。不把所有消息都排成正式报告。
- **翻译/双语**：保留金额、币种、税前税后、期限、责任和条件的强度；术语保持一致。仅在用户要求或受众明确需要时双语，不默认翻译一遍又重复解释一遍。

## 写作与排版

专业、直接，必要细节可长，简单动作可短。用具体判断和事实替代泛泛价值词。删掉没有业务信息的“综上所述”“全面赋能”等铺垫时，要保留有效论证。没有数据就缩小主张，不用华丽语言替代研究。

Word 文件使用真实标题样式、段落、列表和表格，保留引用、脚注、交叉引用与修订；不把文档导出成图片再塞回 DOCX。结构调整要检查目录和引用关联。表格确有对照价值时使用，正文不机械表格化。

## 完成标准

交付可直接使用的正文或用户所需 DOCX；改文件附关键改动与未核实项。使用 [审核清单](references/checklist.md) 的适用项检查。未能验证分页、字体、域刷新或实际编辑能力时明确说明，不将未完成检查报告为通过。

## 共用编辑标准

完整规则只维护一份，见 [共用编辑标准](references/common/editing-core.md)，两个 skill 共用同一份，改动只改那一份。执行时先读共用文件，再按本 skill 的专属章节工作。

不可动摇的五条（摘要，与共用文件一致，不替代全文）：

- 已有材料默认保留式精修：保留页面数量与顺序、主要对象、数据、品牌和必要的信息密度。
- 事实、推断、建议、预测分开写；没有证据不补造数字、来源和结论。
- 去 AI 味只改善表达和论证，不承诺改变检测分数，不伪装作者身份。
- 截图、PDF、预览图不能冒充原生可编辑文件；未验证的检查写“未验证”，不要写成通过。
- 大词列表是识别提示，不是替换词典；专业概念确有必要时保留。
