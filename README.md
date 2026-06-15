# 24/7 Playout v0.8.19 - OBS Plugin

24/7 Playout is an OBS Studio plugin that helps creators run structured 24/7 streams by combining media library management, playlist/rundown playback, live timing, Twitch metadata automation, chat messages, ad handling and transparent browser overlays directly inside OBS.

This release provides the Windows x64 installer and the Windows x64 ZIP package. The ZIP package includes the plugin DLL, debug symbols, `yt-dlp.exe`, `ffmpeg.exe`, documentation and the GPL license file.


## Screenshots

### Main control window

![24/7 Playout main control window](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-OBS-Plugin/28bdc4b1dd3aef3cc2f2abf65403ce606d1e2208/img/Screenshot%202026-06-13%20151008.png)

### Interface and overlay examples

![24/7 Playout interface screenshot 1](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-OBS-Plugin/28bdc4b1dd3aef3cc2f2abf65403ce606d1e2208/img/Screenshot%202026-06-12%20202907.png)

![24/7 Playout interface screenshot 2](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-OBS-Plugin/28bdc4b1dd3aef3cc2f2abf65403ce606d1e2208/img/Screenshot%202026-06-12%20203101.png)

![24/7 Playout overlay screenshot 1](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-OBS-Plugin/28bdc4b1dd3aef3cc2f2abf65403ce606d1e2208/img/Screenshot%202026-06-12%20203848.png)

![24/7 Playout overlay screenshot 2](https://github.com/KPLiveDE/24-7-Playout-OBS-Plugin/blob/28bdc4b1dd3aef3cc2f2abf65403ce606d1e2208/img/Screenshot%202026-06-12%20203821.png)

### Twitch Integration and Video Edit

![24/7 Playout overlay screenshot 2](https://github.com/KPLiveDE/24-7-Playout-OBS-Plugin/blob/28bdc4b1dd3aef3cc2f2abf65403ce606d1e2208/img/Screenshot%202026-06-12%20203635.png)

![24/7 Playout overlay screenshot 2](https://github.com/KPLiveDE/24-7-Playout-OBS-Plugin/blob/28bdc4b1dd3aef3cc2f2abf65403ce606d1e2208/img/Screenshot%202026-06-12%20204021.png)

![24/7 Playout overlay screenshot 2](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-OBS-Plugin/28bdc4b1dd3aef3cc2f2abf65403ce606d1e2208/img/Screenshot%202026-06-12%20204036.png)

![24/7 Playout overlay screenshot 2](https://github.com/KPLiveDE/24-7-Playout-OBS-Plugin/blob/28bdc4b1dd3aef3cc2f2abf65403ce606d1e2208/img/Screenshot%202026-06-12%20203657.png)

## Highlights

- OBS Tools menu integration via `Tools > 24/7 Playout`
- Local media library for videos, folders and video links
- Drag and drop support for videos and folders
- Playlist / rundown management for continuous playout
- Planned start and end times based on the current rundown
- Live rundown timing updates during playback and video changes
- Visual rundown markers for orientation without changing playback behavior
- Now / Next display with progress, remaining time and upcoming video information
- Dedicated OBS media source named `24/7 Playout Feed`
- OBS scene integration for playout and ad scenes
- Twitch automation for stream titles, categories, chat messages and ad breaks
- Stream title prefix and suffix support
- Optional ad mode with Twitch ads, ad scene/program board mode or ads off
- Transparent and responsive browser overlays for program board, info banner and info graphic
- Customizable overlay colors
- Loop mode, shuffle mode, autostart and resume support
- Optional OBS stream auto-reconnect for long Twitch streams
- English and German UI language support
- Configuration backup, restore, auto-recovery and safer saving

## Installation

### Option 1: Installer

1. Close OBS Studio completely.
2. Download and run `24-7-Playout-v0.8.18-windows-x64-installer.exe`.
3. Select your OBS Studio installation folder.
4. Complete the installation.
5. Start OBS Studio.
6. Open `Tools > 24/7 Playout`.

### Option 2: Manual ZIP Installation

1. Close OBS Studio completely.
2. Download `24-7-Playout-v0.8.18-windows-x64.zip`.
3. Extract the ZIP file.
4. Copy the contents of the `OBS-Studio` folder into your OBS Studio installation folder.
5. Merge folders when Windows asks.
6. Start OBS Studio.
7. Open `Tools > 24/7 Playout`.

The installed structure should look like this:

```text
OBS-Studio/
  obs-plugins/
    64bit/
      playout-247-plugin.dll
      playout-247-plugin.pdb
  data/
    obs-plugins/
      playout-247-plugin/
        ffmpeg.exe
        yt-dlp.exe
        locale/
          en-US.ini
```

## Browser Sources

The program board, info banner and info graphic are transparent, responsive OBS browser overlays. They can be used at different browser source sizes while keeping their proportions intact, and can be placed above custom backgrounds, images, videos or stream graphics.



## Notes

- This is a Windows x64 release.
- OBS Studio 32.x or a compatible version is recommended.
- Twitch automation requires Twitch authorization inside the plugin.
- After updating the plugin, restart OBS Studio completely.
- Source code is available in this repository.

## Download

Recommended for most Windows users:

```text
24-7-Playout-v0.8.19-windows-x64-installer.exe
```

Manual installation package:

```text
24-7-Playout-v0.8.19-windows-x64.zip
```

Source code archive:

```text
24-7-Playout-v0.8.19-source.zip
```
