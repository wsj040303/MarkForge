# MarkForge

![MarkForge 标识](assets/logo.png)

MarkForge 是一个面向 Codex 的 Markdown 文档优化 Skill，用于在明确边界内整理中文 Markdown 内容。该 Skill 强调保留标题编号、保护代码块与示例内容，并通过三档强度控制改写范围，适合讲义、教程、项目材料与长文档整编场景。

## 核心能力

- 修正错别字、病句、术语不统一与 Markdown 排版问题
- 在基本不改变原意的前提下统一章节内部结构
- 在明确允许的情况下，对内容单薄或冗余的小节进行编辑性增强
- 将正文统一为正式书面语，适配教程、讲义和方案文档
- 默认保留 `2.1.1`、`8.5.3` 等显式编号标题

## 三档优化强度

### Level 1

仅进行表层校正：

- 错别字、漏字、重复字
- 病句与明显不通顺的句子
- 标点、空格、术语写法与大小写不统一
- 标题、列表、表格、代码块的明显排版问题

该等级不调整章节顺序、不重组段落逻辑、不增删实质性内容。

### Level 2

在 Level 1 基础上进行结构整编：

- 统一失衡的小节结构
- 拆分过长段落，合并过碎段落
- 优化讲述顺序与说明结构
- 在需要时套用稳定的小节模板，但不实质改变原意

该等级不主动补充新的知识点，也不进行明显扩写。

### Level 3

在 Level 2 基础上进行编辑性增强：

- 为内容单薄的小节补充必要说明
- 对冗余小节进行压缩
- 增加最小示例、微案例或配置示例
- 将资料堆叠式表述改为更清晰的教学型表述

该等级仍以保持文档核心原意与章节用途不变为前提。

## 仓库结构

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── md-edge-cases.md
│   ├── style-rules.md
│   └── templates.md
└── assets/
    └── logo.png
```

## 在 Codex 中安装

Codex 会从 `~/.codex/skills/<skill-name>` 加载本地 Skill。本项目的稳定运行名为 `markdown-doc-polisher`。

### 方式一：直接克隆到 Skill 目录

```bash
git clone https://github.com/wsj040303/MarkForge.git ~/.codex/skills/markdown-doc-polisher
```

### 方式二：手动复制到本地 Skill 目录

```bash
mkdir -p ~/.codex/skills
cp -R /path/to/MarkForge ~/.codex/skills/markdown-doc-polisher
```

安装完成后建议重启 Codex，以便重新加载 Skill。

## 使用方式

典型调用方式如下：

```text
Use $markdown-doc-polisher to refine this Markdown document at level 2 while preserving heading numbering, formal tone, and core meaning.
```

若用户未指定强度等级，该 Skill 会先询问采用 `1`、`2`、`3` 中的哪一档，再进入编辑流程。

## 关键约束

- 保留原文中的显式编号标题
- 代码块、Prompt、JSON、YAML、命令示例、样例表格默认视为受保护示例
- 正文应保持正式书面语，不使用第二人称或聊天式表达
- 不得超出所选强度等级允许的改写边界

## 参考文件

- `references/style-rules.md`：正式书面语规范
- `references/templates.md`：Level 2 与 Level 3 的常用整编模板
- `references/md-edge-cases.md`：编号标题、代码块、表格、图片、引用块等边界处理规则

## 贡献方式

贡献说明见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 开源许可

本项目采用 [MIT License](LICENSE)。
