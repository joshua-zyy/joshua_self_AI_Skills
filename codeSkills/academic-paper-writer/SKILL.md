---
name: "academic-paper-writer"
description: "CS/AI领域学术论文写作辅助skill。根据用户提供的研究概要撰写论文，支持中英双语，自动检索目标期刊/会议风格，在线推荐参考文献并构建本地文献库，缺失材料以占位符标记。触发词：写论文、draft paper、academic writing、论文写作、paper writing、撰写论文、论文辅助、paper draft、write a paper。"
---

# Academic Paper Writer

辅助CS/AI领域学术论文写作。根据研究概要、目标会议/期刊风格，分节交互式撰写论文，在线检索参考文献并构建本地文献库，缺失材料用占位符标记。

## 工作流

### Step 1: 研究内容收集

向用户收集研究概要，包括：
- 研究问题与动机
- 提出的方法/模型
- 核心贡献与创新点
- 实验设计思路（如有）
- 已有的图表、数据、实验结果（如有）

若用户概要不完整，主动追问关键信息，但不要阻塞流程——缺失信息用占位符标记。

### Step 2: 目标确认

向用户确认：
1. **目标期刊/会议**: 名称、年份（如 CVPR 2026, NeurIPS 2025）
2. **写作语言**: 英文 / 中文（根据目标自动建议）
3. **页数限制**: 如 8+2, 9, 无限制等
4. **其他要求**: 匿名审稿、特定模板等

### Step 3: 风格检索

使用 web 搜索目标会议/期刊的：
1. 投稿指南（Call for Papers, Author Guidelines）
2. 格式要求（模板、页数、匿名要求）
3. 近年代表性论文风格（段落结构、Related Work 组织方式、实验呈现方式）

将检索到的风格要点整理为 **Style Brief**，呈现给用户确认。

详细检索方法见 [references/writing-guidelines.md](references/writing-guidelines.md)。

### Step 4: 参考文献库构建

基于研究内容构建参考文献库：

1. **关键词提取**: 从研究概要提取核心方法词、任务词、领域词、技术词
2. **在线检索推荐**: 搜索目标会议/期刊上的相关论文和领域经典论文
3. **呈现推荐列表**: 每篇标注标题、作者、年份、核心贡献、与本文关系
4. **用户确认筛选**: 用户确认保留/排除/补充
5. **生成本地组织方案**:
   - 在论文项目目录下创建 `references/` 文件夹
   - PDF 命名规范: `{第一作者姓氏}{年份}_{关键词}.pdf`（如 `vaswani2017_attention.pdf`）
   - 生成 `references/index.md` 索引文件

详细检索策略、PDF组织规范、索引格式见 [references/reference-library.md](references/reference-library.md)。

### Step 5: 大纲生成

根据 Style Brief 和研究内容生成论文大纲：
1. 参照目标会议/期刊的论文典型结构
2. 每节标注核心内容、关键论点、预计篇幅
3. 标注需要用户提供的材料位置
4. 呈现大纲，与用户确认后进入写作

参见 [references/paper-structure.md](references/paper-structure.md) 了解各类型论文结构。

### Step 6: 分节撰写

按大纲逐节撰写，**每节完成后暂停**，简要呈现该节要点并确认：
- 用户是否满意当前内容
- 是否需要调整
- 确认后继续下一节

撰写过程中的材料处理：
- **已有材料**: 直接引用用户提供的图表、数据、结果
- **缺失材料**: 使用占位符标记（见占位符规范）
- **参考文献**: 使用 Step 4 建立的文献库，按目标格式引用

参见 [references/paper-structure.md](references/paper-structure.md) 了解各节写作要点。
参见 [references/writing-guidelines.md](references/writing-guidelines.md) 了解写作风格适配和双语注意事项。

### Step 7: 审校完善

全局审校：
1. **逻辑连贯性**: 各节之间逻辑是否通顺
2. **占位符清单**: 列出所有占位符，提醒用户补充
3. **风格一致性**: 是否遵循 Style Brief 的风格要求
4. **参考文献**: 格式是否统一、引用是否完整
5. **语言润色**: 根据目标语言进行最终润色

输出最终 Markdown 论文文件和占位符清单。

## 占位符规范

当论文所需材料用户未提供时，使用以下占位符标记：

- **图片**: `[FIGURE: 描述 | 建议尺寸 | 来源说明]`
  - 示例: `[FIGURE: 模型整体架构图 | 单栏宽度 | 用户需提供架构设计图]`

- **表格**: `[TABLE: 描述 | 所需数据列 | 来源说明]`
  - 示例: `[TABLE: 各方法在COCO数据集上的对比结果 | Method, AP, AP50, AP75 | 用户需提供实验数据]`

- **实验结果**: `[RESULT: 描述 | 所需指标 | 对比方法列表]`
  - 示例: `[RESULT: 消融实验结果 | Accuracy, F1, Inference Time | Full model w/o attention, w/o pretrain]`

## 交互协议

- **大纲阶段**: 完整呈现大纲，等待用户确认
- **分节阶段**: 每节完成后简要呈现，等待用户确认
- **审校阶段**: 一次性输出完整审校报告
- **任何阶段用户可中断修改**，从修改点重新继续

## Resources

### references/

- **paper-structure.md**: CS/AI 论文各节结构模板与写作要点
- **writing-guidelines.md**: 目标会议/期刊风格检索方法与写作风格适配指南
- **reference-library.md**: 参考文献检索策略、本地PDF组织规范、索引与BibTeX格式