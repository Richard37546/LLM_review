# Mock Interview｜Inference & Performance + Fine-Tuning & Alignment（小白友好版）

> 说明：这是一份“面试官提问顺序脚本”。你可以自己对着答，也可以让别人照着问你。

---

## Part A｜Inference & Performance

## 0) 开场（候选人 30 秒）
请用 30 秒解释：
1) Prefill 是什么？  
2) Decode 是什么？  
3) KV cache 缓存什么？它为什么能让 decode 更快？代价是什么？

---

## 1) 追问：Prefill vs Decode
1) 长 prompt 和长输出分别主要影响哪一段？为什么？  
2) Prefill 更像吞吐问题，Decode 更像延迟问题，这句话怎么理解？  
3) 为什么很多代码里看不到 prefill 这个词？

---

## 2) 追问：KV cache
1) KV cache 为什么“按层缓存”？为什么不能只存一份？  
2) KV cache 越大一定越慢吗？（提示：显存与带宽压力）  
3) 如果显存不够，通常有哪些策略？它们各自的副作用是什么？

---

## 3) 追问：常见架构名词（理解力）
1) RMSNorm 和 LayerNorm 的区别是什么？（是否减均值）  
2) RoPE 的目标是什么？为什么作用在 q/k？  
3) SwiGLU 的“门控”是什么意思？为什么可能更强？代价是什么？

---

## 4) 追问：MoE 与 MLA（扩展题）
1) MoE 为什么能“参数很大但计算可控”？  
2) 什么是专家塌缩？负载均衡在解决什么？  
3) MLA 想解决什么问题？它和 MQA/GQA 的区别是什么？

---

## 5) 收尾（总结能力）
请用 20 秒总结：
- 你认为“长上下文推理慢”的主要原因有哪些？  
- 你会优先解释哪两个概念来让别人快速理解？（建议：Prefill/Decode + KV cache）

---

## Part B｜Fine-Tuning & Alignment

## 6) 开场（候选人 30–45 秒）
请用 30–45 秒解释：
1) LoRA 是什么？  
2) QLoRA 比 LoRA 多做了什么？  
3) 为什么说 LoRA / QLoRA 不是训练目标，而是训练实现方式？

---

## 7) 追问：LoRA / QLoRA
1) 为什么会有 LoRA？它相对全参数微调解决了什么问题？  
2) LoRA 为什么叫 low-rank？  
3) 标准 LoRA 训练时，原模型参数会不会更新？  
4) 为什么很多实践喜欢先把 LoRA 加在 q/v 上？  
5) 为什么不能说“LoRA 只能作用在 q/v”？  
6) QLoRA 为什么更省显存？  
7) 为什么不能把 QLoRA 说成“直接训练 4-bit 底模”？

---

## 8) 追问：强化学习基础
1) 强化学习和监督学习最本质的区别是什么？  
2) agent、state、action、reward、policy 分别是什么？  
3) 为什么 RL 优化的是长期累计回报，而不是单步 reward？  
4) value 和 policy 分别是什么？  
5) advantage 的本质是什么？

---

## 9) 追问：Policy Gradient / PPO
1) 为什么 REINFORCE 不够？它最大的问题是什么？  
2) 为什么要引入 baseline？  
3) Actor 和 Critic 分别做什么？  
4) PPO 和普通 policy gradient 的关键区别是什么？  
5) PPO 的 clip 本质上在防什么？  
6) 为什么 PPO 特别强调“稳定更新”？

---

## 10) 追问：RLHF
1) 为什么 SFT 之后还会有 RLHF？  
2) RLHF 的三阶段分别是什么？  
3) Reward Model 的训练数据长什么样？为什么常用 pairwise preference？  
4) Reward Model 和真实人类偏好是什么关系？  
5) 为什么 RLHF 里要有 KL 惩罚和 reference model？  
6) reward hacking 是什么？为什么它是 RLHF 的风险之一？

---

## 11) 追问：DPO
1) 为什么在 RLHF 之后还会出现 DPO？  
2) DPO 和 RLHF 的目标一样吗？最大的区别是什么？  
3) 为什么说 DPO 不需要“显式 reward model”，但又不能说它和 reward 完全没关系？  
4) 为什么 DPO 通常还需要一个 reference model？  
5) DPO 和 SFT 的区别是什么？  
6) 为什么很多人觉得 DPO 比 PPO 更简单、更稳？  
7) 如果面试官问“DPO 算不算强化学习”，你会怎么回答更稳？

---

## 12) 收尾（整条链路复述）
请你用 1–2 分钟从头讲一遍：

- 预训练在干什么  
- 为什么需要 SFT  
- LoRA / QLoRA 在整条链里处于什么位置  
- RLHF 在解决什么问题  
- DPO 为什么会出现  
- 这些方法在项目实践里该怎么组合使用

---

## 13) 最后一问（项目衔接）
如果你做一个领域任务项目，目标是：
- 学会特定标签体系  
- 输出格式要稳定  
- 显存资源有限

请你解释：
1) 为什么这更像一个 SFT 问题，而不是 RLHF 问题？  
2) 你为什么可能选择 LoRA 或 QLoRA？  
3) 如果以后任务变成“让回答更符合人类偏好”，你会怎么考虑 DPO / RLHF？
