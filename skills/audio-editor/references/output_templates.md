# Output Templates

## `slides.html`

Single-file HTML slide deck. Use concise text and readable styling.

Required structure:

- `<section class="slide">` per slide
- One main idea per slide
- Minimal bullets
- No PPTX/export instructions

Skeleton:

```html
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Audio Slides</title>
<style>
body{margin:0;font-family:Inter,Arial,sans-serif;background:#111;color:#fff}
.slide{min-height:100vh;box-sizing:border-box;padding:8vh 10vw;display:flex;flex-direction:column;justify-content:center;border-bottom:1px solid #333}
h1{font-size:clamp(42px,7vw,88px);line-height:1.05;margin:0 0 24px}
h2{font-size:clamp(32px,5vw,64px);line-height:1.1;margin:0 0 20px}
p,li{font-size:clamp(20px,2.4vw,34px);line-height:1.35;color:#e7e7e7}
ul{padding-left:1.2em}
</style>
</head>
<body>
<section class="slide"><h1>[Title]</h1><p>[Hook]</p></section>
<section class="slide"><h2>[Slide title]</h2><ul><li>[Point]</li></ul></section>
</body>
</html>
```

## `rednote.html`

Single-file HTML RedNote script. Use Chinese as the content language.

Required sections:

1. 标题建议
2. 开头 Hook
3. 正文
4. 结尾 CTA
5. 话题标签

Skeleton:

```html
<!doctype html>
<html lang="zh-CN">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>小红书文案</title>
<style>
body{font-family:-apple-system,BlinkMacSystemFont,"PingFang SC","Microsoft YaHei",sans-serif;line-height:1.75;max-width:820px;margin:40px auto;padding:0 24px;color:#1f2937;background:#fff7f7}
.card{background:white;border-radius:24px;padding:28px;box-shadow:0 12px 40px rgba(190,24,93,.12)}
h1{color:#be185d}h2{margin-top:28px;color:#9d174d}.tags{color:#be185d}
</style>
</head>
<body><main class="card">
<h1>小红书文案</h1>
<h2>标题建议</h2><ol><li>[标题]</li></ol>
<h2>开头 Hook</h2><p>[Hook]</p>
<h2>正文</h2><p>[正文]</p>
<h2>结尾 CTA</h2><p>[CTA]</p>
<h2>话题标签</h2><p class="tags">#[标签] #[标签]</p>
</main></body>
</html>
```

## `transcript.md`

Use only when needed:

```markdown
# Clean Transcript

[Clean transcript. Mark unclear audio as `[unclear]`.]
```
