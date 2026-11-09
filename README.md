# GrannyForge

**Granny `.gr2` editor for Metin2** — preview models, select individual parts (logos, texts, tails, armor pieces), remove what you don’t need, and save a clean GR2.

Built by [ShayRed](https://github.com/ShayRed) · Windows · .NET 8 · x86 (32-bit `granny2.dll`)

[![Release](https://img.shields.io/github/v/release/ShayRed/GrannyForge?style=flat-square)](https://github.com/ShayRed/GrannyForge/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/ShayRed/GrannyForge/total?style=flat-square)](https://github.com/ShayRed/GrannyForge/releases)
[![License](https://img.shields.io/badge/license-see%20repo-lightgrey?style=flat-square)](#license)

---

## Showcase

### Video

> **So dockst du ein YouTube-Video an:**  
> 1. Video hochladen → Link kopieren, z. B. `https://youtu.be/dQw4w9WgXcQ`  
> 2. Nur die **Video-ID** nehmen (`dQw4w9WgXcQ`)  
> 3. Unten `YOUTUBE_VIDEO_ID` durch diese ID ersetzen  
> 4. Optional: eigenes Vorschaubild unter `docs/media/youtube-thumb.jpg` legen und die Thumbnail-URL anpassen

<!-- ========== YOUTUBE: Video-ID hier einsetzen ========== -->
[![GrannyForge – Demo / Tutorial](https://img.youtube.com/vi/YOUTUBE_VIDEO_ID/maxresdefault.jpg)](https://www.youtube.com/watch?v=YOUTUBE_VIDEO_ID)

*Klick auf das Bild öffnet das Video auf YouTube.*

<!-- Zweites Video (optional) – Block kopieren und ID tauschen:
[![GrannyForge – Teil 2](https://img.youtube.com/vi/YOUTUBE_VIDEO_ID_2/maxresdefault.jpg)](https://www.youtube.com/watch?v=YOUTUBE_VIDEO_ID_2)
-->

### Screenshots

> **So dockst du Bilder an:**  
> Dateien nach `docs/media/` legen (PNG/JPG), Namen wie unten — oder Pfade in den `![](...)`-Links anpassen.  
> Lokal: `docs/media/preview.png` · Extern: `https://i.imgur.com/....png`

| 3D-Vorschau | Teile markieren |
| :---: | :---: |
| ![3D preview](docs/media/preview.png) | ![Part selection](docs/media/parts-select.png) |

| Mesh-Liste | Logo / Text entfernen |
| :---: | :---: |
| ![Mesh list](docs/media/meshes-list.png) | ![Logo cleanup](docs/media/logo-remove.png) |

<!-- Einzelbild über die volle Breite (optional):
![GrannyForge UI](docs/media/ui-full.png)
-->

---

## Features

- **Textured 3D preview** — orbit, pan, zoom; Metin2 DDS/TGA/PNG next to the GR2
- **Part picking** — click a logo letter, tail, or armor piece; mark red; remove triangles only
- **Parts list** — same selectable islands in a sidebar tab (filter by texture name, e.g. `logo`)
- **Mesh & animation cleanup** — multi-select, prune unused materials/textures/topology
- **Safe saves** — optional `.bak`, reload check after write
- **GitHub auto-update** — downloads only changed files (SHA-256), with staging + rollback
- **Rest-pose skinning** — armor/body pieces display correctly in bind pose

---

## Download

1. Open **[Releases](https://github.com/ShayRed/GrannyForge/releases/latest)**
2. Download `GrannyForge-*-win-x86.zip` (or use the in-app updater after the first install)
3. Unpack and run `GrannyForge.exe`

`granny2.dll` (2.11.8, 32-bit) is included in the release package.

---

## Quick start

1. Start **GrannyForge.exe**
2. Drop a `.gr2` onto the window (or **Öffnen…**)
3. Use the **Vorschau** on the right: click parts to mark them
4. Or open the **Teile** tab → filter → check parts → **Teile entfernen**
5. **Speichern unter…** when you’re done

| Control | Action |
| --- | --- |
| Drag LMB | Rotate |
| Mouse wheel | Zoom |
| MMB / Shift+LMB / RMB | Pan |
| Click part | Toggle red mark |
| **Teile entfernen** | Delete marked triangles |
| **Teile färben** | Color each pickable island |
| **Ganzes Mesh** | Click selects the full mesh instead |

Changes stay in memory until you save. **Neu laden** discards unsaved edits.

---

## Build from source

**Requirements:** Visual Studio 2022 (17.8+) with *.NET desktop development*, .NET 8 SDK, 32-bit `granny2.dll` 2.11.8.

```bat
git clone https://github.com/ShayRed/GrannyForge.git
cd GrannyForge
:: optional for Debug: copy granny2.dll into lib\
dotnet build GrannyForge.sln -c Release
src\GrannyForge.Desktop\bin\Release\net8.0-windows\GrannyForge.exe
```

The desktop app targets **x86** so it can load the game’s 32-bit Granny DLL.

---

## Publishing a release (maintainers)

```bat
:: Token only on your PC — never in the app
set GITHUB_TOKEN=ghp_...
upload_release.bat
```

Or put the token in `Git\Token.txt` (gitignored). Useful flags: `--dry-run`, `--skip-build`, `--replace`, `-y`.

Version = `<Version>` in `Directory.Build.props`. Only **changed** binaries are uploaded (plus manifest + full zip).

---

## Project layout

```
GrannyForge.sln
Directory.Build.props
docs/
  media/                 ← screenshots & video thumbs (for this README)
  ARCHITECTURE.md
lib/                     ← local granny2.dll (not committed)
src/
  GrannyForge.Core/      ← native interop, GR2 edit, preview math
  GrannyForge.Updates/   ← GitHub release client / install
  GrannyForge.Desktop/   ← WPF UI
tools/
  GrannyForge.Publish/   ← upload_release.bat backend
tests/
  GrannyForge.Core.Tests/
```

---

## Limits

- Preview = rest/bind pose (skinned), no animation playback
- No FBX/DAE import/export (yet)
- No mesh rename/merge/rebuild beyond triangle/mesh removal
- Layout offsets assume Granny **2.11.8** (`NativeLayout.cs`)

---

## License

Application code: see repository / author terms.

`granny2.dll` is a proprietary RAD / Epic Games Tools runtime as used by Metin2 clients. Redistribute only in line with your own rights and the game’s ecosystem practices.

---

## Author

**Shay** ([@ShayRed](https://github.com/ShayRed))

Issues and ideas: [GitHub Issues](https://github.com/ShayRed/GrannyForge/issues)

---

### Media checklist (for you)

| Slot | File / placeholder | Status |
| --- | --- | --- |
| YouTube main | `YOUTUBE_VIDEO_ID` in this README | replace |
| Screenshot preview | `docs/media/preview.png` | add file |
| Screenshot parts | `docs/media/parts-select.png` | add file |
| Screenshot meshes | `docs/media/meshes-list.png` | add file |
| Screenshot logo | `docs/media/logo-remove.png` | add file |
| Optional full UI | `docs/media/ui-full.png` | optional |
