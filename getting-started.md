---
layout: default
title: Getting Started
nav_order: 2
---

# Getting Started

This guide walks you through setting up BatchTranslate with AI and running your first batch translation.

---

## 1. Install the app

Download and install **BatchTranslate with AI** from the Microsoft Store. Once installed, launch it from the Start menu.

---

## 2. Set up your AI provider

Before translating anything, you need an API key from an AI provider.

1. Click the **key icon** (top right of the app)
2. Select your provider from the dropdown — if you're not sure which one to pick, see [Choosing an AI Provider](choosing-a-provider)
3. Click **Get API key** to open the provider's signup page
4. Paste your API key into the field — it saves automatically
5. Click **Test** to confirm everything is working

Your API key is encrypted and stored on your device only. It is sent directly to your chosen provider — nowhere else.

Providers marked **“Cost-efficient for multi-language”** support prompt caching, which makes translating into several languages much cheaper. See [Choosing an AI Provider](choosing-a-provider).

---

## 3. Choose your source folder (Step 1)

Click **Choose…** next to *Folder* and select the folder containing the documents you want to translate.

- Only files **directly inside** that folder are picked up — subfolders are **not** scanned. Move files into one folder if needed.
- Supported types: `.pdf`, `.docx`, `.txt`, `.md`
- The app shows how many documents were found and a per-type breakdown

> Scanned / image-only PDFs (no selectable text) have no text layer to translate. They are detected, skipped, and clearly listed in the results — see [Supported Files & Output](supported-files).

---

## 4. Set the source language (Step 1)

- **Auto-detect (recommended)** — the AI identifies the source language of each document. This handles mixed folders and is the safest choice.
- **Force** — type a language name (e.g. `German`) to tell the app the source explicitly. If left blank, the app falls back to auto-detect.

The detected language for each document is shown in the results after a run.

---

## 5. Pick target languages (Step 1)

Tick one or more languages to translate **into**. You can select many at once.

- Translating into multiple languages reuses the source cheaply on caching-capable providers.
- Some languages (e.g. German, Finnish) use more tokens per character than English, so their output costs a little more — the in-run estimate accounts for this automatically.
- If you select a language a document is already in, that document is **copied through unchanged** (zero tokens) and marked accordingly.

---

## 6. Output settings (Step 2)

1. Choose an **output folder** (defaults to `Documents\BatchTranslate`)
2. Choose an **output format**:
   - **Markdown (.md)** — preserves headings, lists, and paragraph structure
   - **Plain text (.txt)** — clean text only

Each run creates a **timestamped subfolder** (e.g. `2026-05-18_12-44-05`). Inside it you get one file per document per language, named like `Report 2024-pdf.de-DE.md`.

---

## 7. Estimate, then translate (Step 2)

1. _(Optional)_ Click **Estimate size** for a rough token range before a large job. For cost, multiply the token count by your provider's per-token price (see their pricing page).
2. Click **▶ Translate**.

The app extracts text, splits long documents into chunks on natural boundaries, and translates them. A progress bar and a live, self-correcting token projection are shown while it runs. When complete, a summary lists every document → language result with the detected source language, and a button opens the output folder.

---

## Long documents

Books of 100–500 pages are fully supported. Documents are chunked and translated piece by piece, and a `.batchtranslate-progress.json` file is written inside the active run folder while the job is in progress.

If a run is cancelled, crashes, hits a rate limit, or loses connection, start the batch again from the app. The current desktop UI creates a new timestamped output folder for each run, so a restarted run begins fresh rather than continuing inside the previous folder. See [Supported Files & Output](supported-files).

---

## Next steps

- Try translating into several languages at once with a caching-capable provider
- Use **Estimate size** before committing to a large book
- Check the **Activity Log** (clipboard icon, top right) to see exactly what was scanned, skipped, or failed
