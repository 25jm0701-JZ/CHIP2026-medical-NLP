# Transformer NER：临床试验筛选标准解析 中文翻译版

原文题名：Transformer-Based Named Entity Recognition for Parsing Clinical Trial Eligibility Criteria

## 中文题名

基于 Transformer 的命名实体识别用于解析临床试验筛选标准

## 摘要翻译

电子健康记录系统的快速普及，使临床数据能够以电子形式用于研究和下游应用。利用临床数据库自动筛选潜在合格患者，是提高临床试验招募效率的重要需求。

然而，把自由文本筛选标准人工翻译成数据库查询非常耗时、低效。为了支持自动筛选，必须把自由文本筛选标准结构化，并使用受控词表编码成可计算格式。因此，命名实体识别是重要的第一步。

本研究在两个公开的 eligibility criteria 标注语料上评估了四种 Transformer NER 模型，包括 Chia 数据和 Facebook Research 数据。比较的模型包括 BERT、ALBERT、RoBERTa 和 ELECTRA，并比较了不同预训练语料的影响，包括通用英文语料、PubMed 文献、MIMIC-III 临床笔记以及 ClinicalTrials.gov 中的筛选标准。

实验显示，在 MIMIC-III 临床笔记和 eligibility criteria 上预训练的 RoBERTa 表现最好，在 Chia 数据上的严格/宽松 F1 为 0.658/0.798，在 FRD 数据上的严格/宽松 F1 为 0.785/0.916。

## 方法翻译

本文主要研究命名实体识别，也就是从筛选标准文本中找出有意义的医学片段。

模型比较包括：

1. BERT。
2. ALBERT。
3. RoBERTa。
4. ELECTRA。

预训练语料比较包括：

1. 通用英文语料。
2. PubMed 医学文献。
3. MIMIC-III 临床笔记。
4. ClinicalTrials.gov 筛选标准。

研究重点是看哪种模型和预训练语料最适合识别筛选标准中的实体。

## 结果翻译

结果表明，医学领域和临床文本相关的预训练语料对任务有帮助。尤其是同时包含临床笔记和筛选标准文本的预训练模型，在实体识别上表现更好。

不过，作者也指出，较好的 NER 结果只是构建自动筛选管线的第一步。后续仍然需要关系抽取、逻辑解析、概念标准化和可执行查询生成。

## 对 CHIP2026 的启发

这篇文章提醒我们：NER 有用，但不是全部。

CHIP2026 里可以借鉴：

1. 如果时间允许，可用 LLM 或现成医学模型辅助识别实体。
2. 但不要把比赛简化成 NER。
3. 识别出实体后，还必须生成正确 FHIR resources。
4. 代码可运行和格式正确仍然比模型复杂度更重要。

大白话：

> 模型可以帮我们找“病名、检查、手术、数值”，但最后还得靠工程把这些东西放进 FHIR 里。

