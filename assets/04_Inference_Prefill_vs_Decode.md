# 04 Inference｜Prefill vs Decode（推理两阶段）

## 你现在应该记住什么
1) 推理（inference）通常分成两段：Prefill（处理输入 prompt）和 Decode（逐 token 生成）。  
2) Prefill 的核心产物是建立 KV cache（后续生成会复用）。  
3) Prefill 更像“批处理计算”，Decode 更像“逐步等待”，所以优化目标不同：吞吐 vs 每步延迟。

---

## 专有名词解释
- **Inference（推理）**：模型在训练完成后，用来生成/预测的过程。  
- **Prompt（提示词/上下文）**：模型输入的文本（或其它形式输入）内容。  
- **Generation（生成）**：模型输出 token 序列的过程。  
- **Latency（延迟）**：从请求开始到得到结果的时间。  
- **Throughput（吞吐）**：单位时间内处理的 token 数或请求数。  
- **Token-by-token（逐 token）**：一次只生成一个 token，再把它接到上下文继续生成。

---

## Prefill 是什么
Prefill 指：把 prompt（可能包含很多 token）一次性送进模型前向计算：
- 计算出每层注意力需要的中间量（尤其是 K/V）；
- 把这些中间量保存起来，作为后续生成的基础。

你可以把它理解成：
- “先把输入上下文读完，并把后面需要的中间结果准备好”。

---

## Decode 是什么
Decode 指：在 prefill 完成后，开始逐 token 生成：
- 每一步输入“上一步生成的新 token”（或其 embedding/隐藏表示）；
- 模型输出下一个 token 的概率分布；
- 选出下一个 token，再重复。

Decode 的特点是：
- 每生成一个 token 都要等待一次模型计算；
- 因此“每步延迟”非常重要。

---

## Prefill vs Decode：慢点通常在哪里
### Prefill 常见慢点
- prompt 很长（token 数多）；
- 模型本身很大；
- 需要一次性处理很多 token。

Prefill 更像“吞吐问题”：一次算很多 token。

### Decode 常见慢点
- 每个 token 都要跑一次模型；
- 生成 token 数越多，总时间越长；
- 每步延迟会直接影响“你觉得它快不快”。

Decode 更像“交互延迟问题”：每步都要等。

---

## 为什么你可能没见过“prefill”这个词
很多高层接口会把 prefill 和 decode 都封装掉：
- 例如一些库的 `generate()` 调用内部自动完成两阶段；
- 你只看到“输入→输出”，没有看到阶段划分。

在一些推理/服务系统中（serving），日志或指标里会明确区分：
- prompt processing（prefill）
- generation（decode）

---

## 常见误区
1) 以为推理只有“生成”：其实生成之前需要先处理 prompt（prefill）。  
2) 以为优化就是“让模型更快”：要先分清是 prefill 慢还是 decode 慢。  
3) 把“长 prompt”与“长输出”混为一谈：一个影响 prefill，一个影响 decode。

---

## 自测题（6 题）
1) Prefill 做的事情是什么？它的核心产物是什么？  
2) Decode 为什么说“每步延迟敏感”？  
3) 长 prompt 更影响哪一段？长输出更影响哪一段？  
4) 吞吐和延迟的区别是什么？  
5) 为什么有些代码里看不到 prefill？  
6) 用一句话区分 prefill 与 decode。