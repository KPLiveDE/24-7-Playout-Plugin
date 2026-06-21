# 24/7 Playout - OBS Plugin

24/7 Playout is an OBS Studio plugin that helps creators run structured 24/7 streams by combining media library management, playlist/rundown playback, live timing, Twitch metadata automation, chat messages, Discord notifications, web widgets, ad handling, transparent browser overlays and optional live-feed integration directly inside OBS.

The plugin supports local videos, folders, external video links, Twitch VODs and live-feed sources inside the same rundown. It can automatically update Twitch titles, categories and chat messages, display Now / Next information, manage ads and provide transparent overlays that can be placed above custom backgrounds, videos or stream graphics.

This release provides the Windows x64 installer and the Windows x64 ZIP package. The full package includes the plugin DLL, debug symbols, `yt-dlp.exe`, `ffmpeg.exe`, `mediamtx.exe`, documentation and the GPL license file.

---

## Screenshots

### Main control window

![24/7 Playout main control window](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-Plugin/refs/heads/main/img/Screenshot%202026-06-21%20115138.png)
![24/7 Playout Planning Calendar](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-Plugin/refs/heads/main/img/Screenshot%202026-06-21%20115242.png)

### Discord notifications and web widget

![Discord WebSocket Notifications](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-Plugin/refs/heads/main/img/Screenshot%202026-06-21%20115550.png)

![24/7 Playout Web Widget](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-Plugin/refs/heads/main/img/Screenshot%202026-06-21%20115050.png)

### Interface and overlay examples

![24/7 Playout interface screenshot 1](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-Plugin/main/img/Screenshot%202026-06-12%20202907.png)

![24/7 Playout interface screenshot 2](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-Plugin/main/img/Screenshot%202026-06-12%20203101.png)

![24/7 Playout overlay screenshot 2](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-Plugin/refs/heads/main/img/Screenshot%202026-06-21%20115319.png)

### Twitch integration and metadata

![24/7 Playout Twitch screenshot 1](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-Plugin/main/img/Screenshot%202026-06-12%20203635.png)

![24/7 Playout Twitch screenshot 2](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-Plugin/main/img/Screenshot%202026-06-12%20204021.png)

![24/7 Playout Twitch screenshot 3](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-Plugin/main/img/Screenshot%202026-06-12%20204036.png)

![24/7 Playout Twitch screenshot 4](https://raw.githubusercontent.com/KPLiveDE/24-7-Playout-Plugin/main/img/Screenshot%202026-06-12%20203657.png)

---

## Highlights

- OBS Tools menu integration via `Tools > 24/7 Playout`
- Local media library for videos, folders, video links, Twitch VODs and live-feed entries
- Drag and drop support for videos and folders
- Playlist / rundown management for continuous playout
- Calendar overview for the playlist / rundown
- Planned start and end times based on the current rundown
- Live rundown timing updates during playback and video changes
- Visual rundown markers for orientation without changing playback behavior
- Copy and paste support for playlist entries and markers
- Right-click actions for playlist entries such as copy, paste, duplicate, edit and remove
- Optional automatic scrolling to the currently active rundown entry
- Now / Next display with progress, remaining time and upcoming video information
- Twitch VOD metadata detection including title, duration, resolution and preview thumbnail
- Live-feed entries with configurable runtime and signal status display
- Optional local MediaMTX live server integration for RTMP, SRT, RTSP and WebRTC workflows
- Dedicated OBS media source named `24/7 Playout Feed`
- OBS scene integration for playout and ad scenes
- Twitch automation for stream titles, categories, chat messages and ad breaks
- Per-entry Twitch category field directly in the metadata editor
- Stream title prefix and suffix support
- Optional ad mode with Twitch ads, ad scene/program board mode or ads off
- Transparent and responsive browser overlays for program board, info banner and info graphic
- Customizable overlay colors
- Loop mode, shuffle mode, autostart and resume support
- Optional OBS stream auto-reconnect for long Twitch streams
- English and German UI language support
- Configuration backup, restore, auto-recovery and safer saving
- Discord WebSocket integration for automatic notifications
- Notifications when videos or rundown entries change
- Web widget for showing current and next playback content
- Automatic grouping of consecutive videos by Twitch category in the web widget
- Built-in Twitch chat commands (`!now`, `!next`, `!schedule`, `!commands`)
- Customizable chat commands
- Optional moderator-only command mode
- Chat command cooldown system to prevent spam
- Completely redesigned settings interface with subtabs
- New UI themes: Standard, Dark, Gray, Twitch Mode
- Calendar updates now refresh instantly on playlist changes
- Fixed German and English translations across multiple UI areas
- Added proper German umlaut support

---

## Installation

### Option 1: Installer

1. Close OBS Studio completely.
2. Download and run the Windows x64 installer.
3. Select your OBS Studio installation folder.
4. Complete the installation.
5. Start OBS Studio.
6. Open `Tools > 24/7 Playout`.

### Option 2: Manual ZIP Installation

1. Close OBS Studio completely.
2. Download the Windows x64 ZIP package.
3. Extract the ZIP file.
4. Copy the contents of the `OBS-Studio` folder into your OBS Studio installation folder.
5. Merge folders when prompted.
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
        mediamtx.exe
        locale/
          en-US.ini
          de-DE.ini

          
```

## Browser Sources

The program board, info banner and info graphic are transparent, responsive OBS browser overlays. They can be used at different browser source sizes while keeping their proportions intact, and can be placed above custom backgrounds, images, videos or stream graphics.

## Notes

- This is a Windows x64 release.
- OBS Studio 32.x or a compatible version is recommended.
- Twitch automation requires Twitch authorization inside the plugin.
- Live-feed workflows can optionally use the included local MediaMTX server.
- After updating the plugin, restart OBS Studio completely.
- Source code is available in this repository.

## Download

Recommended for most Windows users:

```text
Windows x64 installer
```

Manual installation package:

```text
Windows x64 ZIP package
```

Source code archive:

```text
Source ZIP package
```
