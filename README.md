# audio-editor

An **Agent Skill** that turns English audio into a minimal HTML content package: a clean transcript, HTML slides, and a Chinese RedNote/Xiaohongshu script.

## What it produces

- `transcript.md` — clean English transcript (filler removed, `[unclear]` marks for unclear audio)
- `slides.html` — HTML slide deck built from one of the 34 bundled templates (hook → context → insight → examples → takeaway → action); the user picks the template before it's built
- `rednote.html` — native-Chinese Xiaohongshu/RedNote script (title options, hook, body, CTA, hashtags)

## Repo layout

```
skills/
  audio-editor/
    SKILL.md
    references/
      output_templates.md
      beautiful-html-templates/   # 34-template slide library (see index.json)
```

## Install

The skill uses the standard `SKILL.md` Agent Skills format (a folder with `SKILL.md` plus supporting files), so it works in any agent that loads skills from a `SKILL.md` directory.

```bash
git clone https://github.com/MackenzieLin2233/audio-script-editor-skill.git
cd audio-script-editor-skill
```

### Claude Code / Claude Desktop

```bash
mkdir -p ~/.claude/skills
cp -r skills/audio-editor ~/.claude/skills/
```

### Kimi Code

```bash
mkdir -p ~/.kimi-code/skills
cp -r skills/audio-editor ~/.kimi-code/skills/
```

Then invoke with `/skill:audio-editor` in a new session.

### Shared cross-agent location (`~/.agents/skills`)

Several agents (including Kimi Code) also scan `~/.agents/skills/`, which lives under the real OS home and can be shared across tools:

```bash
mkdir -p ~/.agents/skills
cp -r skills/audio-editor ~/.agents/skills/
```

### Other agents

Any agent that reads `SKILL.md`-style skills: copy the `audio-editor` folder into that agent's skills directory (e.g. `.claude/skills/`, `.kimi-code/skills/`, `.agents/skills/`, or the agent's own equivalent).

## Use

Provide English audio and ask for the transcript, slides, and/or RedNote script. The skill produces only the requested essentials.
