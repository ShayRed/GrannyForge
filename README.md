# GrannyForge

**Granny `.gr2` editor for Metin2** — preview models in 3D, click individual parts (logos, texts, tails, armor pieces), remove what you don’t need, and save a clean GR2.

Built by [ShayRed](https://github.com/ShayRed) · Windows · .NET 8 · x86 (`granny2.dll` 2.11.8)

[![Release](https://img.shields.io/github/v/release/ShayRed/GrannyForge?style=flat-square)](https://github.com/ShayRed/GrannyForge/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/ShayRed/GrannyForge/total?style=flat-square)](https://github.com/ShayRed/GrannyForge/releases)

---

## What it looks like

![GrannyForge – tool preview](https://i.ibb.co/HLzXSz2K/Granny-Forge-u3-Eg-Ht-Ou0a.png)

*Textured 3D preview, mesh list, and part picking — open a `.gr2`, mark logos/texts, remove them, save.*

---

## Video demo

[![GrannyForge – Demo](https://img.youtube.com/vi/RZG3jWNyvBc/maxresdefault.jpg)](https://youtu.be/RZG3jWNyvBc)

**[▶ Watch on YouTube](https://youtu.be/RZG3jWNyvBc)** — short walkthrough of the tool in action.

---

## Why GrannyForge?

Metin2 (and other Granny-based) models often ship with extra junk: logos, watermarks, texts on armor, unused meshes, leftover animations. GrannyForge lets you **see** the model and **cut only what you want** — without re-exporting through Max/Blender and breaking the file format.

| You can… | How |
| --- | --- |
| See the model textured | Live 3D preview (DDS / TGA / PNG next to the GR2) |
| Remove a logo letter by letter | Click parts in the preview (or use the **Teile** tab) |
| Delete whole meshes / animations | Checkboxes → remove → save |
| Keep the rest intact | Skeleton, skinning, materials of remaining geometry stay |
| Stay up to date | Built-in GitHub update (only changed files) |

---

## Features

- **Textured 3D preview** — rotate, pan, zoom; rest-pose skinning for armor
- **Part picking** — mark islands red (logo, text, tail, clothing piece) and delete those triangles
- **Parts list** — filter by texture name (e.g. `logo`), same selection as the 3D view
- **Mesh & animation cleanup** — multi-select + optional prune of unused data
- **Safe save** — optional `.bak`, verify after write
- **Auto-updater** — public GitHub Releases, SHA-256 checks, rollback on failure

---

## Download

1. Open **[Latest Release](https://github.com/ShayRed/GrannyForge/releases/latest)**
2. Download `GrannyForge-*-win-x86.zip`
3. Unpack → run `GrannyForge.exe`

`granny2.dll` is included in the release zip.

---

## Quick start

1. Start **GrannyForge.exe**
2. Drop a `.gr2` onto the window (or **Öffnen…**)
3. In the **Vorschau**: click a part → it turns red → **Teile entfernen**
4. Or open the **Teile** tab → filter → check → remove
5. **Speichern unter…**

| Control | Action |
| --- | --- |
| Drag LMB | Rotate |
| Mouse wheel | Zoom |
| MMB / Shift+LMB / RMB | Pan |
| Click part | Toggle mark |
| **Teile entfernen** | Delete marked triangles |
| **Teile färben** | Color each pickable part |
| **Ganzes Mesh** | Click selects the full mesh |

Edits stay in memory until you save. **Neu laden** discards unsaved changes.

---

## Build from source

**Needs:** VS 2022 (.NET desktop), .NET 8 SDK, 32-bit Granny 2.11.8.

```bat
git clone https://github.com/ShayRed/GrannyForge.git
cd GrannyForge
dotnet build GrannyForge.sln -c Release
src\GrannyForge.Desktop\bin\Release\net8.0-windows\GrannyForge.exe
```

The app is **x86** so it can load the game’s 32-bit `granny2.dll`.

---

## Publish a release (maintainers)

```bat
set GITHUB_TOKEN=ghp_...
upload_release.bat
```

Token only on your machine (`Git\Token.txt` or env). Flags: `--dry-run`, `--skip-build`, `--replace`, `-y`.  
Version = `<Version>` in `Directory.Build.props`.

---

## Project layout

```
src/GrannyForge.Core/       native Granny interop, edit, preview
src/GrannyForge.Updates/    GitHub update client
src/GrannyForge.Desktop/    WPF UI
tools/GrannyForge.Publish/  release uploader (upload_release.bat)
tests/                      xUnit
docs/                       docs + media notes
```

---

## Limits

- Preview = bind/rest pose (no animation playback)
- No FBX/DAE bridge yet
- Offsets target Granny **2.11.8**

---

## License / notes

App code: see repo / author.  
`granny2.dll` is the proprietary Granny runtime as used by Metin2 clients.

---

## Author

**Shay** — [github.com/ShayRed](https://github.com/ShayRed)

Issues: [github.com/ShayRed/GrannyForge/issues](https://github.com/ShayRed/GrannyForge/issues)
