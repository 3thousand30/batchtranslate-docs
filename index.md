---
layout: default
title: Home
nav_order: 1
---

# BatchTranslate with AI

**BatchTranslate with AI** is a Windows desktop app by [3thousand30](https://3thousand30.com) for translating a whole folder of documents — PDF, DOCX, TXT, and Markdown — into one or more languages using AI.

You bring your own AI API key (BYOK). The app connects directly to the provider of your choice — no middleman, no subscription, and no file storage operated by us.

[Get it on Microsoft Store](https://apps.microsoft.com/detail/9N75DWR9X2S7){: .btn .btn-blue }

---

## How it works

1. **Pick a folder** — point the app at a folder of documents (`.pdf`, `.docx`, `.txt`, `.md`)
2. **Choose languages** — select one or more target languages; the source language is auto-detected (or you can force it)
3. **Estimate** _(optional)_ — get a rough token size before committing to a large job
4. **Translate** — the app extracts, chunks, translates, and writes the results to a timestamped folder

Each run lands in your output folder, one file per document per language, ready to use. The app may also request the Inter UI font from Google Fonts for display consistency when an internet connection is available.

---

## Key features

- **Whole-folder batches** — translate dozens of documents in one run; one file in, one file out per language
- **Handles long documents** — books of 100–500 pages are split on natural boundaries and translated in chunks for reliable long-document handling
- **Multiple languages at once** — translate into several languages in one pass; on caching-capable providers the source text is reused cheaply instead of re-sent at full price
- **Automatic source detection** — the AI identifies the source language per document; you can also force it
- **Skips scanned PDFs cleanly** — image-only PDFs with no text layer are detected and reported, not silently mangled
- **Same-language pass-through** — selecting a language a document is already in copies it through unchanged, spending zero tokens
- **Live cost-size projection** — a rough pre-flight estimate that self-corrects from real token usage as the run proceeds
- **9 AI provider presets** — OpenAI, DeepSeek, OpenRouter, Groq, Mistral, Together AI, xAI, Fireworks, Cerebras, or any custom OpenAI-compatible endpoint
- **Secure API key storage** — keys are encrypted on-device using Windows DPAPI, never transmitted anywhere except directly to your chosen AI provider

---

## Documentation

- [Getting Started](getting-started) — install, configure, and run your first batch
- [Supported Files & Output](supported-files) — input formats, output layout, and long-document handling
- [Choosing an AI Provider](choosing-a-provider) — compare providers by cost, speed, and multi-language efficiency
- [Finding Your Base URL](base-url) — what Base URL is and where to find it for each provider
- [Troubleshooting](troubleshooting) — common errors and how to fix them

---

## Support

Found a bug or have a question? Email [hello@3thousand30.com](mailto:hello@3thousand30.com) or [open an issue](https://github.com/3thousand30/batchtranslate-docs/issues) on GitHub.

---

[Privacy Policy](privacy)
