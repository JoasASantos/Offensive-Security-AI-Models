# Uncensored LLMs for Offensive Security

Curated list of open-weight uncensored models for authorized red team operations, penetration testing, and security research.

> All data sourced from HuggingFace model cards and official publications. Sep 2026.

<img width="4000" height="1568" alt="offsec-benchmark-v3" src="https://github.com/user-attachments/assets/3a0e3514-6805-4cf5-8400-628178df538c" />

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

### 2. BugTraceAI-CORE-Apex (26B)

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

### 3. BugTraceAI-CORE-Ultra (27B)

| Spec | Value |
|------|-------|
| Base Model | Qwen3.6-27B (DavidAU fine-tuned variant) |
| Parameters | 27B dense |
| Context Length | 4K (recommended) |
| VRAM (Q6_K) | ~22-24 GB |
| Uncensoring Method | SFT via Unsloth on bug bounty + CVE data |
| Training Data | 2,541 examples from bug bounty disclosures, CVE writeups, and security research (2024-2026) |
| Specialization | Tooling model: generates Nuclei templates, CVE PoCs, exploit code, pentest scripts |
| Vision | No |
| Tool Calling | Yes |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)

---

### 4. CYBER-FROST-3.8 (Blackfrost-AI)

| Spec | Value |
|------|-------|
| Base Model | Qwen/Qwen3.8-Flash-Next |
| Parameters | ~180B total (512 routed experts, 10 active per token) |
| Context Length | 262K |
| Architecture | Qwen4ExpForConditionalGeneration, 48 transformer blocks, hybrid linear + full attention |
| VRAM | Multi-GPU required (tested on 4x NVIDIA B300 SXM6) |
| Uncensoring Method | Security-domain fine-tuning on proprietary Blackfrost-AI corpus |
| Training Data | Proprietary security corpus: recon, web app security, vuln research, malware analysis, cloud security, threat intel |
| MTP | Yes (1 native MTP layer for speculative decoding) |
| Vision | No |
| Tool Calling | Yes |
| License | Qwen Community License 1.0 |

**Download:** [https://huggingface.co/Blackfrost-AI/CYBER-FROST-3.8-BF16](https://huggingface.co/Blackfrost-AI/CYBER-FROST-3.8-BF16)

---

### 5. CyberPal 2.0 (20B)

| Spec | Value |
|------|-------|
| Base Model | gpt-oss-20b |
| Parameters | ~20B (21B in files) |
| Context Length | 8,192 |
| VRAM (BF16) | ~42 GB |
| Uncensoring Method | SFT on SecKnowledge 2.0 pipeline |
| Training Data | 403K examples via expert-in-the-loop schema steering, multi-step grounding, LLM quality checks |
| Specialization | Defensive: CTI, vuln analysis, detection/mitigation, SOC/IR, AppSec, compliance |
| Vision | No |
| Tool Calling | No |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/cyber-pal-security/CyberPal2.0-20B](https://huggingface.co/cyber-pal-security/CyberPal2.0-20B)

---

### 6. Cyber-Prime 1.1 (2.6B)

| Spec | Value |
|------|-------|
| Base Model | LiquidAI/LFM2-2.6B |
| Parameters | 2.6B (~3B actual) |
| Context Length | N/A (model card does not specify) |
| VRAM (BF16) | ~6 GB |
| Tensor Type | BF16 |
| Uncensoring Method | SFT + RL + reward-guided post-training on 75K cybersecurity rows |
| Training Data | NER repair (~6K), HTTP reasoning w/ CoT (~5K), email phishing (~5K), threat intel summarization (~2K), GHSA/KEV/ATT&CK |
| Operating Modes | Direct mode (classification) + Think mode (chain-of-thought) |
| CyberBench Average | 0.592 F1/Acc (up from 0.501 in v1.0) |
| CyberBench Highlights | NER 0.499, Phishing 0.890, HTTP Attack 0.628 |
| Vision | No |
| Tool Calling | No |
| License | LFM Open License v1.0 |

**Download:** [https://huggingface.co/Akahsizrr/Cyber-Prime-1.1-2.6B](https://huggingface.co/Akahsizrr/Cyber-Prime-1.1-2.6B)

---

### 7. Cyber-Ornith-1.5-9B (DuoNeural / mradermacher)

| Spec | Value |
|------|-------|
| Base Model | ornith-ai/Ornith-1.5-9B (Qwen 3.5 architecture) |
| Parameters | 9B |
| Context Length | 128K (Qwen 3.5 default) |
| VRAM (Q4_K_M) | ~7 GB |
| Uncensoring Method | Obliteration (abliteration variant) |
| Training Data | NousResearch/hermes-function-calling-v1, OpenThoughts3-1.2M, openhands-synthetic-conversations |
| Specialization | Agentic cybersecurity: function-calling, tool-use, reasoning, CLI/terminal automation |
| Format | GGUF (IQ1_S to Q6_K available) |
| Vision | No |
| Tool Calling | Yes |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/mradermacher/Cyber-Ornith-1.5-9B-OBLITERATED-i1-GGUF](https://huggingface.co/mradermacher/Cyber-Ornith-1.5-9B-OBLITERATED-i1-GGUF)

---

### 8. Dolphin3-Cyber-8B (RavichandranJ)

| Spec | Value |
|------|-------|
| Base Model | Dolphin3.0-Llama3.1-8B-abliterated |
| Parameters | 8.03B |
| Context Length | 2,048 (fine-tuned) / 131K (base) |
| VRAM (Q4_K_M) | ~6 GB |
| Uncensoring Method | LoRA rank-16 on abliterated Dolphin3 base |
| Training Data | Cybersecurity-specific: pentest, vuln analysis, exploit dev, incident response |
| Architecture | LlamaForCausalLM, 32 layers, GQA (32 heads, 8 KV heads) |
| Performance | 5 tok/s (CPU) to 55 tok/s (RTX 4060) |
| Vision | No |
| Tool Calling | No |
| License | Llama 3.1 |

**Download:** [https://huggingface.co/RavichandranJ/Dolphin3-Cyber-8B-GGUF](https://huggingface.co/RavichandranJ/Dolphin3-Cyber-8B-GGUF)

---

### 9. Imperum-CybersecurityLLM v1.0

| Spec | Value |
|------|-------|
| Base Model | Qwen/Qwen3.6-35B-A3B |
| Parameters | 34.66B total / ~3B active (MoE, 256 routed experts, 8 active per token) |
| Context Length | 16,384 (recommended 8,192 for resource-constrained) |
| VRAM (Q4_K_M) | ~22 GB |
| Architecture | Qwen3.5-MoE, 40 layers, hybrid linear + full attention |
| Uncensoring Method | SFT across 10+ security domains |
| Training Data | SOC/SIEM operations, detection engineering, DFIR, malware analysis, threat intel, vuln management, cloud/K8s/IAM, OT security, GRC, authorized pentesting |
| Vision | No |
| Tool Calling | Yes |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/IMPERUM/Imperum-CybersecurityLLM-v1.0-GGUF](https://huggingface.co/IMPERUM/Imperum-CybersecurityLLM-v1.0-GGUF)

---

### 10. Lily-Cybersecurity-7B v0.2 (Segolily Labs)

| Spec | Value |
|------|-------|
| Base Model | Mistral-7B-Instruct-v0.2 |
| Parameters | 7B |
| Context Length | 8K |
| VRAM (Q4_K_M) | ~6 GB |
| Uncensoring Method | SFT on 22K cybersecurity pairs |
| Training Data | 22,000 hand-crafted cybersecurity data pairs across 28+ domains: pentesting, malware analysis, IR, cloud security |
| Training Hardware | Single A100, 24h, 5 epochs |
| Vision | No |
| Tool Calling | No |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/segolilylabs/Lily-Cybersecurity-7B-v0.2](https://huggingface.co/segolilylabs/Lily-Cybersecurity-7B-v0.2)

---

### 11. pentest-v2 (gewsefa)

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

### 12. Qwythos-9B (Empero AI)

| Spec | Value |
|------|-------|
| Base Model | Qwen3.5-9B |
| Parameters | 9B |
| Context Length | 1M (YaRN rope-scaling) |
| VRAM (Q4_K_M) | ~7 GB |
| Uncensoring Method | Post-training on 500M+ tokens of Claude Mythos / Claude Fable traces with CoT |
| Benchmarks | +34 MMLU, +30 GSM8K vs base (Empero evals) |
| Native Function Calling | Yes (Qwen3.5 spec) |
| Chain-of-Thought | Always-on `<think>` block |
| Variants | Base (SFT), Claude-Mythos-5-1M-GGUF (Q4_K_M to BF16) |
| Vision | Yes (inherited vision tower) |
| Tool Calling | Yes |
| License | Apache 2.0 |

**Download (base):** [https://huggingface.co/emperorai/Qwythos-9B](https://huggingface.co/emperorai/Qwythos-9B)  
**Download (GGUF):** [https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)

---

### 13. RavenX-CyberAgent (deadbydawn101)

| Spec | Value |
|------|-------|
| Base Model | Qwen/Qwen3.6-35B-A3B |
| Parameters | 36B total / 3B active (MoE) |
| Context Length | 262K (native), 32K tested |
| VRAM (Q4_K_M) | ~24 GB |
| Uncensoring Method | 12-round progressive SFT on 745K+ examples from 110 sources |
| Training Data | Pentest reports, bug bounty data, Claude Mythos reasoning, MITRE ATT&CK, blackhat content |
| Specialization | RATH protocol: Attack Surface, Exploit, Impact, Remediation, Document, Prevent |
| Output Format | CVSS scores, CWE identifiers, MITRE ATT&CK mappings |
| Inference Speed | 89 tok/s generation, 900 tok/s prompt processing |
| Vision | No |
| Tool Calling | Yes |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/deadbydawn101/RavenX-CyberAgent-Qwen3.6-35B-A3B-Opus-4.7-OpenMythos-Pentester-BugHunter-RATH-GGUF](https://huggingface.co/deadbydawn101/RavenX-CyberAgent-Qwen3.6-35B-A3B-Opus-4.7-OpenMythos-Pentester-BugHunter-RATH-GGUF)

---

### 14. REDCELL-26B-A4B (terrorswift)

| Spec | Value |
|------|-------|
| Base Model | Google Gemma 4 26B-A4B (Unsloth fine-tuned) |
| Parameters | 26B total / ~4B active (MoE) |
| Context Length | 262K |
| VRAM (APEX-Mini) | ~12 GB |
| VRAM (Q8_0) | ~26 GB |
| Uncensoring Method | 16-bit LoRA SFT on 6,500 custom instructions |
| Training Data | Cyber threat intelligence, investigative journalism, counter-disinformation, analytical methodology |
| Specialization | OSINT: threat actor attribution, IoC pivoting, geolocation analysis, Admiralty source credibility, vulnerability contextualization |
| APEX Quantization | Domain-weighted imatrix (~70% REDCELL corpus, ~30% general calibration) |
| Vision | No |
| Tool Calling | No |
| License | Apache 2.0 |

**Download:** [https://huggingface.co/terrorswift/REDCELL-26B-A4B-OSINT-Cyber-APEX-GGUF](https://huggingface.co/terrorswift/REDCELL-26B-A4B-OSINT-Cyber-APEX-GGUF)

---

### 15. VEXT Pentest-7B

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

### 16. security-slm-unsloth-1.5b

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

### 17. Qwen3.8-27B-Uncensored-OrcaRouter (chimingw GGUF)

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

### 18. GLM-5.3-Flash-Uncensored-FP8 (OrcaRouter)

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

### 19. GLM-5.3-CYBERSECURITY-FP8 (dealignai)

| Spec | Value |
|------|-------|
| Base Model | zai-org/GLM-5.3 (via JANGQ-AI/GLM-5.3-FP8) |
| Parameters | 753B total (glm_moe_dsa architecture) |
| Context Length | ~131K (practical on 8x H200 w/ TP8) |
| VRAM (FP8) | 8x H200 GPUs with tensor parallelism |
| Architecture | 78 layers, text-only, routed FP8 experts |
| Uncensoring Method | Direct weight modification for offensive-security, red-team, exploit-dev, RE, evasion, phishing, credential-attack, malware-analysis |
| Notes | Not abliteration or LoRA; direct bf16 residual writer editing. Soft refusal on copyright reproduction retained |
| Vision | No (text-only) |
| Tool Calling | Yes |
| License | MIT |

**Download:** [https://huggingface.co/dealignai/GLM-5.3-CYBERSECURITY-FP8](https://huggingface.co/dealignai/GLM-5.3-CYBERSECURITY-FP8)

---

### 20. DeepSeek-V4.1-Flash-Abliterated-Cybersecurity-Unleashed (drowzeys)

| Spec | Value |
|------|-------|
| Base Model | DeepSeek-V4.1-Flash |
| Parameters | MoE (size matches base) |
| Context Length | Matches base DeepSeek-V4.1-Flash |
| Uncensoring Method | Abliteration overlay on layers 10-35 attention projection (wo_b); layers 0-9, 36-39, expert layers, vision components unchanged |
| Format | Modular overlay (not standalone checkpoint): FP8 (~1.1 GB) or EXL3 mul1 K=5 (~651 MB) |
| Deployment | Apply on top of existing quantized base packs (native, EXL3, TR3-Hybrid) |
| GPU Util | <= 0.85 recommended |
| Vision | Yes (preserved) |
| Tool Calling | Yes |
| License | MIT |

**Download:** [https://huggingface.co/drowzeys/DeepSeek-V4.1-Flash-Abliterated-Cybersecurity-Unleashed](https://huggingface.co/drowzeys/DeepSeek-V4.1-Flash-Abliterated-Cybersecurity-Unleashed)

---

### 21. huihui-ai/Qwen3.5-27B-abliterated

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

### 22. huihui-ai/Qwen2.5-Coder-32B-Instruct-abliterated

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

### 23. Qwen3.8-27B-Cyber-agentic

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

### 24. HIDra-30B-A3B (huihui-ai/Qwen3-Coder-30B-A3B-abliterated)

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

### 25. qwen25_UNCENSORED_03-C

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

### 26. Dolphin-Llama3-8B (Cognitive Computations)

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

### 27. Wizard-Vicuna-13B-Uncensored (QuixiAI)

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

## Cloud Providers & Deployment Platforms

### Managed Inference (API Access)

| Provider | Description | Uncensored Models | Pricing | API |
|----------|-------------|-------------------|---------|-----|
| **[OrcaRouter](https://www.orcarouter.ai/)** | AI gateway with adaptive routing across 200+ models. Zero token markup, OpenAI-compatible endpoint. Own abliterated models (Qwen3.8, GLM-5.3). | Yes, hosts own abliterated variants | $0 token markup, BYOK or pay-as-you-go | OpenAI-compatible |
| **[Featherless AI](https://featherless.ai/)** | Serverless LLM hosting, HuggingFace's largest inference provider (6,700+ models). Supports uncensored/abliterated models natively. | Yes, 40K+ models including uncensored | $25/mo (32K ctx) or $50 credits/mo (256K ctx) | OpenAI-compatible |
| **[Together AI](https://www.together.ai/)** | Production inference platform, supports open models including uncensored variants. | Select open models | Pay-per-token | OpenAI-compatible |

### GPU Cloud (Self-Hosted)

| Provider | Description | Best For | GPU Options |
|----------|-------------|----------|-------------|
| **[RunPod](https://www.runpod.io/)** | GPU cloud with serverless and pod options, Docker-based. Quick deploy with Ollama/vLLM templates. | Self-hosting any model, no content restrictions | A100, H100, H200, RTX 4090 |
| **[Vast.ai](https://vast.ai/)** | GPU marketplace, cheapest cloud GPUs. Peer-to-peer rental model. | Budget self-hosting | Consumer to datacenter GPUs |
| **[Lambda](https://lambdalabs.com/)** | On-demand GPU cloud for AI. Enterprise-grade infrastructure. | Production workloads | A100, H100, H200 |

### Local Deployment

| Stack | Description | GPU Required |
|-------|-------------|-------------|
| **[Ollama](https://ollama.ai/)** | One-command local LLM deployment. Easiest setup for GGUF models. | Consumer GPU (6-24 GB) |
| **[llama.cpp](https://github.com/ggerganov/llama.cpp)** | C/C++ inference engine for GGUF. CPU+GPU hybrid, maximum hardware flexibility. | Flexible (CPU-only possible) |
| **[vLLM](https://github.com/vllm-project/vllm)** | High-throughput inference engine. PagedAttention for efficient memory. | Datacenter GPU |
| **[SGLang](https://github.com/sgl-project/sglang)** | Structured output + agentic workflow engine. RadixAttention for multi-turn. | Datacenter GPU |
| **[LM Studio](https://lmstudio.ai/)** | GUI-based local LLM runner. Drag-and-drop GGUF loading. | Consumer GPU |

---

## Quick Reference

| # | Model | Params | Context | VRAM | Method | Vision | Tools | License |
|---|-------|--------|---------|------|--------|--------|-------|---------|
| 1 | DeepHat V2 | 7B/32B | 131K | ~6 GB | SFT 1.7M samples | No | Yes | Apache 2.0 |
| 2 | BugTrace Apex | 26B MoE | 32K | ~16 GB | SFT HackerOne | No | Yes | Apache 2.0 |
| 3 | BugTraceAI Ultra | 27B | 4K | ~22 GB | SFT Unsloth | No | Yes | Apache 2.0 |
| 4 | CYBER-FROST | ~180B MoE | 262K | Multi-GPU | Security FT | No | Yes | Qwen CL |
| 5 | CyberPal 2.0 | 20B | 8K | ~42 GB | SFT 403K | No | No | Apache 2.0 |
| 6 | Cyber-Prime 1.1 | 2.6B | N/A | ~6 GB | SFT+RL 75K | No | No | LFM Open |
| 7 | Cyber-Ornith | 9B | 128K | ~7 GB | Obliteration | No | Yes | Apache 2.0 |
| 8 | Dolphin3-Cyber | 8B | 2K/131K | ~6 GB | LoRA on Dolphin3 | No | No | Llama 3.1 |
| 9 | Imperum | 34B/3B MoE | 16K | ~22 GB | SFT 10+ domains | No | Yes | Apache 2.0 |
| 10 | Lily-Cyber | 7B | 8K | ~6 GB | SFT 22K pairs | No | No | Apache 2.0 |
| 11 | pentest-v2 | 8B | 32K | ~6 GB | LoRA 2.8K | No | No | Apache 2.0 |
| 12 | Qwythos-9B | 9B | 1M | ~7 GB | Post-train 500M tok | Yes | Yes | Apache 2.0 |
| 13 | RavenX-CyberAgent | 36B/3B MoE | 262K | ~24 GB | SFT 745K, 12 rounds | No | Yes | Apache 2.0 |
| 14 | REDCELL-26B | 26B/4B MoE | 262K | ~12 GB | LoRA 6.5K OSINT | No | No | Apache 2.0 |
| 15 | VEXT Pentest-7B | 7B | 8K | ~6 GB | QLoRA SFT+DPO | No | No | Apache 2.0 |
| 16 | security-slm | 1.5B | 32K | ~2 GB | Unsloth SFT | No | No | Apache 2.0 |
| 17 | Qwen3.8-27B | 27B | 262K | ~18 GB | Abliteration 131 mat | Yes | Yes | Apache 2.0 |
| 18 | GLM-5.3-Flash | 320B/18B | 1M | ~80 GB+ | Abliteration | Yes | Yes | MIT |
| 19 | GLM-5.3-CYBER | 753B | ~131K | 8xH200 | Weight modification | No | Yes | MIT |
| 20 | DS-V4.1-Flash | MoE | base | ~1.1 GB overlay | Abliteration overlay | Yes | Yes | MIT |
| 21 | Huihui-Qwen3.5 | 27B | 128K | ~18 GB | Abliteration | No | Yes | Apache 2.0 |
| 22 | Qwen2.5-Coder-32B | 32B | 128K | ~20 GB | Abliteration | No | No | Apache 2.0 |
| 23 | Qwen3.8-Cyber | 27B | 262K | ~18 GB | Abliteration+cyber | Yes | Yes | Apache 2.0 |
| 24 | HIDra-30B-A3B | 30B/3B | 128K | ~20 GB | Abliteration | No | Yes | Apache 2.0 |
| 25 | qwen25_UNCENSORED | ~7B | 32K | ~6 GB | Progressive FT | No | No | Apache 2.0 |
| 26 | Dolphin-Llama3 | 8B | 8K | ~6 GB | Data filtering | No | No | Llama 3 |
| 27 | Wizard-Vicuna-13B | 13B | 2K | ~10 GB | Data filtering | No | No | Other |

---

## Glossary

- **Abliteration**: Weight-level intervention (Arditi et al. 2024) that orthogonalizes the refusal direction out of the residual stream, removing alignment constraints without retraining
- **Obliteration**: Variant of abliteration with similar weight-intervention approach
- **SFT**: Supervised Fine-Tuning on domain-specific data
- **QLoRA**: Quantized Low-Rank Adaptation, memory-efficient fine-tuning
- **DPO**: Direct Preference Optimization
- **MoE**: Mixture of Experts, only a subset of parameters active per token
- **MTP**: Multi-Token Prediction, speculative decoding for faster inference
- **GGUF**: Quantized format for llama.cpp / Ollama deployment
- **FP8**: 8-bit floating point quantization
- **BF16**: Brain floating point 16-bit, standard training/inference format
- **Q4_K_M**: 4-bit quantization with k-quants (medium), good balance of quality/speed
- **Q6_K**: 6-bit quantization with k-quants, higher quality than Q4
- **RATH**: RavenX Attack, Threat & Hunt protocol (6-step autonomous security assessment)
- **APEX**: Domain-weighted quantization using importance matrices from training corpus
- **imatrix**: Importance matrix quantization, preserves domain-critical weights during compression
- **CyberBench**: Benchmark suite for cybersecurity models (CyNER, APTNER, CyNews, SecMMLU, CyQuiz, Email Phishing, HTTP Attack Log)

## Deployment Stacks

| Stack | Best For | GPU Required |
|-------|----------|-------------|
| Ollama | Local dev, quick testing | Consumer GPU (6-24 GB) |
| llama.cpp | GGUF models, CPU+GPU hybrid | Flexible |
| vLLM | Production serving, high throughput | Datacenter GPU |
| SGLang | Agentic workflows, structured output | Datacenter GPU |
| Transformers | Research, custom pipelines | Any |
| LM Studio | Desktop GUI, drag-and-drop | Consumer GPU |

---

## Sources

- HuggingFace model cards (all specifications)
- Open LLM Leaderboard v1 (Wizard-Vicuna benchmarks)
- OrcaRouter release notes (abliteration details, compliance rates)
- WhiteRabbitNeo/Kindo publications (USENIX Security 2024)
- Empero AI model card (Qwythos benchmarks)
- Eric Hartford / Cognitive Computations (Dolphin methodology)
- TrustedSec LLM Attack Benchmark (4,800 runs vs OWASP Juice Shop)
- Blackfrost-AI model card (CYBER-FROST architecture)
- deadbydawn101 model card (RavenX RATH protocol, training data)
- terrorswift model card (REDCELL OSINT methodology)
- cyber-pal-security publication (SecKnowledge 2.0 pipeline)
- BugTraceAI model card (Ultra tooling model design)
- IMPERUM model card (Imperum SOC/DFIR focus)
- Featherless AI ([featherless.ai](https://featherless.ai))
- OrcaRouter ([orcarouter.ai](https://www.orcarouter.ai))
- Reddit r/LocalLLaMA, r/netsec community reports

---

*Joas A. Santos | Red Team Leaders | Sep 2026*  
*For authorized security research and education only.*
