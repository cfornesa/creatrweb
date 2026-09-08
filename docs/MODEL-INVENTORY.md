# Model Inventory — CreatrWeb

Confirmed free models per provider as of April 2026.
Do not use any model not listed here for free-tier sessions
without first verifying current pricing.

---

## OpenRouter — Free Models

| Model ID | Type | Notes |
|---|---|---|
| `openai/gpt-oss-120b:free` | 117B MoE, general reasoning | Strongest free reasoning model |
| `openai/gpt-oss-20b:free` | 20B, general | Fallback when 120b is rate-limited |
| `qwen/qwen2.5-coder-32b-instruct:free` | 32B, coding | Purpose-built code generation |
| `minimax/minimax-m2.5:free` | General reasoning | Strong conversational model |
| `qwen/qwen2.5-vl-72b-instruct:free` | 72B, multimodal | Image input support |

> Free Models Router: `openrouter/free` — routes to best available
> free model at time of request. Output may vary day to day.

---

## Groq — Free Models

| Model ID | Type | Notes |
|---|---|---|
| `groq/compound` | Multi-tool, Llama 4 Scout + GPT-OSS 120B | Web search, code execution via E2B |
| `groq/compound-mini` | Single-tool, Llama 3.3 70B + GPT-OSS 120B | 3× lower latency than Compound |

Rate limits: 30 req/min, 70,000 TPM for both models.
Orpheus V1 English (`orpheus-tts-0.1-af-v1`) is free but
TTS only — not applicable to coding sessions.

---

## Opencode Zen — Free Models (included with Opencode Go)

| Model ID | Type | Notes |
|---|---|---|
| `big-pickle` | General coding | Confirmed permanently free |
| `nemotron-3-super-free` | 120B hybrid MoE | NVIDIA, US-affiliated |
| `minimax-m2.5-free` | General reasoning | MiniMax, note PRC-affiliated |
| `gpt-5-nano` | Fast reasoning, 400K context | OpenAI, permanently free on Zen |

> minimax-m2.5-free is PRC-affiliated. Do not use on the
> Boycott App or any project with sensitive political content.

---

## Opencode Go — Subscription Models

| Model ID | Type | Notes |
|---|---|---|
| `glm-5.1` | 754B, agentic coding | Zhipu AI — PRC-affiliated |
| `vglm-5` | Earlier GLM generation | Zhipu AI — PRC-affiliated |
| `minimax-m2.7` | General reasoning | MiniMax — PRC-affiliated |
| `minimax-m2.5` | General reasoning | MiniMax — PRC-affiliated |
| `kimi-k2.5` | Reasoning | Moonshot AI — PRC-affiliated |
| `mimo-v2-pro` | Reasoning chains | Tencent — PRC-affiliated |
| `mimo-v2-omni` | Multimodal | Tencent — PRC-affiliated |
| `qwen3.5-plus` | General | Alibaba — PRC-affiliated |
| `qwen3.6-plus` | General | Alibaba — PRC-affiliated |

> All Opencode Go models are PRC-affiliated. Do not use any
> of these on the Boycott App or projects covering Uyghur,
> Palestine, Sudan, or Congo issues.

---

## Kilo Code — Native Free Models

| Model ID | Type | Notes |
|---|---|---|
| `kilo-auto/free` | Auto-routing | Routes to best available free model |
| `nvidia/nemotron-3-super-120b-a12b:free` | 120B hybrid MoE | NVIDIA, permanently free |
| `openrouter/free` | Router | Routes to best OpenRouter free model |

> Dola Seed 2.0 Pro, xAI Grok Code Fast 1, and Step 3.5 Flash
> are time-limited promotional models — do not rely on them
> for any stack configuration.

---

## PRC Affiliation Reference

| Provider / Model family | PRC-affiliated | Safe for Boycott App |
|---|---|---|
| OpenAI (gpt-oss, gpt-5-nano) | No | Yes |
| NVIDIA (Nemotron) | No | Yes |
| Meta (Llama) | No | Yes |
| Mistral (Codestral) | No | Yes |
| Groq infrastructure | No | Yes |
| Zhipu AI (GLM) | Yes | No |
| MiniMax | Yes | No |
| Moonshot AI (Kimi) | Yes | No |
| Tencent (MiMo) | Yes | No |
| Alibaba (Qwen) | Yes | No |
| Bytedance (Dola Seed) | Yes | No |