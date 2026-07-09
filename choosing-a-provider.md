---
layout: default
title: Choosing an AI Provider
nav_order: 4
---

# Choosing an AI Provider

Batch Translate Text with any AI works with any OpenAI-compatible API. Ten providers are built in — you just pick one, get an API key, and paste it in. No other configuration needed.

---

## Quick recommendation

| If you want... | Use |
|---|---|
| Cheapest option for bulk translation | **DeepSeek** |
| Best overall quality | **OpenAI** (gpt-4o or gpt-4o-mini) |
| Cheapest multi-language runs | **OpenAI**, **DeepSeek**, or **xAI** (prompt caching) |
| Fastest responses | **Groq** |
| No account, many models | **OpenRouter** |
| European data residency | **Mistral AI** |

---

## Multi-language efficiency (prompt caching)

When you translate one document into several languages, the source text has to reach the model for each language. Providers with **prompt caching** reuse the source from cache for languages 2…N at a large discount instead of charging full price every time.

In the app, caching-capable providers are labelled **"Cost-efficient for multi-language."** The translation engine still works on any provider — it just won't get the discount on ones without caching, and the settings dialog tells you which is which.

| Caching support | Providers |
|---|---|
| **Yes** (cost-efficient for multi-language) | OpenAI, DeepSeek, OpenRouter*, xAI |
| No (still works, no multi-language discount) | Groq, Mistral, Together AI, Fireworks, Cerebras |

\* OpenRouter caching depends on the underlying model you route to.

---

## All supported providers

| Provider | Strengths | Free tier | Sign up |
|---|---|---|---|
| **OpenAI** | Best quality, reliable, prompt caching | No (credits on signup) | [platform.openai.com](https://platform.openai.com) |
| **DeepSeek** | Extremely low cost, strong quality, context caching | Yes (limited) | [platform.deepseek.com](https://platform.deepseek.com) |
| **OpenRouter** | 100+ models from one key, caching varies by model | No | [openrouter.ai](https://openrouter.ai) |
| **Groq** | Very fast inference, good for high volume | Yes (rate limited) | [console.groq.com](https://console.groq.com) |
| **Mistral AI** | Strong multilingual, EU-based | Yes (limited) | [console.mistral.ai](https://console.mistral.ai) |
| **Together AI** | Wide model selection, competitive pricing | Yes ($1 credit) | [api.together.ai](https://api.together.ai) |
| **xAI (Grok)** | Grok models, good reasoning, prompt caching | No | [console.x.ai](https://console.x.ai) |
| **Fireworks AI** | Fast, cost-effective | Yes ($1 credit) | [fireworks.ai](https://fireworks.ai) |
| **Cerebras** | Ultra-fast inference | Yes (limited) | [cloud.cerebras.ai](https://cloud.cerebras.ai) |

---

## Cost considerations

All providers charge per **token** — roughly 1 token per 0.75 words. Translation output is usually a little longer than the source, and some languages (German, Finnish) use more tokens per character than English.

- A 10-page document into one language uses very roughly 8,000–20,000 tokens total
- A 300-page book into one language can run into the low millions of tokens
- At DeepSeek's rates a large book typically costs a few dollars; premium models cost more
- Translating into N languages with a caching-capable provider costs far less than N× the single-language cost

Use **Estimate size** before large jobs, and watch the live projection during a run. The app deliberately does not display prices — multiply the token figure by your provider's current published rate.

---

## Using a custom endpoint

If you use a self-hosted model (Ollama, LM Studio, LocalAI) or a provider not in the list, select **Custom (OpenAI-Compatible)** from the provider dropdown in the settings dialog and enter your endpoint's base URL manually. The endpoint must be OpenAI-compatible (`/chat/completions`). See [Finding Your Base URL](base-url).

---

## Switching providers

Open the **key icon** (top right) to manage your AI connections. You can save up to 10 named connections and switch between them at any time — click the connection chip you want to use, then click **Set as active connection**. Each connection stores its own provider, model, base URL, and API key separately.

To add a new connection, click **Add** inside the AI Connections dialog. Base URL, model, and the caching flag update automatically when you pick a provider preset.
