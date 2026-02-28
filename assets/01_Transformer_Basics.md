# 01 Transformer Basics｜全局地图
## 你现在应该记住什么
1) Transformer 是一种处理“序列数据”的神经网络结构，核心由 **Attention（注意力）+ FFN（前馈网络）** 反复堆叠组成。  
2) Transformer 的关键优势是：可以并行处理序列（训练更高效），并能建模长距离依赖。  
3) LLM（大语言模型）通常使用 **Decoder-only Transformer**：带因果掩码（causal mask）的自回归生成结构。

---

## 专有名词解释
- **序列（sequence）**：按顺序排列的数据，例如一句话里的词、一个时间序列的采样点。  
- **Token（词元）**：模型处理的最小单位。它可能是一个字、一个词、一个子词（subword），由分词器（tokenizer）决定。  
- **Embedding（嵌入）**：把离散的 token id 映射成连续向量的过程/结果。  
- **Hidden state（隐藏状态）**：网络中间层的向量表示，表示“当前 token 的上下文信息”。  
- **Layer（层）**：Transformer 通常堆叠很多层，每层都有注意力与 FFN。  
- **Residual（残差连接）**：把输入直接加到输出上（output = f(x) + x），让深层网络更容易训练。  
- **Normalization（归一化）**：稳定训练的操作，如 LayerNorm/RMSNorm。  
- **FFN（Feed-Forward Network）**：对每个 token 的向量独立做的两层 MLP（多层感知机）变换。  
- **Attention（注意力）**：让一个 token 根据“相关性”从其它 token 汇聚信息的机制。

---

## Transformer 在做什么（直觉）
想象你读一句话时，某个词的含义需要依赖其它词。Transformer 的注意力机制就是在学习：
- 对于每个 token，“我应该关注哪些位置的信息？”
- 关注的强度有多大？
然后把相关信息汇总成新的表示。

---

## Transformer 的一层通常包含什么
一个典型的 Transformer 层（简化理解）包含：
1) **Attention（注意力）模块**：让 token 彼此交互，汇聚上下文信息。  
2) **FFN（前馈网络）模块**：对每个 token 的表示做更强的非线性变换。  
3) **Residual + Norm**：每个模块外面常配残差连接和归一化，以稳定训练。

> 你可以把 Attention 理解为“信息交换”，把 FFN 理解为“本地加工”。

---

## 三种常见 Transformer 结构
### 1) Encoder-only（编码器）
- 用于理解类任务（例如分类、抽取），可以同时看整句（双向）。
- 常见代表：BERT（概念上）。

### 2) Encoder-Decoder（编码器-解码器）
- Encoder 读输入，Decoder 生成输出。
- 常用于翻译、摘要（概念上）。

### 3) Decoder-only（解码器）
- 只用 Decoder，并通过因果掩码实现自回归生成：每一步只能看过去。
- 常见代表：GPT/LLaMA（概念上）。

---

## 常见误区
1) 以为 Transformer 只用于文本：实际上它是序列建模结构，也可用于语音、时间序列等。  
2) 以为 Attention 就是全部：FFN 同样重要，很多计算量来自 FFN。  
3) 以为“层数越多一定越好”：更深可能更强，但也更难训练、更耗资源。

---

## 自测题（5 题）
1) Token 和 embedding 的区别是什么？  
2) Transformer 一层里主要由哪些组件构成？  
3) Residual（残差连接）为什么有用？  
4) Encoder-only 和 Decoder-only 的关键差异是什么？  
5) 为什么 Decoder-only 需要因果掩码（causal mask）？