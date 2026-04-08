# CS/AI 论文结构模板

## 目录

- 会议论文结构
- 期刊论文结构
- Workshop/短论文结构
- 各节写作要点

---

## 会议论文结构（标准8-9页）

典型 CS 顶会论文结构（如 CVPR, NeurIPS, ICML, AAAI, ACL）：

```
1. Abstract
2. Introduction
3. Related Work
4. Method / Approach
5. Experiments
   5.1 Experimental Setup
   5.2 Main Results
   5.3 Ablation Studies
6. Conclusion
[References]
[Appendix / Supplementary]
```

### 变体说明

- **Method+Experiments 合并**: 短论文或 empirical 论文可能将 Method 和 Experiments 合并
- **Preliminaries 独立节**: 理论性论文常在 Method 前增加 Preliminaries / Background
- **多条实验节**: 部分论文将 Experiments 拆分为 Quantitative / Qualitative / Analysis 等
- **Discussion 节**: 部分论文在 Conclusion 前增加 Discussion 讨论局限性

---

## 期刊论文结构（IEEE Trans / JMLR 等）

```
1. Abstract
2. Introduction
3. Related Work / Literature Review
4. Problem Formulation / Preliminaries
5. Proposed Method
6. Experiments
   6.1 Datasets and Metrics
   6.2 Comparison with State-of-the-Art
   6.3 Ablation Studies
   6.4 Computational Analysis
7. Discussion / Limitations
8. Conclusion
[References]
[Appendix]
```

期刊论文通常比会议论文更详细，可包含更多实验变体和理论分析。

---

## Workshop/短论文结构（2-4页）

```
1. Abstract
2. Introduction (含 Related Work)
3. Method
4. Experiments
5. Conclusion
[References]
```

短论文精简紧凑，Introduction 中嵌入 Related Work，Experiments 通常只含主要结果。

---

## 各节写作要点

### Abstract

- 150-250词（会议），150-300词（期刊）
- 结构：背景问题 → 现有方法不足 → 本文方法 → 核心贡献 → 关键结果
- 避免：过度展开、细节公式、引用文献编号（部分会议允许）
- **务必包含量化结果**

### Introduction

- 1.5-2页（会议），2-3页（期刊）
- 段落结构（4-6段）：
  1. 宏观背景与研究问题的重要性
  2. 现有方法的局限（2-3段，逐步聚焦）
  3. 本文方法的直觉与动机
  4. 核心贡献（以编号列表呈现）：
     - 贡献1: ...
     - 贡献2: ...
     - 贡献3: ...
- **最后一句话概述论文结构**（如 "The rest of this paper is organized as follows..."）
- 避免在 Introduction 出现过多技术细节

### Related Work

- 0.5-1页（会议），1-2页（期刊）
- 组织方式：
  - **按主题分组**: 将相关工作按子领域/方法类别分组
  - **按时间线**: 展示方法演进
  - **按方法类型**: 传统方法 vs 深度学习方法 vs 本文方法
- 每段结构：领域概述 → 代表方法 → 与本文方法的区别
- **结尾段**: 明确指出本文与所有相关工作的区别和改进
- 常见错误：简单罗列而不分析，缺少与本文方法的对比

### Method / Approach

- 2-3页（会议），3-5页（期刊）
- 结构建议：
  1. 问题定义 / 符号说明
  2. 方法整体架构（先给 overview 再展开）
  3. 各模块详细描述
  4. 训练目标 / 优化方式
  5. 推理方式（如有特殊设计）
- **关键原则**：
  - 先用文字/图示说明直觉，再给公式
  - 每个模块说明输入输出
  - 架构图是必需品，不是可选项

### Experiments

- 1.5-2.5页（会议），3-5页（期刊）
- 子节组织：
  - **Setup**: 数据集、评估指标、实现细节（学习率、batch size、硬件）
  - **Main Results**: 与 SOTA 的定量对比（表格为主）
  - **Ablation Studies**: 验证各模块有效性
  - Analysis（可选）: 定性分析、错误分析、效率分析
- 表格规范：
  - 最佳结果加粗，次优加下划线
  - 标注 * 表示本文结果
  - 行列对齐，指标一致的列放在一起
- 图表规范：
  - 消融实验用柱状图或表格
  - 定性结果用对比图（before/after, ours vs others）
  - 收敛曲线、trade-off 图用折线图

### Conclusion

- 0.5页
- 结构：总结贡献 → 关键发现 → 局限性 → 未来工作
- **必须承认局限性**（审稿人非常看重）
- 未来工作1-2个具体方向即可

### Appendix / Supplementary

- 无页数限制的补充材料
- 内容：额外实验、推导证明、更多可视化、实现细节
- 格式：与正文一致，编号独立