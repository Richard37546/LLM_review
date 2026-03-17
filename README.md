# LLM_review

面向小白的 LLM（大语言模型）基础复习仓库：把常见概念拆成“卡片式”文档，帮助你在短时间内建立清晰、可复述的理解。

本仓库每个主题都遵循类似结构：
- **你现在应该记住什么**（先给结论，避免迷路）
- **专有名词解释**（第一次出现就解释清楚）
- **核心内容**（尽量用直觉 + 必要的公式/步骤）
- **常见误区**
- **自测题**（用来确认你真的懂了）

## 适合谁
- 想系统复习 Transformer / LLM 基础概念的初学者
- 面试前希望把“常见名词”讲清楚的人（不堆术语，追求可复述）
- 对“为什么推理会慢”这类问题感到困惑的人
- 想把 **微调 / 对齐 / LoRA / RLHF / DPO** 也系统串起来的人

## 如何使用（每天 10 分钟）
1. 先看 `assets/00_Index.md`，根据自己的目标选一条路线
2. 每天读 1 个主题（约 5–10 分钟）
3. 做该页末尾的自测题（约 2–5 分钟）
4. 面试前只看每页顶部的“你现在应该记住什么”与自测题答案

## 内容地图（v0.3）
- 入口与路线：`assets/00_Index.md`
- Transformer 总览：`assets/01_Transformer_Basics.md`
- Attention 深入：`assets/02_Attention_DeepDive.md`
- 因果掩码：`assets/03_Causal_Mask.md`
- 推理两阶段：`assets/04_Inference_Prefill_vs_Decode.md`
- KV Cache：`assets/05_KV_Cache.md`
- LLaMA 常见模块：`assets/06_LLaMA_Blocks_RMSNorm_RoPE.md`
- FFN 与 SwiGLU：`assets/07_FFN_SwiGLU.md`
- MoE（混合专家）：`assets/08_MoE_Basics.md`
- MLA（DeepSeek 常见）：`assets/09_MLA_DeepSeek.md`
- LoRA / QLoRA：`assets/10_LoRA_QLoRA.md`
- 强化学习基础：`assets/11_Reinforcement_Learning_Basics.md`
- Policy Gradient / PPO / RLHF：`assets/12_Policy_Gradient_PPO_RLHF.md`
- DPO：`assets/13_DPO.md`
- LLM 对齐总主线：`assets/14_LLM_Alignment_Pipeline.md`

## 自测与模拟面试
- 题库：`drills/question_bank.md`
- 模拟面试脚本：`drills/self_interviews`

目前题库与模拟面试已覆盖两大方向：
1. **Inference & Performance**  
   - Prefill / Decode  
   - KV cache  
   - RoPE / RMSNorm / SwiGLU  
   - MoE / MLA

2. **Fine-Tuning & Alignment**  
   - LoRA / QLoRA  
   - 强化学习基础  
   - PPO / RLHF  
   - DPO  
   - 从预训练到对齐的整条训练链

## 如何复习（推荐路线）
### 路线 A：先打基础，再看推理
1. `01_Transformer_Basics.md`
2. `02_Attention_DeepDive.md`
3. `03_Causal_Mask.md`
4. `04_Inference_Prefill_vs_Decode.md`
5. `05_KV_Cache.md`

### 路线 B：理解主流架构模块
1. `06_LLaMA_Blocks_RMSNorm_RoPE.md`
2. `07_FFN_SwiGLU.md`
3. `08_MoE_Basics.md`
4. `09_MLA_DeepSeek.md`

### 路线 C：补齐微调与对齐
1. `10_LoRA_QLoRA.md`
2. `11_Reinforcement_Learning_Basics.md`
3. `12_Policy_Gradient_PPO_RLHF.md`
4. `13_DPO.md`
5. `14_LLM_Alignment_Pipeline.md`

## 这个仓库最适合怎么用
### 如果你是初学者
先按 `00_Index.md` 选路线，逐页看，重点抓“你现在应该记住什么”。

### 如果你在准备面试
优先看：
- 每页顶部总结
- 每页的“常见误区”
- `drills/question_bank.md`
- `drills/self_interviews`

### 如果你已经做过项目
重点看：
- LoRA / QLoRA
- SFT / RLHF / DPO
- `14_LLM_Alignment_Pipeline.md`

因为这些内容更适合把“项目实践”讲成“有原理支撑的故事”。

## 后续会持续更新
