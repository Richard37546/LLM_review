# Question Bank｜自测题库（按难度）

## Level 1｜基础必答（建议 1 分钟内能答）
1) Token 是什么？Embedding 是什么？两者区别？  
2) Transformer 一层通常有哪些组件？  
3) Q/K/V 分别是什么？在注意力里分别起什么作用？  
4) Self-attention 的 Q/K/V 来源是什么？Cross-attention 呢？  
5) 为什么要除以 sqrt(d_k)（scaled dot-product）？  
6) causal mask 是什么？为什么必须有？  
7) Prefill 是什么？Decode 是什么？  
8) KV cache 缓存什么？为什么按层缓存？  
9) RMSNorm 与 LayerNorm 的区别是什么？  
10) RoPE 的目标是什么？为什么作用在 q/k？  
11) FFN 是什么？它在 Transformer 里负责什么？  
12) SwiGLU 的门控是什么意思？为什么更强？代价是什么？

## Level 2｜推理性能与权衡（建议 2–3 分钟内能答）
13) Prefill 与 Decode 的慢点分别在哪里？  
14) 为什么 KV cache 对 decode 更关键？  
15) 上下文长度变长为什么会影响显存与速度？  
16) 什么是吞吐（throughput）？什么是延迟（latency）？  
17) 平均延迟与尾延迟（P95/P99）的区别是什么？  
18) MoE 为什么能“参数更大但计算可控”？  
19) 什么是专家塌缩？为什么要负载均衡？  
20) MoE 为什么可能让尾延迟更差？

## Level 3｜打穿式（建议作为模拟面试题）
21) 你如何用最少的话解释：prefill → KV cache → decode 的关系？  
22) 如果模型生成很慢，你会先从“prompt 很长”还是“输出很长”判断？为什么？  
23) 如果显存不够，你会先缩短上下文还是降低 batch？各有什么副作用？  
24) MLA 想解决什么问题？它与 MQA/GQA 的区别是什么？  
25) MoE 的工程风险有哪些？为什么“平均快”不代表“体验快”？