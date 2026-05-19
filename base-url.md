---
layout: default
title: Finding Your Base URL
nav_order: 5
---

# Finding Your Base URL

The **Base URL** is the root address of the AI provider's API. BatchTranslate with AI appends `/chat/completions` to it when making requests.

If you select one of the nine built-in provider presets, the Base URL is filled in automatically — you don't need to touch it. This page is mainly for custom endpoints or for understanding what the field means.

---

## Base URLs for all built-in providers

| Provider | Base URL |
|---|---|
| OpenAI | `https://api.openai.com/v1` |
| DeepSeek | `https://api.deepseek.com/v1` |
| OpenRouter | `https://openrouter.ai/api/v1` |
| Groq | `https://api.groq.com/openai/v1` |
| Mistral AI | `https://api.mistral.ai/v1` |
| Together AI | `https://api.together.xyz/v1` |
| xAI (Grok) | `https://api.x.ai/v1` |
| Fireworks AI | `https://api.fireworks.ai/inference/v1` |
| Cerebras | `https://api.cerebras.ai/v1` |

---

## Using a custom Base URL

Select **Custom (OpenAI-Compatible)** from the provider dropdown in the settings dialog, then enter your Base URL.

| Setup | Typical Base URL |
|---|---|
| Ollama (local) | `http://localhost:11434/v1` |
| LM Studio (local) | `http://localhost:1234/v1` |
| LocalAI | `http://localhost:8080/v1` |
| Any OpenAI-compatible server | Varies — check your provider's docs |

The endpoint must support the OpenAI `/chat/completions` format. If your provider's docs show a different path structure, use the part before `/chat/completions` as the Base URL.

> Standard Azure OpenAI endpoints are not currently supported by the **Custom (OpenAI-Compatible)** preset. Azure uses different authentication and query-parameter conventions from the generic OpenAI-compatible flow used by the app.

> Custom endpoints generally do not provide prompt caching, so multi-language runs won't get the caching discount. Translation still works normally.

---

## Common mistakes

**Trailing slash** — do not add a `/` at the end. Use `https://api.openai.com/v1`, not `https://api.openai.com/v1/`.

**Including the endpoint path** — the Base URL should stop before `/chat/completions`. The app adds that automatically.

**HTTP instead of HTTPS** — the app only opens HTTPS links for security. Local endpoints (localhost) are handled by your local server setup.

---

## Model max output tokens

The settings dialog also has a **Model max output tokens** field. It controls how much output headroom the app gives each translation call. Higher values reduce chunk splitting and retrying, especially for verbose scripts such as Hindi, Arabic, Chinese, and Japanese. BatchTranslate now translates one target language per call; on caching-capable providers the shared source prefix is reused cheaply across those calls. The preset value is sensible for each provider — only change it if you know your model's real output limit.

---

## Testing your connection

After entering a Base URL and API key, click **Test** in the settings dialog. The app sends a lightweight request to verify the key works before you start a batch. If the test fails, see [Troubleshooting](troubleshooting).
