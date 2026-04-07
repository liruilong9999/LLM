# 附录：术语表、缩写表与公式索引

这个附录是全套教程的“速查手册”。当你在别的章节里遇到陌生术语、忘记某个缩写含义、想快速回看某条公式时，可以先回到这里。

## 统一记号

本教程默认使用下面这组记号：

| 记号 | 含义 |
| --- | --- |
| $x$ | 一个输入样本，常常表示一段文本或一个 token 序列 |
| $y$ | 目标输出，可能是标签，也可能是下一个 token |
| $t$ | 序列中的时间步或位置索引 |
| $d$ | 向量维度（dimension，向量有多少个数） |
| $d_{model}$ | 模型隐藏维度，也就是 Transformer 中主通道的维度 |
| $d_k$ | Key（键，用来和 Query 做匹配的向量）的维度 |
| $d_v$ | Value（值，被加权聚合的信息向量）的维度 |
| $n$ | 序列长度，例如一句话被分成多少个 token |
| $V$ | 词表大小（vocabulary size，可用 token 的总数量） |
| $Q, K, V$ | Query、Key、Value，注意力机制的三组向量 |
| $W$ | 权重矩阵 |
| $b$ | 偏置向量 |
| $\hat{y}$ | 模型预测值 |
| $L$ | 损失函数（loss function，衡量预测与真实差距的函数） |

## 常见缩写

| 缩写 | 全称 | 解释 |
| --- | --- | --- |
| LLM | Large Language Model | 大语言模型 |
| NLP | Natural Language Processing | 自然语言处理 |
| LM | Language Model | 语言模型，预测词或 token 序列概率的模型 |
| Token | Token | 模型处理的最小文本单位 |
| BPE | Byte Pair Encoding | 字节对编码，一种子词分词方法 |
| RNN | Recurrent Neural Network | 循环神经网络，按顺序处理序列 |
| LSTM | Long Short-Term Memory | 一种带门控结构的 RNN |
| GRU | Gated Recurrent Unit | 另一种较简化的门控 RNN |
| MLP | Multi-Layer Perceptron | 多层感知机，常用于前馈层 |
| FFN | Feed-Forward Network | 前馈网络，Transformer 中逐位置处理的两层线性网络 |
| MHA | Multi-Head Attention | 多头注意力 |
| PE | Positional Encoding | 位置编码，为 token 注入顺序信息 |
| EOS | End Of Sequence | 序列结束 token |
| BOS | Beginning Of Sequence | 序列开始 token |
| PAD | Padding | 补齐 token，用于对齐不同长度序列 |
| CLS | Classification Token | 分类任务常用的特殊 token |
| MLM | Masked Language Modeling | 掩码语言建模，BERT 常用训练目标 |
| CLM | Causal Language Modeling | 因果语言建模，只预测后面的 token |
| SFT | Supervised Fine-Tuning | 监督微调 |
| RLHF | Reinforcement Learning from Human Feedback | 基于人类反馈的强化学习 |
| DPO | Direct Preference Optimization | 直接偏好优化 |
| RAG | Retrieval-Augmented Generation | 检索增强生成 |
| LoRA | Low-Rank Adaptation | 低秩适配微调 |
| QLoRA | Quantized Low-Rank Adaptation | 结合量化的 LoRA 微调 |
| KV Cache | Key-Value Cache | 推理时缓存注意力中的 Key/Value 以提速 |
| MoE | Mixture of Experts | 混合专家架构 |
| API | Application Programming Interface | 应用程序编程接口 |
| GPU | Graphics Processing Unit | 图形处理器，擅长并行计算 |
| CPU | Central Processing Unit | 中央处理器 |
| FLOPs | Floating Point Operations | 浮点运算次数 |

## 关键术语

### LLM

LLM（大语言模型）是通过在大规模文本上训练得到的模型，它的核心能力是学习“给定前文，后文出现什么更合理”。当模型参数足够大、数据足够多、训练足够充分时，它不仅能做续写，还会表现出总结、问答、翻译、代码生成等能力。

### Tokenizer

Tokenizer（分词器）负责把原始文本转成 token id（整数编号），并在模型输出后把 token id 还原成文本。它看起来像“预处理模块”，实际上对模型效果影响很大，因为模型看到的不是原始文字，而是 tokenizer 切出来的 token 序列。

### Embedding

Embedding（嵌入）是把离散对象映射到连续向量空间的方法。对于 token 来说，embedding 层会把一个整数 id 变成一个浮点向量，这样神经网络才能对文本做数学计算。

### Attention

Attention（注意力机制）是一种动态选择信息的机制。它会根据当前 token 的需求，给序列中其他 token 分配不同权重，从而聚合最相关的信息。

### Self-Attention

Self-Attention（自注意力）是指 Query、Key、Value 都来自同一段输入序列的注意力。直观地说，就是句子中的每个位置都在看同一句话里的其他位置。

### Transformer

Transformer（基于注意力机制处理序列的神经网络架构）用自注意力替代了传统 RNN 的顺序传播路径，因此更擅长并行训练，也更容易捕捉长距离依赖。

### Pretraining

Pretraining（预训练）是在海量通用文本上训练模型，让模型先获得广泛语言知识。可以把它理解成“先打基础”。

### Fine-Tuning

Fine-Tuning（微调）是在已有预训练模型基础上，用特定任务或特定风格的数据继续训练，让模型更适应具体场景。

### Alignment

Alignment（对齐）指让模型输出更符合人类偏好、规则和使用场景的过程。它不仅关注“会不会答”，还关注“答得是否安全、是否有帮助、是否像人想要的方式”。

### Quantization

Quantization（量化）是把原本高精度的权重或激活值，转换成更低精度表示的方法。它能减少显存和内存占用，常用于本地部署。

## 常用公式索引

### 线性变换

$$
y = Wx + b
$$

解释：把输入向量 $x$ 经过权重矩阵 $W$ 和偏置 $b$ 映射到新的向量空间。这是神经网络里最基础的计算。

### Softmax

$$
\text{softmax}(z_i) = \frac{e^{z_i}}{\sum_j e^{z_j}}
$$

解释：把一组任意实数变成总和为 1 的概率分布。

### 交叉熵损失

$$
L = -\sum_i y_i \log \hat{y}_i
$$

解释：衡量预测分布 $\hat{y}$ 与真实分布 $y$ 的差异。分类任务和语言模型训练里非常常见。

### 缩放点积注意力

$$
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V
$$

解释：先用 $QK^T$ 算相似度，再除以 $\sqrt{d_k}$ 做缩放，经过 softmax 得到权重，最后用权重去加权求和 $V$。

### 位置编码

$$
PE(pos, 2i) = \sin\left(\frac{pos}{10000^{2i/d_{model}}}\right)
$$

$$
PE(pos, 2i+1) = \cos\left(\frac{pos}{10000^{2i/d_{model}}}\right)
$$

解释：把位置信息编码成不同频率的正弦和余弦，让模型知道 token 的顺序。

### LayerNorm

$$
\text{LayerNorm}(x) = \gamma \frac{x - \mu}{\sqrt{\sigma^2 + \epsilon}} + \beta
$$

解释：对单个样本的特征维做归一化，帮助训练更稳定。

## 模型家族速查

| 家族 | 典型代表 | 主要结构 | 更擅长什么 |
| --- | --- | --- | --- |
| Encoder-only | BERT | 只用编码器 | 分类、抽取、句向量 |
| Decoder-only | GPT、LLaMA | 只用解码器 | 文本生成、对话、代码生成 |
| Encoder-Decoder | T5、BART | 编码器加解码器 | 翻译、摘要、条件生成 |
| MoE | Mixtral、Switch Transformer | 多专家路由 | 更高参数规模下的计算效率 |

## 建议搭配阅读

- 忘了公式：回看本附录，再去 [docs/06-Transformer核心公式详解.md](docs/06-Transformer核心公式详解.md)。
- 忘了架构差异：去 [docs/07-主流LLM架构谱系.md](docs/07-主流LLM架构谱系.md)。
- 忘了 tokenizer 过程：去 [docs/03-文本表示与分词器.md](docs/03-文本表示与分词器.md) 和 [docs/08-从零实现Tokenizer.md](docs/08-从零实现Tokenizer.md)。
- 忘了训练和对齐流程：去 [docs/10-预训练、微调与对齐.md](docs/10-预训练、微调与对齐.md)。
- 忘了部署工具区别：去 [docs/13-本地部署与服务化.md](docs/13-本地部署与服务化.md)。
