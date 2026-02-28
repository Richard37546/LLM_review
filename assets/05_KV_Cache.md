# 05 KV Cache｜缓存什么、在哪层、快在哪、代价是什么

## 你现在应该记住什么
1) KV cache 缓存的是 **注意力（attention）里的 K（Key）和 V（Value）**，并且是“历史 token”的 K/V。  
2) KV cache 是 **按层缓存**：每一层 self-attention 都有自己的 cache。  
3) 它能让 decode 更快，因为生成新 token 时不需要重复计算历史 token 的 K/V；代价是显存随上下文长度增长。

---

## 专有名词解释
- **Cache（缓存）**：把计算过的结果保存下来，后面复用，以减少重复计算。  
- **Context length（上下文长度）**：当前输入序列的 token 数（prompt + 已生成 token）。  
- **Layer（层）**：Transformer 堆叠的层数，每层都有 attention。  
- **Head（注意力头）**：多头注意力里的一个头。多个头并行计算注意力。  
- **Memory / VRAM（显存）**：GPU 上的内存，用于存模型参数和中间结果。

---

## KV cache 缓存的是什么张量
在 self-attention 中，每一层都会为每个 token 计算 K 和 V。  
KV cache 保存的是：
- 这层里，历史 token 的 K（Key 向量集合）
- 这层里，历史 token 的 V（Value 向量集合）

随着生成进行，历史 token 越来越多，所以缓存也越来越大。

---

## KV cache 缓存在哪里
重要结论：**每一层 self-attention 都有自己的 KV cache**。

原因很直观：
- 第 1 层的 K/V 和第 10 层的 K/V 不一样（它们来自不同层的表示和不同权重），不能混用；
- 因此必须按层保存。

---

## 为什么能加速（重点理解）
在 decode 阶段，每生成一个新 token：
- 如果没有 KV cache：你需要把“所有历史 token”重新跑一遍，重新算它们的 K/V；
- 有 KV cache：历史 token 的 K/V 已经算过并保存了，只需要算“新 token 的 K/V”，然后与历史 cache 拼起来做注意力。

所以 KV cache 的核心价值是：
- **避免重复计算历史部分**（特别是长上下文时收益很大）。

---

## 代价与权衡
KV cache 带来的代价主要是：
- 显存占用随上下文长度增长（越长越大）；
- 显存压力大时，可能影响速度（因为带宽/搬运更重，或者发生内存不足）。

因此在工程实践里经常会看到：
- 限制最大上下文长度；
- 控制生成长度；
- 使用更省 cache 的注意力变体（例如 MQA/GQA/MLA 等概念会在后面讲）。

---

## 常见误区
1) 以为 cache 缓存的是“模型输出”：实际上缓存的是每层 attention 的 K/V。  
2) 以为 cache 只在某一层：实际上是每层都有。  
3) 以为 cache 只影响速度：它同时影响显存和可支持的上下文长度。

---

## 自测题（8 题）
1) KV cache 缓存的是什么？  
2) 为什么说 KV cache “按层缓存”？  
3) KV cache 对 prefill 和 decode 哪个更关键？为什么？  
4) 没有 KV cache 时，decode 为什么会更慢？  
5) 为什么上下文越长，KV cache 越大？  
6) KV cache 的主要代价是什么？  
7) 限制上下文长度能缓解什么问题？  
8) 用一句话解释 KV cache 的价值。