---
name: "academic-paper-writer"
description: "基于研究概要 Markdown 起草 CS/AI 论文的 skill。默认流程是先解析用户提供的研究概要，再生成大纲，确认后输出完整论文草稿、占位符清单、假设清单，以及可选的候选参考文献列表。优先避免编造实验结果和参考文献，图表与缺失细节统一用占位符保留。触发词：写论文、论文写作、academic writing、paper writing、draft paper、paper draft、write a paper。"
---

# Academic Paper Writer

这个 skill 适用于以下场景：

- 用户已经有一份研究概要 Markdown，希望将其扩展为论文草稿。
- 目标是快速获得结构完整、语气学术化、可继续手工补全的 CS/AI 论文初稿。
- 图、表、部分实验结果、部分文献可能暂时缺失，允许先保留占位符。

这个 skill **优先服务于 empirical CS/AI paper 和 early draft**。对于理论论文、survey、position paper、复现实验报告，也可使用，但需要根据论文类型调整结构，不能机械套用经验论文模板。

## 核心原则

- **以研究概要为中心**：主输入是用户提供的研究概要 `.md`，不是在线检索结果。
- **先结构，后正文**：默认先生成大纲，确认后再生成完整草稿。
- **缺什么就标什么**：缺图、缺表、缺结果、缺文献、缺方法细节时，明确留下占位符。
- **不编造证据**：不得虚构实验指标、参考文献、作者、年份、venue、DOI、arXiv 编号。
- **风格适配是增强项**：若用户给出目标会议/期刊，则做简短风格适配；若没给出，则使用通用 CS/AI 论文风格。

## 推荐输入格式

优先让用户提供结构化研究概要 Markdown。推荐字段如下：

```md
# 标题 / 暂定标题

## 问题定义 / 研究动机

## 方法 / 核心思路

## 贡献点

## 实验设置

## 已有结果

## 已有图表

## 目标会议 / 期刊（可选）

## 写作语言（可选）

## 用户已提供参考文献（可选）
```

如果用户提供的概要不完整：

- 只追问**阻塞写作**的关键缺口。
- 非阻塞缺口直接保留占位符，不阻塞写作流程。

## 默认工作流

### Step 1: 解析研究概要 Markdown

读取并整理用户提供的研究概要，识别：

- 已知信息：题目、任务、方法、贡献、实验设置、已有结果、已有图表、参考文献
- 缺失但阻塞的信息：例如论文主题都无法判断、方法核心机制完全缺失
- 缺失但不阻塞的信息：例如图表、部分对比结果、方法细节、参考文献

### Step 2: 确定写作模式与风格

默认写作模式为：**先大纲后全文**

- 若提供目标会议/期刊，则使用 `web` 检索官方规则，整理一个简短 `Style Brief`
- 若未提供目标会议/期刊，则使用通用 CS/AI 论文风格
- 若未明确语言：
  - 国际会议/期刊默认英文
  - 国内中文期刊默认中文
  - 都未明确时，默认英文

### Step 3: 生成大纲

根据研究概要与可选的 `Style Brief` 生成大纲：

- 每节写明目标、核心论点、预计包含的材料
- 明确标出需要后续补充的内容位置
- 对非 empirical 论文，按论文类型调整结构，不强行加入 ablation、架构图、SOTA 对比等内容

大纲确认前，不直接生成最终全文。

### Step 4: 生成完整论文草稿

在用户确认大纲后，一次性生成完整草稿。正文遵循以下规则：

- 只使用用户已提供的事实、结果、图表信息
- 缺失内容一律用占位符保留
- 缺失结果时，允许写“摘要草稿”或“实验节草稿”，但不得生成虚构数值
- 缺失参考文献时，允许写引用占位符，但不得编造真实论文

### Step 5: 输出补充清单

除论文草稿外，还要输出：

- `Placeholder Checklist`
- `Assumptions Made`
- `Candidate References`（可选）

## 轻量引用策略

默认不做本地文献库管理，不创建 `references/` 目录，不生成 `index.md`，不组织 PDF。

引用策略如下：

1. **用户已提供参考文献**
   - 可直接写入正文引用。
   - 若格式不统一，可在审校阶段统一整理。

2. **在线检索得到的参考文献**
   - 只作为候选文献，默认不直接写入正文的确定性引用。
   - 每条候选必须附：
     - `title`
     - `authors`
     - `venue`
     - `year`
     - `source link`
     - `VERIFIED` 或 `UNVERIFIED`
   - 若未完成核验，只能出现在 `Candidate References` 列表中。

3. **正文中的缺失引用**
   - 用 `[REF_NEEDED: claim/topic]` 标记。
   - 不得为了让段落“看起来完整”而编造论文。

## 占位符规范

当论文所需信息尚未提供时，统一使用以下占位符：

- **图片**: `[FIGURE: 描述 | 建议尺寸 | 来源说明]`
- **表格**: `[TABLE: 描述 | 所需字段 | 来源说明]`
- **实验结果**: `[RESULT: 描述 | 所需指标 | 对比方法列表]`
- **待补引用**: `[REF_NEEDED: claim/topic]`
- **待补方法细节**: `[METHOD_DETAIL_NEEDED: 描述]`
- **待补数据集细节**: `[DATASET_DETAIL_NEEDED: 描述]`

示例：

- `[FIGURE: 模型整体架构图 | 单栏宽度 | 用户后续补充架构设计图]`
- `[TABLE: 主结果对比表 | Method, Dataset, Metric, Score | 用户后续补充实验数据]`
- `[RESULT: 消融实验结果 | Accuracy, F1, Inference Time | Full model, w/o module A, w/o module B]`
- `[REF_NEEDED: transformer-based baseline for this task]`
- `[METHOD_DETAIL_NEEDED: training objective for the consistency branch]`
- `[DATASET_DETAIL_NEEDED: train/val/test split and preprocessing pipeline]`

## 最终输出格式

默认最终输出按以下结构组织：

1. `Outline`
2. `Paper Draft`
3. `Placeholder Checklist`
4. `Assumptions Made`
5. `Candidate References`（可选）

## 适用边界

这个 skill 可以帮助起草论文，但不能替代：

- 真实实验结果的提供
- 图表设计与制作
- 参考文献的最终人工核验
- 目标会议/期刊最新投稿规则的最终确认

如果用户要求“像正式投稿稿件一样完整”，但又没有提供结果、图表或参考文献，应明确说明当前只能生成**带占位符的草稿**，不能伪造缺失内容。

## Resources

### references/

- **paper-structure.md**: 条件化的论文结构建议与各节写作要点
- **writing-guidelines.md**: 目标会议/期刊风格适配与证据优先级指南
- **reference-library.md**: 轻量候选参考文献、核验状态与引用占位策略
