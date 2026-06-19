---
name: markdown-doc-polisher
description: Optimize Chinese Markdown documents with three controlled intensity levels. Level 1 fixes typos,病句, terminology inconsistency, and Markdown formatting only. Level 2 additionally normalizes uneven section structure and improves exposition without materially changing meaning. Level 3 may also expand thin sections, compress redundant sections, and add or remove supporting content while preserving core intent. Use for lecture notes, project documents, tutorials, and structured Markdown that require formal written tone, preserved heading numbering, protected code blocks, and controlled rewriting boundaries.
---

# Markdown Doc Polisher

用于受约束地优化 Markdown 文档，重点处理以下类型的材料：

- 讲义、教程、学习笔记
- 项目方案、申报材料、说明文档
- 结构较长、章节较多的 Markdown 文档
- 已有标题编号、代码块、表格、图片链接的复杂文档

## Required Inputs

执行前应尽量明确以下输入：

- 文件路径
- 强度等级：`1` / `2` / `3`

如用户未明确强度等级，应优先主动确认，不直接默认采用某一等级。

确认原则如下：

- 若运行环境支持结构化用户输入或选项式提问，应提供 `1 / 2 / 3` 三档供用户选择。
- 若运行环境不支持结构化选项，应使用一条简短澄清问题，请用户明确强度等级。
- 仅在用户明确要求“自行判断”或“按合适强度处理”时，才允许根据任务表述推断等级。

推断时可参考以下信号：

- 明确提到“错别字、病句、排版、格式”时，通常对应 `1`
- 明确提到“统一结构、优化讲述、基本不改原意”时，通常对应 `2`
- 明确提到“补充内容、精简内容、扩写、压缩、增强章节”时，通常对应 `3`

**推荐提问文案：**

若当前需要主动确认强度等级，优先使用如下问法：

`请选择本次 Markdown 文档优化强度：1 仅校正；2 统一结构；3 允许增删内容。`

如需更完整说明，可使用如下版本：

`请选择本次 Markdown 文档优化强度：
1. 仅校正：只修正错别字、病句、术语不统一、Markdown 排版和格式错误，不调整内容结构。
2. 统一结构：在 1 的基础上，允许整理章节内部结构、统一讲述模板、优化叙述顺序，但基本不改变原意，也不主动补充新内容。
3. 深度优化：在 2 的基础上，允许适度增删内容，可为单薄章节补充必要内容，为冗余章节压缩内容，但仍保持整篇文档核心原意不变。`

## Global Rules

无论强度等级如何，均遵循以下规则：

1. 保留原文核心原意，不得擅自改变作者立场、判断或结论。
2. 若原文已有显式编号标题，如 `2.1.1`、`8.5.3`，默认必须保留，不得改为无编号标题。
3. 代码块、Prompt、JSON、表格样例、命令示例默认视为示例内容，不参与正文结构重写。
4. 除非用户明确要求，否则不重写代码块内部内容，只修复明显损坏的 Markdown 包围结构。
5. 正文保持正式书面语，避免第二人称、聊天腔、教程式口语提示语。
6. 术语写法应统一，例如模型名、框架名、协议名、工具名、缩写大小写。
7. 优先保护结构与信息完整性，不以“统一风格”为理由删除有效信息。

## Intensity Levels

### Level 1

仅允许处理以下问题：

- 错别字、漏字、重复字
- 病句、明显不通顺的句子
- 标点、空格、大小写、术语写法不统一
- Markdown 格式错乱
- 标题、列表、表格、代码块的明显排版问题

这一等级适用于“只修文，不动内容”的场景。目标是让文档更干净、更规范，但不改变原有讲述方式和信息组织方式。

禁止操作：

- 改变章节顺序
- 改变标题层级
- 改写段落逻辑
- 增加或删除实质性内容
- 重写示例含义

### Level 2

在 Level 1 基础上，额外允许：

- 统一章节内部结构
- 拆分过长段落，合并过碎段落
- 将杂乱表述整理为更稳定的讲述模板
- 在基本不改原意的前提下重写句子和段落组织方式
- 将格式明显失衡的小节改为统一表达模式

这一等级适用于“文档内容大体没问题，但讲述结构不统一、颗粒度不一致、部分小节很难读”的场景。目标是把文档整理得更像一份结构稳定的讲义、教程或说明文档。

禁止操作：

- 主动引入新的知识点
- 大幅扩写内容
- 删除原本有效的信息
- 擅自改变章节定位

### Level 3

在 Level 2 基础上，额外允许：

- 为明显单薄的章节补充必要内容
- 为明显冗余的章节压缩内容
- 增加最小示例、微案例、配置示例、判断标准
- 将“资料堆叠式”小节改为“教学讲解式”小节
- 删除重复、低价值或明显干扰主线的内容

这一等级适用于“文档不只是需要整理，还需要编辑性增强”的场景。目标不仅是统一结构，还包括补足薄弱章节、压缩冗余段落、增强可读性与教学性。

额外约束：

- 只能围绕原章节主题补充或压缩
- 不得凭空发明与主题无关的新内容
- 不得改变整篇文档的核心定位与用途

## Workflow

### 1. Scan Before Editing

先扫描以下结构特征：

- 标题层级与编号体系
- 代码块边界
- 表格
- 图片
- 引用块
- 链接
- 术语写法
- 明显失衡的章节颗粒度

若文档存在显式编号标题，应先记录编号体系，再开始编辑。

### 2. Lock Allowed Operations

根据强度等级锁定允许动作范围：

- `1` 只校正
- `2` 可整编结构
- `3` 可整编并适度编辑内容

不得越级修改。

若当前尚未获得强度等级，先询问用户，再进入编辑流程；不得在未确认的情况下直接开始处理。

### 3. Edit by Section

按章节或小节分段处理，不对整篇文档一次性整体重写。

处理顺序优先如下：

1. 修复标题、列表、代码块、表格等结构问题
2. 统一术语与语体
3. 优化章节内部组织
4. 仅在 `3` 级时补充或压缩内容

### 4. Normalize Tone

正文应统一为说明文或讲义文体。需要重点清理以下表达：

- “你”“我们”“大家”“同学”
- “先说结论”“如果只记一句话”
- “通俗一点”“可以理解为”“想象成”
- “直接”“快速”“跑起来”等偏口语或教程腔的表达

具体替换规则见 [references/style-rules.md](references/style-rules.md)。

### 5. Apply Section Templates When Needed

仅在 `2`、`3` 级使用模板化整编。常用模板见 [references/templates.md](references/templates.md)。

若某小节原本已经结构清晰，不必强行套模板。

### 6. Final Review

编辑完成后，必须再次检查：

- 标题编号是否保留
- 代码块是否完整
- 表格是否破坏
- 章节原意是否偏移
- 正文是否仍有明显口语化表达
- 是否超出当前强度允许范围

Markdown 边界情况见 [references/md-edge-cases.md](references/md-edge-cases.md)。

## Common Failure Modes

必须主动避免以下问题：

1. 将“排版优化”误做成“内容重写”
2. 删除原有编号体系
3. 将代码块中的 `#`、Prompt、JSON 误判为正文结构
4. 将正文改成聊天腔或问答腔
5. 在 `1`、`2` 级擅自补充知识点
6. 为了统一风格而删除有信息量的原文

## Output Requirements

完成后应说明：

- 本次使用的强度等级
- 修改类型
- 是否保留原编号体系
- 是否涉及结构整编
- 是否涉及补充或压缩内容
- 如有保守假设，应明确说明

## Resource Loading Guide

仅在需要时读取以下参考文件：

- [references/templates.md](references/templates.md)
  用于选择合适的小节模板
- [references/style-rules.md](references/style-rules.md)
  用于统一正式书面语
- [references/md-edge-cases.md](references/md-edge-cases.md)
  用于处理编号、代码块、表格、引用块等边界情况
