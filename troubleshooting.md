---
layout: default
title: Troubleshooting
nav_order: 6
---

# Troubleshooting

Common issues and how to fix them. The **Activity Log** (clipboard icon, top right) records scans, connection tests, skipped files, and errors — check it first.

---

## API errors during translation

### 401 Unauthorized
Your API key is invalid or revoked.
- Double-check you copied the full key (no leading/trailing spaces)
- Verify the key is active in your provider's dashboard
- Generate a new key and re-enter it in settings

### 403 Forbidden
Your account can't use the selected model.
- Some providers require billing set up before certain models
- Try a different model in the settings dialog
- Check your provider dashboard for restrictions

### 429 Too Many Requests
You've hit your provider's rate limit.
- Free tiers have strict limits — consider upgrading
- Wait a few minutes and start the batch again; the current desktop UI creates a new timestamped output folder for the new run
- Switch to a provider with higher limits (Groq is generous on free tier)

### 500 / 503 Server Error
The provider's servers are having issues.
- Wait a few minutes and start the batch again; the current desktop UI creates a new timestamped output folder for the new run
- Check the provider's status page
- Switch providers temporarily

---

## Connection test fails

1. Make sure the Base URL matches your provider exactly — see [Finding Your Base URL](base-url)
2. Confirm you picked the right provider preset
3. Re-copy the API key directly from the provider dashboard
4. Check the model name is one your account can access

---

## All my PDFs were skipped

The most common cause is **scanned / image-only PDFs** — they have no text layer to translate, so they are skipped on purpose and listed with a reason.

- Open the Activity Log to see the exact reason per file
- If a PDF *does* contain selectable text but is still skipped, it may be encrypted or malformed — try re-saving/exporting it as a fresh PDF
- For scanned documents, run OCR first to produce a text-based file, then translate that

See [Supported Files & Output](supported-files).

---

## No documents found in the folder

- The app only scans **files directly inside** the chosen folder — it does **not** look in subfolders. Move files up into one folder.
- Supported types: `.pdf`, `.docx`, `.txt`, `.md`, `.png`, `.jpg`, `.jpeg`, `.webp`, `.bmp`, `.tiff`
- Check the folder path is reachable (network/OneDrive paths can be slow or offline)

---

## Translation stopped mid-way

If a single document/language fails, it is logged and the run continues with the rest. Failed items show in red with the reason.

To finish after an interrupted or partially-failed run, start the batch again from the app. The new attempt writes to a fresh timestamped output folder, while files from the earlier attempt remain in their original folder.

---

## A document came out untranslated / in the wrong language

- If you used **Force** source language and got the source language copied through, the document may genuinely already be in a selected target language — check the result note.
- A wrong forced source label does **not** corrupt output: the model still translates from the real content. Forced source only affects the displayed label and the same-language copy decision (which is verified before copying).
- For mixed-language folders, prefer **Auto-detect**.

---

## Output files are empty or missing

- Check the output folder exists and the app has write permission
- On a network drive or OneDrive-synced folder, try a local path (e.g. `Documents\BatchTranslate`)
- Look inside the **timestamped subfolder** created by the run, not the parent folder

---

## App won't start or crashes on launch

- Run the app as Administrator once (right-click → Run as administrator) — helps with initial DPAPI setup
- Make sure Windows is up to date (Windows 10 or later required)
- Reinstall from the Microsoft Store if it persists

---

## Still stuck?

[Open an issue](https://github.com/3thousand30/batchtranslate-docs/issues) and include:
- The error message (and relevant Activity Log lines)
- Which AI provider and model you're using
- The input file types and target languages
- Whether source language was auto-detected or forced
