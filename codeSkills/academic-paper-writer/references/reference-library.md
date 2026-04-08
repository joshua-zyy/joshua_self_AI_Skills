# 参考文献库构建指南

## 目录

- 检索策略
- 本地 PDF 组织规范
- 索引文件格式
- BibTeX 格式参考
- 引用格式适配

---

## 检索策略

### 关键词提取

从用户的研究概要中提取以下类型的关键词：

1. **核心方法词**: 研究方法/模型的专有名称（如 "transformer", "contrastive learning"）
2. **任务词**: 研究任务名称（如 "object detection", "sentiment analysis"）
3. **领域词**: 应用领域（如 "medical imaging", "autonomous driving"）
4. **技术词**: 关键技术组件（如 "attention mechanism", "graph neural network"）

组合搜索公式：`(核心方法词 OR 技术词) AND 任务词 AND 领域词`

### 搜索渠道

按优先级排列：

1. **目标会议/期刊**: `site:openreview.net {关键词}` 或 `site:proceedings.mlr.press {关键词}`
2. **Google Scholar**: `"{论文名}" {作者}` 或 `{关键词} survey`
3. **arXiv**: `"{关键词}" site:arxiv.org`
4. **Semantic Scholar**: 搜索关键方法词，按引用数排序
5. **DBLP**: 搜索特定作者或会议的论文列表

### 文献筛选标准

- **必引**: 目标会议/期刊近3年的相关论文
- **必引**: 领域内奠基性/开创性论文（高被引）
- **必引**: 直接对比的方法（SOTA baseline）的原论文
- **推荐**: 综述性论文（如近2年的 survey）
- **推荐**: 与本文方法最相似的2-3篇同期论文
- **避免**: 过于陈旧（>10年除非是奠基论文）、低引用且不直接相关的论文

---

## 本地 PDF 组织规范

### 目录结构

在论文项目目录下创建：

```
{paper-project}/
├── paper.md                    # 论文正文
├── references/                 # 参考文献库
│   ├── index.md                # 文献索引文件
│   ├── vaswani2017_attention.pdf
│   ├── devlin2019_bert.pdf
│   └── he2016_resnet.pdf
├── figures/                    # 论文图片
└── tables/                    # 论文表格数据
```

### PDF 命名规范

格式: `{第一作者姓氏}{年份}_{核心关键词}.pdf`

规则：
- 作者姓氏全小写
- 年份4位数字
- 关键词用简短英文，下划线分隔
- 多作者同名时添加首字母区分
- 示例：
  - `vaswani2017_attention.pdf`
  - `devlin2019_bert.pdf`
  - `he2016_resnet.pdf`
  - `brown2020_gpt3.pdf`
  - `zhang2018_attention_a.pdf` vs `zhang2020_attention_b.pdf`

---

## 索引文件格式

`references/index.md` 格式：

```markdown
# 参考文献索引

> 最后更新: {日期}
> 共 {N} 篇文献

## [1] {论文标题}

- **作者**: {作者列表}
- **年份**: {年份}
- **来源**: {会议/期刊名} {年份}
- **核心贡献**: {1句话概括}
- **与本文关系**: {说明本文与该文献的关系}
- **本地路径**: references/{文件名}.pdf
- **BibTeX Key**: {作者姓氏}{年份}

---
```

### 索引分组

当文献数量超过15篇时，建议分组：

```markdown
# 参考文献索引

## 1. 核心方法相关

### [1] Attention Is All You Need
...

## 2. 实验基线方法

### [5] ...
...

## 3. 领域背景

### [10] ...
...
```

---

## BibTeX 格式参考

### 常见条目类型

| 类型 | 用途 | 必填字段 |
|------|------|----------|
| `@inproceedings` | 会议论文 | author, title, booktitle, year |
| `@article` | 期刊论文 | author, title, journal, volume, number, pages, year |
| `@misc` | 预印本(arXiv) | author, title, year, eprint, archiveprefix |
| `@phdthesis` | 博士论文 | author, title, school, year |
| `@www` | 网页 | author, title, url, year |

### BibTeX 示例

```bibtex
@inproceedings{vaswani2017attention,
  author    = {Vaswani, Ashish and Shazeer, Noam and Parmar, Niki and Uszkoreit, Jakob and Jones, Llion and Gomez, Aidan N. and Kaiser, {\L}ukasz and Polosukhin, Illia},
  title     = {Attention Is All You Need},
  booktitle = {Advances in Neural Information Processing Systems},
  year      = {2017},
  volume    = {30}
}

@article{devlin2019bert,
  author    = {Devlin, Jacob and Chang, Ming-Wei and Lee, Kenton and Toutanova, Kristina},
  title     = {{BERT}: Pre-training of Deep Bidirectional Transformers for Language Understanding},
  journal   = {Journal of Machine Learning Research},
  volume    = {20},
  pages     = {1--4},
  year      = {2019}
}

@misc{brown2020gpt3,
  author    = {Brown, Tom and Mann, Benjamin and Ryder, Nick and Subbiah, Melanie and others},
  title     = {Language Models are Few-Shot Learners},
  year      = {2020},
  eprint    = {2005.14165},
  archivePrefix = {arXiv}
}
```

---

## 引用格式适配

### 文内引用格式

| 风格 | 格式 | 示例 |
|------|------|------|
| 数字编号 | `[1]` | Recent methods [1] show that... |
| 作者-年份 | `(Author, Year)` | Recent methods (Vaswani et al., 2017) show that... |
| APA | `(Author, Year)` | (Vaswani et al., 2017) |
| IEEE | `[1]` | Recent methods [1] show that... |

常见 CS 顶会使用格式：
- **NeurIPS/ICML/ICLR**: 数字编号 `[1]`
- **CVPR/ECCV/ICCV**: 数字编号 `[1]`
- **ACL/EMNLP**: 作者-年份 `(Author, Year)`
- **IEEE Trans**: 数字编号 `[1]`

### 引用语句模板

**支持型**:
- "Recent studies [1, 2] have demonstrated that..."
- "Inspired by [3], we propose..."
- "Following [4], we adopt..."

**对比型**:
- "Unlike [5], which requires..., our method..."
- "While [6] focuses on..., we extend..."
- "[7] achieves X, but suffers from Y. Our method addresses this by..."

**奠基型**:
- "The seminal work of [8] introduced..."
- "[9] pioneered the approach of..."