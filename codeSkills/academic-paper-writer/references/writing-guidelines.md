# 写作风格适配指南

## 目录

- Web 风格检索 Checklist
- 学术写作最佳实践
- 中英双语写作注意事项
- 常见 CS/AI 会议/期刊风格速查

---

## Web 风格检索 Checklist

当确认目标会议/期刊后，使用 `webfetch` 搜索检索以下信息：

### 必检项

- [ ] **投稿指南**: 搜索 `{会议名} {年份} call for papers` 或 `{期刊名} author guidelines`
- [ ] **格式模板**: 搜索 `{会议名} latex template` 或 `{期刊名} template`
- [ ] **页数限制**: 确认正文页数和附录页数
- [ ] **匿名要求**: 是否要求双盲审稿（需匿名化自我引用）
- [ ] **提交格式**: PDF only / LaTeX source / 其他

### 进阶检索

- [ ] **近期最佳论文**: 搜索 `{会议名} {年份} best paper` 学习获奖论文写作风格
- [ ] **领域同类论文**: 搜索 `site:{会议网站/会议proceedings} {关键方法词}` 查看同类论文的写法
- [ ] **审稿指南**: 搜索 `{会议名} reviewer guidelines` 了解审稿人关注要点
- [ ] **常见拒稿原因**: 搜索 `{会议名} common rejection reasons` 了解需要避免的问题

### 风格要点提取

从检索到的论文中提取：
1. **Abstract 风格**: 是否包含量化结果？篇幅？
2. **Introduction 段落数**: 典型几段？贡献列表格式？
3. **Related Work 位置**: 独立节 vs 嵌入 Introduction？
4. **实验组织**: 子节划分方式？表格格式？用什么数据集？
5. **图表密度**: 每页平均几个图/表？
6. **语言风格**: 正式程度？是否使用第一人称？被动语态比例？

---

## 学术写作最佳实践

### 通用原则

- **清晰优先**: 句子简洁，一段一主题
- **逻辑链条**: 每段首句是主题句，后文论证
- **量化表述**: 用具体数字替代模糊描述（"improves by 3.2%" 而非 "significantly improves"）
- **适度引用**: 关键主张有文献支撑，但不堆砌引用

### 段落结构

- 段首: 主题句（本段要说什么）
- 段中: 论据、分析、对比
- 段尾: 小结或过渡到下一段
- 每段 5-8 句为宜

### 过渡词使用

- **递进**: Furthermore, Moreover, In addition
- **转折**: However, Nevertheless, On the contrary
- **因果**: Therefore, Consequently, As a result
- **举例**: For instance, Specifically, To illustrate
- **总结**: In summary, To summarize, Overall

### 避免事项

- 冗长从句嵌套
- 模糊量化词（"a lot", "very", "really"）
- 同义反复表达
- 过度被动语态（适当使用主动语态更清晰）
- 悬垂修饰语

---

## 中英双语写作注意事项

### 英文写作常见问题

| 问题 | 错误示例 | 正确示例 |
|------|----------|----------|
| 冠词缺失 | We propose novel method. | We propose **a** novel method. |
| 可数名词复数 | This approach handle various task. | This approach handle**s** various task**s**. |
| 时态混乱 | We evaluated results and show that... | We evaluat**ed** results and show**ed** that... |
| 主谓一致 | The results shows... | The results show... |
| 介词错误 | experiment on three datasets | experiments **on** three datasets |
| 连词冗余 | Although..., but... | Although..., **[去掉but]**... |

### 英文论文时态规范

- **Introduction/Related Work**: 一般现在时（"Previous methods focus on..."）
- **Method 描述**: 一般现在时（"Our method consists of..."）
- **Experiments**: 过去时（"We conducted experiments..."）或一般现在时（"Table 1 shows..."）
- **Conclusion**: 一般现在时（"Our method achieves..."）

### 中文写作注意事项

- 学术中文避免口语化表达
- 使用"本文""本研究"而非"我们"（部分场合）
- 技术术语首次出现时标注英文原词
- 图表说明可以用中英双语

### 语言切换判断

- 目标为国际会议/期刊 → 英文写作
- 目标为国内中文期刊 → 中文写作，术语附英文
- 根据目标会议/期刊的官方语言决定

---

## 常见 CS/AI 会议/期刊风格速查

| 会议/期刊 | 典型页数 | 匿名审稿 | 模板 | Related Work 位置 | 特点 |
|-----------|----------|----------|------|--------------------|------|
| CVPR | 8+2 appendix | 是 | LaTeX | 独立节 | 重视可视化和定性分析 |
| NeurIPS | 9+appendix | 是 | LaTeX | 独立节 | 理论严谨性，重视 ablation |
| ICML | 8+appendix | 是 | LaTeX | 独立节 | 理论+实验并重 |
| ICLR | 9+appendix | 是 | LaTeX | Introduction 或独立节 | 重视理论洞察 |
| ACL | 8+appendix | 是 | LaTeX | 独立节 | 强调语言学动机 |
| AAAI | 8 | 是 | LaTeX | 独立节 | 广泛AI主题，表述清晰直白 |
| IEEE Trans | 12-15 | 否 | LaTeX/Word | 独立节长篇综述 | 详细实验和讨论 |
| JMLR | 无限制 | 否 | LaTeX | 独立节长篇综述 | 理论证明充分 |

> 注意：以上为概括性信息，实际以目标会议/期刊官方指南为准。务必在 Step 3 中进行 web 检索确认。