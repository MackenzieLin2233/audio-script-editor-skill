---
name: audio-editor
description: "Transform English audio into a minimal HTML content package. Use when the user provides or plans to provide English audio and wants transcription, HTML slides, and/or a Chinese RedNote/Xiaohongshu script as HTML for personal-brand or educational content."
---

# Audio Editor

## Core workflow

When the user provides English audio, produce only the requested essentials. Avoid unnecessary conversation, audit notes, checklists, and verbose explanations.

1. **Transcribe**
   - Create a clean English transcript.
   - Remove obvious filler words, false starts, and repeated fragments only when meaning is unchanged.
   - Preserve intent, examples, key terms, names, numbers, and sequencing.
   - Label multiple speakers consistently.
   - Mark unclear words as `[unclear]`; do not guess.

2. **Create HTML slides**
   - Generate an HTML slide deck, not `.pptx`.
   - Build from the template library at `references/beautiful-html-templates/` (34 templates). Read its `index.json` for mood/tone metadata and its `AGENTS.md` for adaptation rules — preserve fonts, palette, layout, and decorations; replace placeholder content.
   - **Never auto-select a template; the choice belongs to the user.** Before building slides, read `references/beautiful-html-templates/index.json`, present 3–5 fitting candidates (name + tagline, grouped by inferred tone), and ask the user which one to use. Wait for the answer, then build with that template. This overrides the library's `AGENTS.md` self-pick workflow (its "pick 3 candidates" step becomes "offer candidates, user decides").
   - On Windows, open HTML files in the browser with `start <path>` (the library's `AGENTS.md` says `open <path>`, which is macOS-only).
   - Structure: hook → context → insight → examples → takeaway → action.
   - Keep each slide to one idea with concise text.

3. **Generate RedNote HTML**
   - Generate only the Chinese RedNote/Xiaohongshu part; do not create a polished English script unless explicitly requested.
   - Deliver it as an HTML file, not Word, `.doc`, or `.docx`.
   - Write native Chinese, not literal translation.
   - Include: title options, hook, body, CTA, and limited hashtags.
   - Preserve the original meaning; do not invent facts, data, or claims.

## Default deliverables

Use `references/output_templates.md` for the minimal fallback structure and `references/beautiful-html-templates/` (template library) for slide decks.

Default files:

1. `transcript.md` when transcript is needed.
2. `slides.html` when slides are requested or useful.
3. `rednote.html` for the RedNote script.

If the user asks for “the result,” deliver the generated files with the shortest possible note.

## Clarification rules

Ask only when blocked. Otherwise infer audience, tone, and length from the audio/request and proceed.

## Brevity rule

Use the least tokens needed. No progress chatter, no audit/checklist section, no self-review commentary in the final answer.
