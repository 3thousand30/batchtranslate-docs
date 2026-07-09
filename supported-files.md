---
layout: default
title: Supported Files & Output
nav_order: 3
---

# Supported Files & Output

What goes in, what comes out, and how long jobs are handled.

---

## Input formats

| Type | Notes |
|---|---|
| `.pdf` | Text is extracted from the PDF's text layer. **Scanned / image-only PDFs have no text layer** and are skipped (see below). |
| `.docx` | Text is extracted (paragraphs and headings). Original styling/layout is not preserved. |
| `.txt` | Read as-is. |
| `.md` | Read as-is; Markdown structure is preserved through translation. |
| `.png` `.jpg` `.jpeg` `.webp` `.bmp` `.tiff` `.tif` | Translated via the vision API. The extracted and translated text is the output — original image layout is not reproduced. Requires a vision-capable model. |

Only files **directly inside** the chosen folder are processed — the app does **not** scan subfolders. Put everything you want translated into one folder.

---

## Scanned / image-only PDFs

A scanned PDF is really a set of page images with no selectable text. There is nothing to extract or translate, so the app:

1. Detects that the PDF has no usable text layer
2. **Skips** it (no tokens spent)
3. Lists it in the results as skipped, with the reason

If you need scanned PDFs translated, run them through OCR first to produce a text-based PDF or a `.txt`/`.docx`, then translate that. Alternatively, use standalone image files (`.png`, `.jpg`, etc.) which are handled directly via the vision API.

---

## Output layout

Each run creates a **timestamped subfolder** in your output folder:

```
Documents\BatchTranslate\
  2026-05-18_12-44-05\
    Report 2024-pdf.de-DE.md
    Report 2024-pdf.fr-FR.md
    Notes-docx.de-DE.md
    photo-jpg.de-DE.md
    .batchtranslate-progress.json
```

- **One file per document per language.**
- The output name keeps the original file name, folds in the original extension (so `report.pdf` and `report.docx` never collide), and adds the language code.
- Format is Markdown (`.md`) or Plain text (`.txt`), depending on your Step 2 choice. Original PDF/DOCX page layout and fonts are **not** reproduced — this is a text translator, not a layout converter.
- `.batchtranslate-progress.json` is the progress checkpoint written during an active run (see below). It is safe to delete once you are happy with a finished run.

---

## Same-language pass-through

If a target language is the same language a document is already in (as detected by the AI), the document is **copied through unchanged** and no tokens are spent. It appears in the results marked *"Source already in <language> — copied unchanged (0 tokens)"*.

Languages with regional variants (English US / UK) are always translated rather than copied, so the requested variant's localisation is actually applied.

---

## Long documents

There is no practical page limit. Documents are split into chunks on paragraph and sentence boundaries (never mid-sentence), translated in order with terminology kept consistent across chunks, and written to disk as each chunk completes.

A `.batchtranslate-progress.json` file is written inside the active run folder while translation is in progress. In the current desktop UI, clicking **Translate** again creates a new timestamped run folder, so restarting a stopped batch starts a fresh run rather than resuming inside the previous folder.

---

## Token size and cost

Use **Estimate size** in Step 2 for a rough pre-flight token range. It is deliberately approximate; once translation starts, a live projection refines it from real token usage.

The app does not show prices — providers price differently and change rates. To get a cost figure, multiply the token count by your provider's published per-token price. See [Choosing an AI Provider](choosing-a-provider) for rough comparisons.
