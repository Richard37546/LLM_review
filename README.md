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

## 如何使用（每天 10 分钟）
1. 先看 `assets/00_Index.md`，根据自己的目标选一条路线
2. 每天读 1 个主题（约 5–10 分钟）
3. 做该页末尾的自测题（约 2–5 分钟）
4. 面试前只看每页顶部的“你现在应该记住什么”与自测题答案

## 内容地图（v0.2）
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

## 自测与模拟面试
- 题库：`drills/question_bank.md`
- 模拟面试脚本：`drills/mock_interviews/inference_perf.md`

## 后续会持续更新