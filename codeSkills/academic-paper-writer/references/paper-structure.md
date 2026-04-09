# CS/AI 论文结构建议

## 使用原则

本文件提供的是**默认建议**，不是跨所有论文类型都成立的硬规则。

- 对 empirical method paper，可优先使用标准实验论文结构。
- 对理论论文、survey、position paper、复现实验报告，应按论文类型调整结构。
- 如果研究概要缺失实验结果、图表或方法细节，应保留占位符，不得为了套模板而编造内容。

---

## 1. empirical CS/AI 论文默认结构

典型结构如下：

```text
1. Abstract
2. Introduction
3. Related Work
4. Method / Approach
5. Experiments
   5.1 Experimental Setup
   5.2 Main Results
   5.3 Ablation / Analysis
6. Conclusion
[References]
[Appendix / Supplementary]
```

适用场景：

- 提出新模型、新模块、新训练策略
- 有实验结果与 baseline 对比
- 需要展示方法、实验、分析之间的完整闭环

可选变化：

- 短论文可将 `Related Work` 并入 `Introduction`
- 简短论文可将 `Method` 与 `Experiments` 合并
- 若没有 ablation，可改为 `Analysis` 或完全省略
- 若论文更偏系统实现，可加入 `System Design` 或 `Implementation Details`

---

## 2. 理论论文默认结构

可参考如下结构：

```text
1. Abstract
2. Introduction
3. Background / Preliminaries
4. Problem Formulation
5. Main Theory / Method
6. Theoretical Analysis / Proof Sketch
7. Experiments or Case Study (optional)
8. Conclusion
[References]
[Appendix]
```

说明：

- 不应强行要求架构图、SOTA 对比或消融实验。
- 若存在实验，其角色通常是辅助说明，而不是论文唯一支撑。

---

## 3. Survey / Position / Reproduction 论文提示

- **Survey**: 重点在分类框架、文献脉络、方法比较，不强制要求方法节和实验节。
- **Position Paper**: 重点在问题定义、论证路径、立场边界，不强制要求量化结果。
- **Reproducibility Paper**: 重点在复现设置、偏差来源、失败案例、与原论文差异。

当研究概要明显属于这些类型时，应优先贴合其论证目标，而不是套用 empirical paper 模板。

---

## 4. 各节写作建议

### Abstract

默认建议：

- 交代背景问题、现有不足、本文方法或核心主张、主要发现、意义
- empirical 论文通常应包含量化结果

缺失结果时的降级规则：

- 若用户未提供真实结果，可输出**摘要草稿**
- 摘要草稿中允许使用 `[RESULT: ...]`
- 不得生成未经用户提供的数值、提升幅度或排名表述

### Introduction

默认建议：

- 说明研究问题的重要性与背景
- 说明现有方法的局限
- 引出本文的核心想法
- 列出贡献点

经验性建议而非硬约束：

- empirical 论文常见 4-6 段结构
- 很多论文会在结尾概述后续章节，但这不是必须项
- 若研究概要仍处早期草稿状态，可先弱化“完整贡献列表”的确定语气

### Related Work

默认建议：

- 按主题、方法类别或时间线组织
- 不只罗列文献，还要说明与本文的关系

引用安全规则：

- 没有可靠参考文献时，使用 `[REF_NEEDED: ...]`
- 不得为了让段落完整而编造论文、作者、年份或 venue

### Method / Approach

默认建议：

- 先说明整体思路，再进入模块细节
- 对核心模块说明输入、输出、目标、与已有方法的区别

条件性建议：

- 对 empirical method paper，架构图通常是强烈建议，但不是绝对硬性要求
- 若缺方法细节，可用 `[METHOD_DETAIL_NEEDED: ...]`
- 若缺训练目标、损失函数、推理流程，也应显式占位

### Experiments

默认建议：

- 交代数据集、指标、实现细节
- 展示主结果
- 若适用，再加入 ablation、效率分析、错误分析、定性分析

缺失结果时的降级规则：

- 可以写实验设计与评估计划
- 可以写已有观察，但必须明确哪些是用户已提供事实
- 缺数据集细节时用 `[DATASET_DETAIL_NEEDED: ...]`
- 缺对比结果时用 `[RESULT: ...]` 或 `[TABLE: ...]`

### Conclusion

默认建议：

- 总结工作与主要发现
- 说明局限性
- 给出未来工作方向

注意：

- 承认局限性通常有助于提升论文可信度，但也应与论文成熟度相匹配
- 若当前仍是早期草稿，可把局限性写成“已知限制与待验证点”

### Appendix / Supplementary

可包含：

- 更多实验
- 推导与证明
- 实现细节
- 额外图表

如果目前材料不全，可先标记应补充的附录内容，而不是强行补齐。
