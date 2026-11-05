---
name: business-ppt-editor
description: 制作和修改商业PPT，整合资料研究、业务分析、大纲、逐页文案、图表表达、去AI味与交付审核；保留原页、数据和可编辑对象。适用于汽车、金融、市场研究及BP，不处理纯Word或邮件写作。
metadata:
  version: "0.1.2"
---

# 商业 PPT 工作台

一个入口完成商业演示材料的需求理解、资料研究、分析、大纲、逐页文案、图表表达、文件编辑和质量检查。使用本包内部参考文件即可，不要求用户再调用研究、文案、排版或去 AI 味技能。宿主已有的文件或检索工具可以按需使用；技能本身不提供文件引擎。

## 参考文件路由：按任务读，不全读

| 任务 | 先读 | 需要时再读 | 默认不读 |
| --- | --- | --- | --- |
| 诊断问题 | references/checklist.md | references/examples.md | references/research.md（除非诊断涉及数据来源） |
| 保留式精修已有 PPT | references/file-preservation.md、references/checklist.md | references/preferences.md、references/domains.md、references/examples.md | references/research.md |
| 从零起草 / 研究型 PPT | references/research.md、references/domains.md、references/preferences.md、references/examples.md | references/file-preservation.md | 无 |
| 只有文字 / 截图 | references/examples.md | references/checklist.md | references/file-preservation.md（拿到原文件后再读） |

共用编辑标准见 [共用编辑标准](references/common/editing-core.md)，任何任务都要先读它。

## 本 skill 不接的任务

- 单纯写商务邮件、工作消息或整理会议纪要：用 business-word-editor。
- 只改 Word 报告、排版 DOCX、校对长篇文字：用 business-word-editor。
- 代码调试、图片生成、视频制作、纯设计排版（没有文案或证据任务）：不属于本 skill，另找对应工具。

混合任务先拆成 PPT 和 Word 两步，或由用户指定以一个入口为主，另一个只给文本建议，不要两个入口同时改同一份材料。


## 识别任务后直接推进

- **从零做**：确认现有上下文中的读者、要支持的决定、材料和约束。以证据组织叙事，再写逐页内容；不默认套“背景—痛点—解决方案—赋能—展望”。商业计划按实际业务说明收入来源、关键假设、资源需求和风险。
- **研究型**：先读 [资料研究与业务分析](references/research.md)。把来源、计算、结论和建议连起来；需要当前数据时实际查源。按问题选取品牌/车型/月份/地域等维度，不先画版式再找数字填满。
- **改已有 PPT**：默认在原页面和原对象内精修。系列材料先找用户确认版，沿用其版式和信息结构；有实际问题再局部修复。跨页大改按用户授权执行。
- **只有文字/截图**：完成可以可靠完成的逐页文案或修改方案，明确无法从截图保证原生对象可编辑；不声称输出了尚未生成的 PPTX。

按当前任务读取 [PPT 与文字示例](references/examples.md)、[场景规则](references/domains.md) 和 [用户偏好](references/preferences.md)。需要文件交付时读取 [文件保护](references/file-preservation.md)，使用 [审核清单](references/checklist.md) 验收。

## 页面组织

让每页承担明确任务，但不强制每页只有一句话。高密度对照表、成本瀑布、研究方法和风险页按其用途保留细节。商业故事要能说明“发生了什么、为什么与当前决策有关、还缺什么”，不必在每页重复这三句话。

有数据再选择图表。比较、趋势、构成、流程、测算对应的表达应由信息关系决定。保留原图可读性足够时不换图；不能为视觉效果夸大坐标变化、删掉不利样本或把预测画成已发生。

报告型 PPT 的正文细节可以比演讲稿多；演讲型 PPT 可把已授权移出的解释放在备注或附录。页数、字体、配色和卡片数量按材料与参考稿决定，不硬编码审美。

## 完成标准

用户要文件时交实际可用的 PPTX；工具受限时交逐页内容、位置和待执行修改，并准确说明状态。预览图是辅助验收材料，不能替代可编辑文件。用户只要大纲/文案时不额外造整稿。交付时简述关键改动、待核项和实际完成的检查。

## 共用编辑标准

完整规则只维护一份，见 [共用编辑标准](references/common/editing-core.md)，两个 skill 共用同一份，改动只改那一份。执行时先读共用文件，再按本 skill 的专属章节工作。

不可动摇的五条（摘要，与共用文件一致，不替代全文）：

- 已有材料默认保留式精修：保留页面数量与顺序、主要对象、数据、品牌和必要的信息密度。
- 事实、推断、建议、预测分开写；没有证据不补造数字、来源和结论。
- 去 AI 味只改善表达和论证，不承诺改变检测分数，不伪装作者身份。
- 截图、PDF、预览图不能冒充原生可编辑文件；未验证的检查写“未验证”，不要写成通过。
- 大词列表是识别提示，不是替换词典；专业概念确有必要时保留。
