# LLM（Large Language Model，大语言模型）学习仓库

这个仓库用于系统学习大语言模型（LLM, Large Language Model）。目标不是简单收集资料，而是建立一条完整的理解主线：文本如何进入模型，模型如何训练，为什么能生成语言，以及它如何被部署成稳定服务。

## 阅读入口

1. 先读 [LLM学习路线索引](docs/LLM学习路线索引.md)
2. 再读 [LLM从Transformer到训练推理部署](docs/LLM从Transformer到训练推理部署.md)

## 这套材料覆盖什么

- Transformer（以注意力机制为核心的序列建模架构）为什么成为主流
- Token（模型处理的最小离散文本单元）为什么不是“字数”也不是“词数”
- Embedding（把离散编号映射成连续向量的表示层）如何让文本进入模型
- 预训练（Pretraining，在海量语料上学习语言规律）如何塑造基础模型
- 监督微调（SFT, Supervised Fine-Tuning，用标注数据让模型更会按指令回答）
- 推理（Inference，使用已训练参数生成输出）时为什么要逐 Token 生成
- KV Cache（Key-Value Cache，缓存历史注意力键值以加速生成）为什么重要
- 量化（Quantization，把高精度权重压缩成低精度表示）和部署如何影响成本与性能

## 文档结构

- [docs/LLM学习路线索引.md](docs/LLM学习路线索引.md)：按阶段给出学习顺序、目标、完成标准和复习建议
- [docs/LLM从Transformer到训练推理部署.md](docs/LLM从Transformer到训练推理部署.md)：完整主文档，从基础原理讲到训练、推理和部署

## 阅读建议

- 第一次阅读先抓主线，不要一开始陷在细节术语里
- 第二次阅读重点看 Attention（注意力机制）、Token 化、训练目标、推理解码、量化部署
- 每读完一个章节，试着不用原文复述“输入是什么、发生了什么变换、输出为什么合理”

## 适合谁

- 有编程基础，但没有系统学过 LLM 的读者
- 需要搭建完整认知，而不是只想背几个流行术语的读者
- 想继续学习模型训练、推理工程、RAG（Retrieval-Augmented Generation，检索增强生成）或 Agent（能调用工具并执行多步任务的智能体）的人
