# ASS Effect Notes

This document collects reusable ASS subtitle-effect patterns from real typesetting workflows. The goal is to preserve technical thinking: fewer layers, cleaner tags and easier debugging in Aegisub and FFmpeg/libass.

## Working Principles

| Principle | Reason |
|---|---|
| Normal lyric lines usually need only two layers | The lower layer provides colored glow; the upper layer keeps readable white text |
| Avoid animating blur and border unless necessary | Transform-heavy blur and border changes can look unstable and are harder to control |
| Avoid shadow on primary lyric text | Shadow can dirty the edge, especially on bright or glow-heavy frames |
| Match glow color to the background | A color that works on one frame may fail after a scene cut |
| Keep nearby scene phases stable | Excessive fade-in/fade-out can create flicker when phases are close together |

## Two-Layer Glow Pattern

Lower glow layer:

```ass
Dialogue: 1,0:00:00.00,0:00:03.00,OP,,0,0,0,,{\an2\q2\fad(120,150)\blur7.5\bord6.5\1a&HFF&\3a&H3A&\c&H7E5D31&\3c&H7E5D31&}Sample lyric
```

Upper readable layer:

```ass
Dialogue: 2,0:00:00.00,0:00:03.00,OP,,0,0,0,,{\an2\q2\fad(120,150)\blur0.7\bord0\1a&H00&\c&HFFFFFF&}Sample lyric
```

## Preview Check

Render a cropped subtitle region:

```powershell
ffmpeg -i input.mp4 -vf "ass=preview.ass,crop=1920:320:0:760" -frames:v 1 preview.png
```

## When to Use Multi-Line Gradients

Use line-by-line gradients only when the effect genuinely needs vertical or frame-aware color movement. For normal lyric text, a two-layer glow is cleaner and easier to maintain. If a gradient is required, automate it with a script such as `lyger.GradientEverything.moon` instead of manually writing hundreds of `\clip` tags.
