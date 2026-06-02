# Case Study: Kyoukai no Kanata OP Typesetting Workflow

This case study records the engineering thinking behind a subtitle-typesetting workflow. The repository does not include original video, anime media or full subtitle sources; it preserves technical decisions and ASS snippets for review.

## Objective

| Initial issue | Technical handling |
|---|---|
| Inconsistent lyric color across nearby lines | Choose color by scene context and split phases when the visual context changes |
| Border and blur looked too harsh | Use a soft glow layer under a clean white readable layer |
| Too many transforms, clips and noisy lines | Reduce normal lyrics to two clear layers |
| Shadow polluted the readable text | Remove shadow from the primary lyric layer |
| A few special lines needed the old style | Keep a separate block only when the special style carries the intended visual identity |

## Main Layer Formula

| Layer | Role | Main tags |
|---|---|---|
| 1 | Soft colored glow | `\blur`, `\bord`, alpha control and scene-matched border color |
| 2 | Readable white text | low blur, no border and white fill |

## Technical Lessons

- A clean effect is usually a small number of correct tags, not a large number of animated tags.
- Use `\fad` for entry and exit timing; avoid transform-heavy blur/border animation unless it is visually necessary.
- Render cropped subtitle regions for faster glow review before running a full-frame pass.
- Split phases by scene context instead of forcing one color across every frame.
- Keep special gradient blocks only when they explain a real visual decision.

## Verification Command

```powershell
ffmpeg -i input.mp4 -vf "ass=preview.ass,crop=1920:320:0:760" -frames:v 1 preview.png
```
