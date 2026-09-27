# Uncensored LLMs for Offensive Security

Curated list of open-weight uncensored models for authorized red team operations, penetration testing, and security research.

> All data sourced from HuggingFace model cards and official publications. Sep 2026.

---

## Security Fine-tuned Models

### 1. DeepHat V2 (WhiteRabbitNeo)

| Spec | Value |
|------|-------|
| Base Model | Qwen2.5-Coder-7B |
| Parameters | 7B / 32B |
| Context Length | 131K |
| VRAM (Q4_K_M) | ~6 GB |
| Uncensoring Method | SFT on 1.7M offensive/defensive samples |
| Training Data | 1.7M security-specific samples (USENIX Security 2024 workshop) |
| Vision | No |
| Tool Calling | Yes |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/WhiteRabbitNeo](https://huggingface.co/WhiteRabbitNeo)

---

### 2. BugTraceAI-CORE-Apex

| Spec | Value |
|------|-------|
| Base Model | Gemma4-26B MoE |
| Parameters | 26B MoE |
| Context Length | 32K |
| VRAM (Q4_K_M) | ~16 GB |
| Uncensoring Method | SFT on HackerOne Hacktivity 2024-2025 |
| Training Data | HackerOne reports + WAF evasion dataset |
| Vision | No |
| Tool Calling | Yes |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Apex-26b](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Apex-26b)

---

### 3. pentest-v2

| Spec | Value |
|------|-------|
| Base Model | Qwen3-8B |
| Parameters | 8B |
| Context Length | 32K |
| VRAM (Q4_K_M) | ~6 GB |
| Uncensoring Method | LoRA r=4, 2,804 curated samples |
| Training Data | GTFOBins, HackTricks, HackTheBox writeups |
| GTFOBins Accuracy | 100% (vs 25% base model zero-shot) |
| Vision | No |
| Tool Calling | No |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/gewsefa/pentest-v2](https://huggingface.co/gewsefa/pentest-v2)

---

### 4. Qwythos-9B (Empero AI)

| Spec | Value |
|------|-------|
| Base Model | Qwen3.5-9B |
| Parameters | 9B |
| Context Length | 1M |
| VRAM (Q4_K_M) | ~7 GB |
| Uncensoring Method | Post-training on 500M tokens |
| Benchmarks | +34 MMLU, +30 GSM8K vs base (Empero evals) |
| Vision | No |
| Tool Calling | Yes |
| License | Qwen License |

**Download:** [https://huggingface.co/emperorai/Qwythos-9B](https://huggingface.co/emperorai/Qwythos-9B)

---

### 5. VEXT Pentest-7B

| Spec | Value |
|------|-------|
| Base Model | Mistral-7B |
| Parameters | 7B |
| Context Length | 8K |
| VRAM (Q4_K_M) | ~6 GB |
| Uncensoring Method | QLoRA SFT + DPO on pentest traces |
| Training Data | Pentest methodology, tool usage, reporting |
| Vision | No |
| Tool Calling | No |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/vextechnologies/VEXT-Pentest-7B](https://huggingface.co/vextechnologies/VEXT-Pentest-7B)

---

### 6. security-slm-unsloth-1.5b

| Spec | Value |
|------|-------|
| Base Model | Qwen2.5-1.5B |
| Parameters | 1.5B |
| Context Length | 32K |
| VRAM (Q4_K_M) | ~2 GB |
| Uncensoring Method | Unsloth SFT on security Q&A |
| Training Data | Security knowledge base, CTF-style |
| Vision | No |
| Tool Calling | No |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/AbdullahMujtaba/security-slm-unsloth-1.5b](https://huggingface.co/AbdullahMujtaba/security-slm-unsloth-1.5b)

---

## General Abliterated Models

### 7. Qwen3.8-27B-Uncensored-OrcaRouter (chimingw GGUF)

| Spec | Value |
|------|-------|
| Base Model | Qwen3.8-27B |
| Parameters | 27B dense |
| Context Length | 262K |
| VRAM (Q4_K_M) | ~18 GB |
| Uncensoring Method | Abliteration (131 matrices, Arditi et al. 2024) |
| Intelligence Index | 52 (Artificial Analysis) |
| Vision | Yes |
| Tool Calling | Yes |
| License | Apache 2.0 |
| HF Downloads | 230K+ |
| HF Likes | 257+ |

**Download (GGUF):** [https://huggingface.co/chimingw/Qwen3.8-27B-Uncensored-OrcaRouter-GGUF](https://huggingface.co/chimingw/Qwen3.8-27B-Uncensored-OrcaRouter-GGUF)  
**Download (base):** [https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored)

---

### 8. GLM-5.3-Flash-Uncensored-FP8

| Spec | Value |
|------|-------|
| Base Model | GLM-5.3-Flash |
| Parameters | 320B total / 18B active (288 routed experts, MoE) |
| Context Length | 1M |
| VRAM (FP8) | ~80 GB+ (multi-GPU) |
| Uncensoring Method | Abliteration (layer 22/45, deeper refusal mechanism) |
| Compliance Rate | 82.8% (OrcaRouter testing) |
| MTP | Yes (Multi-Token Prediction preserved) |
| Vision | Yes + Video |
| Tool Calling | Yes |
| License | MIT |

**Download:** [https://huggingface.co/orcarouter/GLM-5.3-Flash-Uncensored-FP8](https://huggingface.co/orcarouter/GLM-5.3-Flash-Uncensored-FP8)

---

### 9. huihui-ai/Qwen3.5-27B-abliterated

| Spec | Value |
|------|-------|
| Base Model | Qwen3.5-27B |
| Parameters | 27B dense |
| Context Length | 128K |
| VRAM (Q4_K_M) | ~18 GB |
| Uncensoring Method | Abliteration |
| Vision | No |
| Tool Calling | Yes |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/huihui-ai/Qwen3.5-27B-abliterated](https://huggingface.co/huihui-ai/Qwen3.5-27B-abliterated)

---

### 10. huihui-ai/Qwen2.5-Coder-32B-Instruct-abliterated

| Spec | Value |
|------|-------|
| Base Model | Qwen2.5-Coder-32B-Instruct |
| Parameters | 32B dense |
| Context Length | 128K |
| VRAM (Q4_K_M) | ~20 GB |
| Uncensoring Method | Abliteration |
| Vision | No |
| Tool Calling | No |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/huihui-ai/Qwen2.5-Coder-32B-Instruct-abliterated](https://huggingface.co/huihui-ai/Qwen2.5-Coder-32B-Instruct-abliterated)

---

### 11. Qwen3.8-27B-Cyber-agentic

| Spec | Value |
|------|-------|
| Base Model | Qwen3.8-27B |
| Parameters | 27B dense |
| Context Length | 262K |
| VRAM (Q4_K_M) | ~18 GB |
| Uncensoring Method | Abliteration + cyber agentic fine-tune |
| Vision | Yes |
| Tool Calling | Yes |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) (base, community abliterated variants available)

---

### 12. HIDra-30B-A3B (huihui-ai/Qwen3-Coder-30B-A3B-abliterated)

| Spec | Value |
|------|-------|
| Base Model | Qwen3-Coder-30B-A3B |
| Parameters | 30B total / 3B active (MoE) |
| Context Length | 128K |
| VRAM (Q4_K_M) | ~20 GB |
| Uncensoring Method | Abliteration |
| Vision | No |
| Tool Calling | Yes |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/huihui-ai/Qwen3-Coder-30B-A3B-abliterated](https://huggingface.co/huihui-ai/Qwen3-Coder-30B-A3B-abliterated)

---

### 13. qwen25_UNCENSORED_03-C

| Spec | Value |
|------|-------|
| Base Model | Qwen2.5-based |
| Parameters | ~7B |
| Context Length | 32K |
| VRAM (Q4_K_M) | ~6 GB |
| Uncensoring Method | Progressive fine-tuning (multi-stage) |
| Vision | No |
| Tool Calling | No |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/models?search=qwen25_UNCENSORED](https://huggingface.co/models?search=qwen25_UNCENSORED)

---

## Legacy / Classic Models

### 14. Dolphin-Llama3-8B (Cognitive Computations)

| Spec | Value |
|------|-------|
| Base Model | Llama 3 8B |
| Parameters | 8B |
| Context Length | 8K |
| VRAM (Q4_K_M) | ~6 GB |
| Uncensoring Method | Data filtering (Dolphin method, Eric Hartford) |
| Training Data | Dolphin dataset (alignment/refusal responses removed) |
| Vision | No |
| Tool Calling | No |
| License | Llama 3 Community |

**Download:** [https://huggingface.co/cognitivecomputations/dolphin-2.9.3-llama-3-8b](https://huggingface.co/cognitivecomputations/dolphin-2.9.3-llama-3-8b)

---

### 15. Wizard-Vicuna-13B-Uncensored (QuixiAI)

| Spec | Value |
|------|-------|
| Base Model | LLaMA-13B |
| Parameters | 13B |
| Context Length | 2K |
| VRAM (Q4_K_M) | ~10 GB |
| Uncensoring Method | Data filtering (wizard_vicuna_70k_unfiltered) |
| MMLU | 47.92 (Open LLM Leaderboard) |
| HellaSwag | 81.95 (Open LLM Leaderboard) |
| TruthfulQA | 51.69 (Open LLM Leaderboard) |
| Vision | No |
| Tool Calling | No |
| License | Other |
| HF Likes | 323 |

**Download:** [https://huggingface.co/QuixiAI/Wizard-Vicuna-13B-Uncensored](https://huggingface.co/QuixiAI/Wizard-Vicuna-13B-Uncensored)

---

## Quick Reference

| # | Model | Params | Context | VRAM | Method | Vision | Tools | License |
|---|-------|--------|---------|------|--------|--------|-------|---------|
| 1 | DeepHat V2 | 7B/32B | 131K | ~6 GB | SFT 1.7M samples | No | Yes | Apache 2.0 |
| 2 | BugTrace Apex | 26B MoE | 32K | ~16 GB | SFT HackerOne | No | Yes | Apache 2.0 |
| 3 | pentest-v2 | 8B | 32K | ~6 GB | LoRA 2.8K samples | No | No | Apache 2.0 |
| 4 | Qwythos-9B | 9B | 1M | ~7 GB | Post-train 500M tok | No | Yes | Qwen |
| 5 | VEXT Pentest-7B | 7B | 8K | ~6 GB | QLoRA SFT+DPO | No | No | Apache 2.0 |
| 6 | security-slm-1.5b | 1.5B | 32K | ~2 GB | Unsloth SFT | No | No | Apache 2.0 |
| 7 | Qwen3.8-27B Uncensored | 27B | 262K | ~18 GB | Abliteration 131 mat | Yes | Yes | Apache 2.0 |
| 8 | GLM-5.3-Flash | 320B/18B | 1M | ~80 GB+ | Abliteration | Yes | Yes | MIT |
| 9 | Huihui-Qwen3.5-27B | 27B | 128K | ~18 GB | Abliteration | No | Yes | Apache 2.0 |
| 10 | Qwen2.5-Coder-32B | 32B | 128K | ~20 GB | Abliteration | No | No | Apache 2.0 |
| 11 | Qwen3.8-27B-Cyber | 27B | 262K | ~18 GB | Abliteration+cyber | Yes | Yes | Apache 2.0 |
| 12 | HIDra-30B-A3B | 30B/3B | 128K | ~20 GB | Abliteration | No | Yes | Apache 2.0 |
| 13 | qwen25_UNCENSORED | ~7B | 32K | ~6 GB | Progressive FT | No | No | Apache 2.0 |
| 14 | Dolphin-Llama3 | 8B | 8K | ~6 GB | Data filtering | No | No | Llama 3 |
| 15 | Wizard-Vicuna-13B | 13B | 2K | ~10 GB | Data filtering | No | No | Other |

---

## Glossary

- **Abliteration**: Weight-level intervention (Arditi et al. 2024) that orthogonalizes the refusal direction out of the residual stream, removing alignment constraints without retraining
- **SFT**: Supervised Fine-Tuning on domain-specific data
- **QLoRA**: Quantized Low-Rank Adaptation, memory-efficient fine-tuning
- **DPO**: Direct Preference Optimization
- **MoE**: Mixture of Experts, only a subset of parameters active per token
- **MTP**: Multi-Token Prediction, speculative decoding for faster inference
- **GGUF**: Quantized format for llama.cpp / Ollama deployment
- **FP8**: 8-bit floating point quantization
- **Q4_K_M**: 4-bit quantization with k-quants (medium), good balance of quality/speed

## Deployment Stacks

| Stack | Best For | GPU Required |
|-------|----------|-------------|
| Ollama | Local dev, quick testing | Consumer GPU (6-24 GB) |
| llama.cpp | GGUF models, CPU+GPU hybrid | Flexible |
| vLLM | Production serving, high throughput | Datacenter GPU |
| SGLang | Agentic workflows, structured output | Datacenter GPU |
| Transformers | Research, custom pipelines | Any |

---

## Sources

- HuggingFace model cards (all specifications)
- Open LLM Leaderboard v1 (Wizard-Vicuna benchmarks)
- OrcaRouter release notes (abliteration details, compliance rates)
- WhiteRabbitNeo/Kindo publications (USENIX Security 2024)
- Empero AI model card (Qwythos benchmarks)
- Eric Hartford / Cognitive Computations (Dolphin methodology)
- TrustedSec LLM Attack Benchmark (4,800 runs vs OWASP Juice Shop)
- Reddit r/LocalLLaMA, r/netsec community reports

---

*Joas A. Santos | Red Team Leaders | Sep 2026*  
*For authorized security research and education only.*
