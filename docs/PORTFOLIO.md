# Portfolio Notes

This repository should be read as a small engineering artifact: it has a real workflow problem, scripting tools, documentation, visual evidence and release snapshots.

## Repository Positioning

| Component | Purpose |
|---|---|
| README | Explains the repository quickly for HR and engineering review |
| `automation/` | Contains the actual macro and include material |
| `examples/` | Preserves technical snippets without redistributing copyrighted media |
| `docs/` | Explains workflow decisions and verification commands |
| `assets/` | Provides GitHub-safe visual evidence |
| Releases and tags | Preserve reviewable snapshots |

## Current Review Status

| Item | Status |
|---|---|
| README language | US English |
| Profile fit | Automation tooling and subtitle workflow scripting |
| Visual assets | Self-hosted SVG/GIF/PNG files under `assets/` |
| SVG text policy | English and ASCII-safe |
| Boundary note | No original anime/video media or full source subtitle redistribution |
| Release model | Latest release points reviewers to a stable source snapshot |

## HR Signals

- Clear repository description and topic taxonomy.
- Relevant topics: `aegisub`, `lua`, `moonscript`, `ass-subtitles`, `typesetting`, `karaoke-effects`.
- Release-backed README with visual evidence.
- Link back to the main GitHub profile and portfolio index.
- English documentation without encoding errors.

## Engineering Signals

- Clear separation between code, config, docs, examples and assets.
- Installation and verification commands where they matter.
- Dependency and copyright notes to avoid careless redistribution.
- Concrete macro/workflow examples rather than abstract claims.

## Next Improvements

| Priority | Work item |
|---|---|
| High | Add a self-generated cropped preview image from a synthetic ASS sample |
| High | Add a macro-load smoke test if an Aegisub CLI environment is available |
| Medium | Add macro origin/license notes when upstream headers are identifiable |
| Medium | Separate personal-only config from reusable config |
| Low | Add a demo GIF generated from a fully synthetic subtitle sample |
