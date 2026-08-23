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
   - Use a simple, readable single-file HTML format unless the user asks otherwise.
   - Structure: hook → context → insight → examples → takeaway → action.
   - Keep each slide to one idea with concise text.

3. **Generate RedNote HTML**
   - Generate only the Chinese RedNote/Xiaohongshu part; do not create a polished English script unless explicitly requested.
   - Deliver it as an HTML file, not Word, `.doc`, or `.docx`.
   - Write native Chinese, not literal translation.
   - Include: title options, hook, body, CTA, and limited hashtags.
   - Preserve the original meaning; do not invent facts, data, or claims.

## Default deliverables

Use `references/output_templates.md` for HTML structure.

Default files:

1. `transcript.md` when transcript is needed.
2. `slides.html` when slides are requested or useful.
3. `rednote.html` for the RedNote script.

If the user asks for “the result,” deliver the generated files with the shortest possible note.

## Clarification rules

Ask only when blocked. Otherwise infer audience, tone, and length from the audio/request and proceed.

## Brevity rule

Use the least tokens needed. No progress chatter, no audit/checklist section, no self-review commentary in the final answer.
