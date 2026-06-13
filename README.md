# 24/7 Playout

Current version: `0.8.18`

`24/7 Playout` is an OBS Studio plugin for creators who want to prepare and control long-form or always-on livestreams directly inside OBS.

The plugin opens from the OBS Tools menu via `Tools > 24/7 Playout` and provides a dedicated control window for media library management, playlist/rundown playback, ads, Twitch automation and browser overlays.

## Features

- Media library for local videos, folder imports and video links
- Drag and drop support for local videos and folders
- Playlist / rundown with planned start and end times
- Visual markers directly inside the rundown for orientation only, without affecting playback or sorting
- Markers can be moved, selected and removed
- Now / Next display with progress and remaining time
- Dedicated OBS media source named `24/7 Playout Feed`
- Automatic insertion of the playout feed into the current OBS scene
- Loop mode, shuffle mode, autostart and optional resume support
- Per-rundown-entry metadata for custom stream titles, video-name titles, chat messages, info graphics and ads after videos
- Stream title prefix and suffix support with custom separators, including spaces or emojis
- Twitch integration for automatic category changes, stream title updates, chat messages and Twitch ad breaks
- Twitch OAuth directly from the plugin, including status information for missing scopes
- Ad modes for Twitch ads, ad scene/program board mode or ads off
- Dedicated OBS ad scene with pre-roll and post-roll timing
- Browser overlays for program board, info banner and info graphic
- Transparent program board, so custom backgrounds or scenes can remain visible underneath
- Responsive browser overlays that keep their proportions at different source sizes
- Custom overlay colors for program board and info banner, including color picker and saved settings
- English and German UI language support
- Configuration protection with backup copy, auto-recovery and safer atomic saving
- Configuration import, export and backup restore
- Keyboard shortcuts for lists, search, selection and removal

## Installation

1. Close OBS Studio completely.
2. Download and extract the ZIP file.
3. Copy the contents of the `OBS-Studio` folder into your OBS Studio installation folder.
4. Merge folders when Windows asks.
5. Start OBS Studio.
6. Open `Tools > 24/7 Playout`.

The target structure should look like this:

```text
OBS-Studio/
  obs-plugins/
    64bit/
      playout-247-plugin.dll
  data/
    obs-plugins/
      playout-247-plugin/
        yt-dlp.exe
        ffmpeg.exe   optional, included only in the Full package
        locale/
          en-US.ini
```

## Full And Slim Packages

The Full package is intended for OBS plugin/resource uploads and contains:

- Plugin DLL
- Debug symbols (`.pdb`)
- `yt-dlp.exe`
- `ffmpeg.exe`
- Documentation and license

The Slim package is intended for GitHub or smaller downloads and does not include `.pdb` files or `ffmpeg.exe`.

If needed, `ffmpeg.exe` can be installed manually from the official FFmpeg website:

```text
https://www.ffmpeg.org/download.html
```

Then place the file here:

```text
OBS-Studio\data\obs-plugins\playout-247-plugin\ffmpeg.exe
```

## Browser Overlays

The browser overlays should be added to OBS as Browser Sources. Recommended size:

```text
1920 x 1080
```

The overlays are responsive. Other source sizes also work, while the proportions stay intact.

The program board is transparent and can be placed above custom images, videos or scenes in OBS.

## Twitch

Twitch features require authorization inside the plugin. After authorization, the plugin can automatically:

- Update the stream title
- Switch the Twitch category
- Send per-video chat messages
- Start Twitch ad breaks

Used scopes:

```text
channel:manage:broadcast channel:edit:commercial chat:read chat:edit user:write:chat
```

## Build Notes

The current local build was created with the official template dependency state `obs-studio 31.1.1`.

Typical build:

```powershell
cmake -S . -B build
cmake --build build --config RelWithDebInfo
```

Current build output:

```text
build-template\RelWithDebInfo\playout-247-plugin.dll
dist\OBS-Studio\obs-plugins\64bit\playout-247-plugin.dll
```

## Create Release Packages

```powershell
.\tools\package-release.ps1
```

To overwrite existing release artifacts:

```powershell
.\tools\package-release.ps1 -Overwrite
```

## Versioning

- Visible plugin version: `src/plugin-version.hpp`
- Build/package version: `buildspec.json`
- Project notes: `PROJECT_MEMORY.md`

## License

This project is licensed under the GNU General Public License v2.0 or later.
See the `LICENSE` file for details.
