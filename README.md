# NexName

[![Support on Ko-fi](https://img.shields.io/badge/Ko--fi-Support%20me-FF5E5B?logo=ko-fi&logoColor=white)](https://ko-fi.com/marcdev)

A Windows desktop app for **bulk-renaming files** by configurable rules — built with **WinUI 3 / Windows App SDK** for a modern Fluent look (Mica backdrop, the new `TitleBar`, Segoe Fluent icons).

## Download

Grab the latest **`NexName-<version>.zip`** from the [**Releases**](../../releases) page, unzip it anywhere, and run **`NexName.exe`**. It's self-contained — no .NET install required.

> On first launch Windows SmartScreen may show a "Windows protected your PC" prompt (the app is unsigned) — click **More info → Run anyway**.

## What it does

A two-pane window: the **file queue** (with a live preview of the new names) on the left, the **rule stack** on the right.

**Filling the queue**

- Drag files **and folders** from File Explorer onto the window, or use **Add folder…** / **Add files…**.
- **Include subfolders** toggle — when set, a dropped/picked folder pulls in files from its whole subtree (inaccessible folders are skipped, hidden files are kept, system files are skipped).
- Duplicate-safe (the same file added twice is ignored). **Remove selected** (multi-select) and **Clear all**.

**Building the rules** — add rules from the **Add rule** menu; they form a list of cards you can **drag to reorder** and **toggle on/off**. The new name = every enabled rule applied top-to-bottom. The rule types:

| Rule | What it does |
|---|---|
| **Find & replace** | Literal or **regex** (with `$1` capture references), match-case toggle, first-only / all, applies to name / extension / whole file name. Inline warning when the regex pattern is invalid. |
| **Add prefix / suffix** | Literal text before / after the base name. |
| **Numbering** | Sequential number — start / step / zero-pad width, before or after the name, custom separator, optional restart-the-count-in-each-folder. |
| **Change case** | lower / UPPER / Title / Sentence / iNVERT cASE, applied to name / extension / whole name. |
| **Clean up** | Trim, collapse repeated spaces, replace spaces with `_`/`-`/nothing, strip accents (`é`→`e`). |
| **Reformat date** | Find a date already in the name — auto-detect common patterns (`yyyy-MM-dd`, `yyyyMMdd`, `dd.MM.yyyy`, …; ambiguous orders read EU-first), pin a specific one, or supply a custom .NET format — and rewrite it in the format you choose. Optionally also captures the time after the date. |

**Preview, apply, undo**

- The "New name" column updates as you edit rules (debounced). A red ⚠ on a row means the new name would clash (with another file in the batch, or with a file already on disk) — hover it for the reason; those files are skipped on Apply.
- Whatever a rule produces is sanitized so it's always a legal Windows file name (illegal characters → `_`, trailing dots/spaces dropped, reserved device names like `CON` escaped).
- **Rename…** shows a confirmation with a few old → new examples, then performs the renames in two phases (so swaps like `a.txt`↔`b.txt`, cycles, and case-only changes all work). A results bar reports how many were renamed / failed.
- **Undo last rename** puts the batch back.
## Screenshots
<img width="1426" height="746" alt="1" src="https://github.com/user-attachments/assets/ce20282b-a8b9-4be0-bd97-928bb605ba56" />
<img width="1422" height="825" alt="2" src="https://github.com/user-attachments/assets/392c57c5-074d-4345-8736-d3c618a7e43d" />
<img width="1920" height="1032" alt="3" src="https://github.com/user-attachments/assets/637c2b5d-bb65-4efe-a1f2-c35ae1cd9393" />

## Requirements

- **Windows 10 version 1809 (build 17763)** or newer — Windows 11 recommended.
- Nothing else to install — the .NET runtime is bundled in the download.

## Support

NexName is free. If it saves you some clicking, you can buy me a coffee — genuinely appreciated, and it helps me keep building. ❤

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/marcdev)

## License

[MIT](LICENSE) © marcdev1220
