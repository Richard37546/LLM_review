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
13) LoRA 是什么？它主要想解决什么问题？  
14) QLoRA 比 LoRA 多做了哪一步？  
15) 强化学习中的 agent、state、action、reward、policy 分别是什么？  
16) RL 和监督学习最本质的区别是什么？  
17) RLHF 的三阶段通常是什么？  
18) DPO 的核心目标是什么？

## Level 2｜推理性能与权衡（建议 2–3 分钟内能答）
19) Prefill 与 Decode 的慢点分别在哪里？  
20) 为什么 KV cache 对 decode 更关键？  
21) 上下文长度变长为什么会影响显存与速度？  
22) 什么是吞吐（throughput）？什么是延迟（latency）？  
23) 平均延迟与尾延迟（P95/P99）的区别是什么？  
24) MoE 为什么能“参数更大但计算可控”？  
25) 什么是专家塌缩？为什么要负载均衡？  
26) MoE 为什么可能让尾延迟更差？  
27) LoRA 为什么叫 low-rank？  
28) 标准 LoRA 训练时，原模型参数会不会更新？  
29) 为什么 LoRA 常见加在 q/v 上，但又不能说“LoRA 只能加在 q/v”？  
30) LoRA 为什么能省显存？  
31) 为什么 QLoRA 比普通 LoRA 更省显存？  
32) PPO 和普通 policy gradient 的关键区别是什么？  
33) Advantage 的本质是什么？为什么它比直接用 return 更稳？  
34) 为什么 RLHF 里要有 KL 惩罚和 reference model？  
35) DPO 为什么通常被认为比 PPO / RLHF 更简单、更稳定？

## Level 3｜打穿式（建议作为模拟面试题）
36) 你如何用最少的话解释：prefill → KV cache → decode 的关系？  
37) 如果模型生成很慢，你会先从“prompt 很长”还是“输出很长”判断？为什么？  
38) 如果显存不够，你会先缩短上下文还是降低 batch？各有什么副作用？  
39) MLA 想解决什么问题？它与 MQA/GQA 的区别是什么？  
40) MoE 的工程风险有哪些？为什么“平均快”不代表“体验快”？  
41) 全参数微调、LoRA、QLoRA 三者的主要区别是什么？  
42) 为什么说 LoRA / QLoRA 是“实现方式层”，而不是“训练目标层”？  
43) 如果一个任务主要是在学领域标签体系和结构化输出，你为什么会优先把它看成 SFT 问题？  
44) 为什么说 RLHF 主要优化的是行为与偏好，而不是主要负责灌知识？  
45) DPO 和 SFT 的核心区别是什么？  
46) 如果面试官问“DPO 算不算强化学习”，你会怎么回答更稳？

## Level 4｜微调与对齐（建议 3–5 分钟内能答）
47) 为什么会有 SFT？它相对预训练多解决了什么问题？  
48) 为什么很多高质量回答问题不适合只用 SFT 解决？  
49) Reward Model 的训练数据长什么样？为什么常用 pairwise preference？  
50) Reward Model 和真实人类偏好是什么关系？  
51) PPO 的 clip 本质上在防什么？  
52) 为什么 REINFORCE 不够，后来还要有 baseline、actor-critic 和 PPO？  
53) RLHF 里的 reward hacking 是什么？为什么会发生？  
54) 为什么说 DPO 不是否定 reward 思想，而是把它“隐式吸收”了？  
55) 为什么 DPO 一般仍然需要 reference model？  
56) RLHF 和 DPO 在工程复杂度、稳定性和可复现性上分别有什么特点？

## Level 5｜综合叙事与项目衔接（建议作为终极口头题）
57) 请你从预训练开始，一口气讲到 SFT、LoRA/QLoRA、RLHF、DPO，说明它们分别解决什么问题。  
58) 如果资源有限，但你要做一个领域任务微调项目，你会如何在全参数微调、LoRA、QLoRA 之间做选择？  
59) 如果任务目标是“输出格式要稳定、标签体系要对齐、结构化结果要准确”，你更倾向用 SFT、DPO 还是 RLHF？为什么？  
60) 如果任务目标是“让回答更符合人类偏好而不是更像唯一标准答案”，为什么 DPO / RLHF 更适合？  
61) LoRA 和 DPO 可以组合吗？为什么？  
62) 你如何向非技术面试官解释：为什么大模型训练不是“一个方法打天下”，而是分成预训练、SFT、偏好对齐、参数高效微调等不同层次？  
63) 如果让你把今天复习的这条线压缩成 1 分钟面试回答，你会怎么组织？
