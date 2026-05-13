# Aegisub Automation Pack

Personal Aegisub automation and macro setup for fansub/typesetting work.

This repo keeps the useful, reusable parts of my Aegisub setup: Automation scripts, include libraries, macro configs, hotkeys, and small tool configuration files. Personal subtitle backups, autosaves, logs, crash dumps, recent-file history, and machine-local paths are intentionally ignored.

## Included

- `automation/autoload/` - Lua/Moonscript macros loaded automatically by Aegisub.
- `automation/include/` - shared libraries used by the macros.
- `config/` - macro/plugin-specific configuration files.
- `zeref-cfg/` - Zeref-related macro config.
- `hotkey.json` - Aegisub hotkey configuration.
- `colourise.conf`, `masquerade.conf`, `recalculator.conf` - tool-specific config files.

## Not Included

The following are intentionally excluded because they contain private work files, local paths, generated data, or runtime state:

- `autoback/`
- `autosave/`
- `recovered/`
- `log/`
- `crashdumps/`
- `feedDump/`
- `catalog/`
- `mru.json`
- `config.json`
- `shift_history.json`
- `aegisub-motion.json`
- `aegisub-motion.stats.json`

## Notable Macros

- `ua.HYDRA.lua`
- `ua.Relocator.lua`
- `ua.FadeWorks.lua`
- `ua.Masquerade.lua`
- `ua.Colorize.lua`
- `ILL.Shapery.moon`
- `a-mo.Aegisub-Motion.moon`
- `petzku.EncodeClip.lua`
- `lyger.Image2ASS.lua`
- `zah.aegi-color-track.lua`

## Install

Copy or clone this repo into the Aegisub roaming config folder:

```powershell
$env:APPDATA\Aegisub
```

Then restart Aegisub so it reloads the automation scripts.

## Notes

Some automation packages include third-party helper libraries and native binaries required by their macros. Keep the directory structure unchanged so `autoload` scripts can resolve their dependencies under `automation/include`.
