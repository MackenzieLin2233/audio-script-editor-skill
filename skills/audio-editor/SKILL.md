---
name: audio-editor
description: "Transform English audio into a content package: a Word transcript, HTML slides, and/or a Chinese RedNote/Xiaohongshu script as a Word document. Use when the user provides or plans to provide English audio for personal-brand or educational content."
---

# Audio Editor

## Audio intake

When the skill is invoked, before any transcription or slide work:

1. If the user already gave an explicit audio file path, use that file and skip the steps below.
2. Otherwise, read the `D:\Audio Draft` folder and find the most recently modified audio file (by modification time; extensions: `.mp3`, `.wav`, `.m4a`, `.aac`, `.flac`, `.ogg`, `.wma`, `.opus`, `.webm`, `.mp4`, `.mov`).
3. Show the user the candidate: file name, full path, size, and modified time. Then **ask them to confirm it is the file they want** — do not transcribe or build slides until they confirm.
4. If they say no (or the folder is empty), list the other audio files in `D:\Audio Draft` (if any) and let them pick, or accept a file path they provide.

## Core workflow

Two phases. Produce only the requested essentials; avoid unnecessary conversation, audit notes, checklists, and verbose explanations.

### Phase 1 — Transcribe + Word deliverables (no slides yet)

1. **Transcribe**
   - Transcribe with faster-whisper (v1.2.1) on CPU with int8, model `distil-small.en` (Systran's English-only distilled Whisper "small"). The audio is always English; this is the smallest model that still transcribes it cleanly.
   - From the raw model output, create a clean English transcript, delivered as a Word document (`transcript.docx`).
   - Remove obvious filler words, false starts, and repeated fragments only when meaning is unchanged.
   - Preserve intent, examples, key terms, names, numbers, and sequencing.
   - Label multiple speakers consistently.
   - Mark unclear words as `[unclear]`; do not guess.

2. **Generate RedNote script**
   - Generate only the Chinese RedNote/Xiaohongshu part; do not create a polished English script unless explicitly requested.
   - Deliver it as a Word document (`rednote.docx`).
   - Write native Chinese, not literal translation.
   - Include: title options, hook, body, CTA, and limited hashtags.
   - Preserve the original meaning; do not invent facts, data, or claims.

**Do NOT create slides in Phase 1.**

### Phase 2 — Slides, only after the user edits the transcript

- Wait for the user to edit `transcript.docx` and then request the slides. Do not build slides before that.
- Read the edited `transcript.docx`.
- Build `slides.html` from the edited transcript: **one or two slides per H1 heading** in the transcript.
- Generate an HTML slide deck, not `.pptx`.
- Build from the template library at `references/beautiful-html-templates/` (34 templates). Read its `index.json` for mood/tone metadata and its `AGENTS.md` for adaptation rules — preserve fonts, palette, layout, and decorations; replace placeholder content.
- **Never auto-select a template; the choice belongs to the user.** Before building slides, read `references/beautiful-html-templates/index.json`, present 3–5 fitting candidates (name + tagline, grouped by inferred tone), and ask the user which one to use. Wait for the answer, then build with that template. This overrides the library's `AGENTS.md` self-pick workflow (its "pick 3 candidates" step becomes "offer candidates, user decides").
- On Windows, open HTML files in the browser with `start <path>` (the library's `AGENTS.md` says `open <path>`, which is macOS-only).
- Structure: hook → context → insight → examples → takeaway → action.
- Keep each slide to one idea with concise text.

## Slide benchmark — "Big Number" SOP

Benchmark source: `C:\Users\Sande\audio-editor-output\0粉100元Day1+30\slides.html`, slide 03 ("Why 100 yuan"). Every stat/number slide in a future deck must match this bar:

1. **Numbered kicker** — `NN / <topic>` label, uppercase, letter-spaced, ≤ 6 words (e.g., `01 / Why 100 yuan`).
2. **One big number as the anchor** — a single memorable number, comma-formatted (3,000 not 3000), rendered as a huge serif numeral at the top of the slide.
3. **Completion phrase** — the h2 completes the number into a full claim so number + phrase read as one sentence (`3,000 / yuan a month is the survival line.`).
4. **One lede** — exactly one plain-word sentence (≤ ~20 words) stating the significance: "Earn this — 100 yuan a day — and I can survive without a 9-to-6 job." No bullets, no second sentence.
5. **Layout** — number on top (massive, serif), completion phrase directly beneath, lede below; slide uses its section color; nothing else on the slide.

General bar it enforces for every slide in any deck:

- One idea per slide: kicker + headline + at most one lede (plus at most one cards/stats/ol block).
- Concrete numbers over vague claims; keep exact values from the source audio.
- Every slide's lede answers "so what?"

## Default deliverables

Use `references/output_templates.md` for the minimal fallback structure and `references/beautiful-html-templates/` (template library) for slide decks.

Default files:

1. `transcript.docx` (Word) when transcript is needed.
2. `slides.html` when slides are requested or useful.
3. `rednote.docx` (Word) for the RedNote script.

If the user asks for “the result,” deliver the generated files with the shortest possible note.

## Clarification rules

Ask only when blocked. Otherwise infer audience, tone, and length from the audio/request and proceed.

## Brevity rule

Use the least tokens needed. No progress chatter, no audit/checklist section, no self-review commentary in the final answer.
