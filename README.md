<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&height=165&text=LayFix&fontSize=42&fontAlignY=35&animation=fadeIn&fontColor=FFFFFF&color=0:0F1115,45:1C1C1C,100:2D5BFF"/>

<br>

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=500&size=15&pause=1200&color=2D5BFF&center=true&vCenter=true&width=720&lines=Instant+Arabic+and+English+keyboard+layout+fixer...;Tray-first+lightweight+workflow...;Fast+local-only+conversion..." />

<br><br>

<img src="https://img.shields.io/badge/Windows-2D5BFF?style=for-the-badge&logo=windows&logoColor=white">
<img src="https://img.shields.io/badge/.NET%208-1C1C1C?style=for-the-badge">
<img src="https://img.shields.io/badge/Local%20Only-2D5BFF?style=for-the-badge">

</div>

---

# LayFix

LayFix is a lightweight tray-first utility that fixes accidental Arabic and English keyboard layout mistakes directly inside selected text.

Select text anywhere, press the shortcut, and LayFix replaces only the selected content with the corrected version.

No cloud conversion.
No telemetry.

---

# Features

* Tray-first workflow
* Selected-text replacement only
* Clipboard Convert mode
* Dark / Light / Follow System themes
* Global shortcuts
* Settings panel
* Optional History
* Startup with Windows toggle
* Local-only conversion
* No telemetry or analytics

---

# Examples

## Arabic typed on English layout

```text id="m4t7xk"
hgsghl ugd;l
```

Result:

```text id="p8w0fa"
السلام عليكم
```

---

## English typed on Arabic layout

```text id="d1n5qe"
اثممخ LayFix
```

Result:

```text id="u9v2wc"
hello LayFix
```

---

## Mixed Text

```text id="f3k8zb"
pdh fhg; LayFix
```

Result:

```text id="y2m4qx"
حيا بالك LayFix
```

---

# Usage

1. Launch LayFix
2. Find the icon in the system tray
3. Select text in any application
4. Press the conversion shortcut
5. LayFix replaces only the selected text

Default shortcut:

```text id="r7p1ls"
Ctrl + Alt + F9
```

---

# Tray Menu

```text id="s4q9vu"
Settings
Clipboard Convert
About
Check for Updates
Exit
```

---

# Privacy

LayFix is designed to stay local.

* No telemetry
* No analytics
* No cloud conversion
* No text uploading
* No automatic history storage

`Check for Updates` only connects to GitHub Releases when triggered manually by the user.

---

# Project Structure

```text id="q8w6af"
LayFix/
  README.md
  LayFix.sln

  src/
    LayFix.Core/
    LayFix.Windows/
    LayFix.Linux/

  tests/
    LayFix.Core.Tests/
    LayFix.Windows.IntegrationTests/

  installer/
    LayFix.wxs

  release/
    LayFix-portable.exe
    LayFix-installer.msi
    LayFix-linux-x64
```

---

# Releases

GitHub tag:

```text id="x2m9ot"
v1.0.0
```

Suggested release title:

```text id="v5f8qe"
LayFix v1.0.0 Stable
```

Release assets:

```text id="n1k4wy"
LayFix-portable.exe
LayFix-installer.msi
LayFix-linux-x64
LayFix-release.zip
```

---

# Linux Build

```powershell id="z6u3pn"
dotnet publish src\LayFix.Linux\LayFix.Linux.csproj `
  -c Release `
  -r linux-x64 `
  --self-contained false `
  -p:PublishSingleFile=true `
  -o artifacts\publish\LayFix-linux-x64
```

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&height=100&section=footer&color=0:2D5BFF,100:0F1115"/>

</div>
