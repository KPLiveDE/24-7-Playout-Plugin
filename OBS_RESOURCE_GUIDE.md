# OBS Resource / Plugin Page

Diese Datei enthaelt fertige Texte fuer die OBS-Resource-Seite von `24/7 Playout`.

## Resource Title

```text
24/7 Playout
```

## Tag-line

```text
Automated 24/7 playout control for OBS Studio, Twitch streams, ads and transparent browser overlays.
```

## Tags

```text
24/7, playout, automation, twitch, rundown, playlist, scheduler, livestream, ads, overlay, browser source, media source, stream title, chat, category
```

## Overview - English

```markdown
# 24/7 Playout

24/7 Playout is an OBS Studio plugin for creators who want to run structured 24/7 livestreams with local video playlists, Twitch automation, ad handling and transparent stream overlays directly inside OBS.

The plugin helps you manage continuous playout inside OBS without relying on a separate broadcast tool. You can build a media library, create a playlist/rundown, display Now/Next information, place visual markers in the rundown and automatically update Twitch titles, Twitch categories, chat messages and ads based on the currently running program.

The control window opens from the OBS Tools menu via `Tools > 24/7 Playout`.

## Features

- Local media library for video files, folders and video links
- Drag and drop support for videos and folders
- Playlist / rundown management for continuous playout
- Planned start and end times based on the current rundown
- Live rundown timing updates during playback and video changes
- Visual rundown markers for user orientation without changing playback behavior
- Now / Next display with progress, remaining time and upcoming video information
- Automatic Twitch title updates per video or rundown entry
- Automatic Twitch category switching
- Automatic or custom chat messages per rundown entry
- Stream title prefix and suffix support
- Optional ad mode with Twitch ads, ad scene/program board mode or ads off
- Transparent program board overlay
- Transparent info banner overlay
- Transparent info graphic overlay per rundown entry
- Customizable and saved overlay colors
- Responsive overlays that keep their proportions at different browser source sizes
- Overlays can be placed above custom backgrounds, images, videos or stream graphics
- OBS scene integration for playout and ad scenes
- Dedicated OBS media source named `24/7 Playout Feed`
- Loop mode, shuffle mode, autostart and resume support
- Optional OBS stream auto-reconnect for long Twitch streams
- Configuration backup, restore, auto-recovery and safer saving
- English and German UI language support

## Twitch Automation

24/7 Playout can automatically update Twitch metadata to match the current program. This allows titles, categories and chat messages to change during the stream without manual interaction.

Supported automation includes:

- Automatic Twitch title updates on video changes
- Custom titles per rundown entry
- Prefix and suffix support for recurring title parts
- Automatic category switching
- Prepared chat messages per video or rundown entry
- Automatically generated chat notices such as "Now playing" and "Coming up"
- Twitch ad breaks, if the channel and authorization allow them
- Optional OBS stream auto-reconnect support for longer Twitch streams

## Transparent Overlays

The program board, info banner and info graphic are designed as transparent OBS browser overlays. This means you can freely place your own background below them in the OBS scene, such as a static image, animated background, video loop or custom stream design.

This keeps the overlays flexible for different stream styles while displaying playout information automatically and clearly.

Recommended browser source size:

`1920 x 1080`

The overlays are responsive, so their proportions stay intact even when a different source size is used.

## What is this plugin for?

24/7 Playout is intended for creators who want to run long-form or always-on streams, such as:

- 24/7 video channels
- archive or rerun streams
- gaming episode marathons
- music or ambient playouts
- scheduled community streams
- themed livestream blocks

## Installation

1. Close OBS Studio.
2. Download and extract the ZIP file.
3. Copy the contents of the `OBS-Studio` folder into your OBS Studio installation folder.
4. Merge folders when Windows asks.
5. Start OBS Studio.
6. Open `Tools > 24/7 Playout`.

## Requirements

- Windows 64-bit
- OBS Studio 32.x or compatible
- Twitch account and authorization for Twitch automation

## Notes

24/7 Playout keeps the playout workflow directly inside OBS and opens in a dedicated Tools window with enough space for larger rundowns and continuous stream operation.

This plugin is not affiliated with or endorsed by OBS Studio. For major updates, it is recommended to back up your existing configuration first.

Screenshots and setup examples can be added below.
```

## Overview - Deutsch

```markdown
# 24/7 Playout

24/7 Playout ist ein Plugin fuer OBS Studio. Es hilft Creatorn dabei, lange oder dauerhafte Playout-Streams direkt in OBS vorzubereiten und zu steuern.

Das Plugin wird ueber das OBS-Menue `Werkzeuge` geoeffnet und bietet ein eigenes Steuerfenster fuer Mediathek, Playlist/Rundown, Twitch-Automation, Werbung und Browser-Overlays.

## Funktionen

- Mediathek fuer lokale Videos, Ordnerimporte und Video-Links
- Drag and Drop fuer Videos und Ordner
- Playlist / Rundown mit berechneten Start- und Endzeiten
- Visuelle Marker im Rundown als reine Orientierung
- Now / Next-Anzeige mit Fortschritt und Restzeit
- Dedizierte OBS Media Source: `24/7 Playout Feed`
- Automatisches Einfuegen des Playout-Feeds in eine Szene
- Loop-Modus, Shuffle-Modus, Autostart und Fortsetzen des letzten Eintrags
- Metadaten pro Video fuer Stream-Titel, Chat-Nachrichten, Info-Grafik und Werbung
- Twitch-Integration fuer automatische Kategorie-Wechsel, Stream-Titel, Chat-Nachrichten und Werbepausen
- Werbe-Modi fuer Twitch-Werbung, nur Szene/Programmtafel oder keine Werbung
- Transparente und responsive Browserquellen fuer Programmtafel, Info-Banner und Info-Grafik
- Eigene Overlay-Farben fuer Programmtafel und Info-Banner
- Deutsch/Englisch umschaltbare Oberflaeche
- Konfigurationsschutz mit Backups, Auto-Wiederherstellung und sichererem Speichern

## Transparente Browserquellen

Die Programmtafel ist transparent. Dadurch kannst du in OBS eigene Hintergrundbilder, Videos oder Szenen darunter legen.

Empfohlene Browserquellen-Groesse:

`1920 x 1080`

Die Overlays sind responsive, sodass die Proportionen auch bei anderen Quellgroessen erhalten bleiben.

## Twitch-Automation

Nach der Twitch-Autorisierung kann das Plugin automatisch:

- den Stream-Titel aktualisieren
- die Twitch-Kategorie wechseln
- Chat-Nachrichten pro Video senden
- Twitch-Werbepausen starten

## Installation

1. OBS Studio schliessen.
2. ZIP herunterladen und entpacken.
3. Inhalt des Ordners `OBS-Studio` in den OBS-Studio-Installationsordner kopieren.
4. Ordner beim Kopieren zusammenfuehren.
5. OBS Studio starten.
6. `Werkzeuge > 24/7 Playout` oeffnen.

## Voraussetzungen

- Windows 64-bit
- OBS Studio 32.x oder kompatibel
- Twitch-Konto und Autorisierung fuer Twitch-Automation

## Hinweis

24/7 Playout haelt den Playout-Workflow direkt in OBS und oeffnet ein eigenes Werkzeuge-Fenster mit genug Platz fuer groessere Rundowns und den Dauerbetrieb.

Dieses Plugin ist nicht offiziell mit OBS Studio verbunden.
Vor groesseren Updates wird empfohlen, die bestehende Konfiguration zu sichern.
```

## Changelog fuer v0.8.18

```markdown
## 24/7 Playout v0.8.18

### New

- Plugin window opens from the OBS Tools menu.
- Technical module/package name changed to `playout-247-plugin` to avoid using OBS in the primary plugin name.
- Visual rundown markers replace the old chapter/daypart scheduling workflow.
- Markers can be moved, selected and removed like playlist entries.
- Browser overlays keep their proportions responsively.

### Improved

- German/English UI language coverage expanded.
- Visible playback/status logs are translated more consistently.
- Now/Next time labels use English wording when the English interface is active.
- Program board, info banner and info graphic remain transparent/responsive for OBS browser sources.
- README, installation docs and release packaging were updated for the new name and file layout.

### Fixed

- Rundown no longer disappears when working with former chapter/marker workflows.
- Marker deletion now removes the marker from the internal data as well.
- Delete-key confirmation is localized.

### Notes

- Recommended browser source size for program board, info banner and info graphic: `1920 x 1080`.
- The Full package contains `ffmpeg.exe` and debug symbols.
- The Slim package omits `ffmpeg.exe` and `.pdb` files for a smaller GitHub upload.
```

## Upload-Hinweise

- Fuer OBS-Plugins/OBS-Forum: `24-7-Playout-v0.8.18-windows-x64-full.zip`
- Fuer GitHub Release: `24-7-Playout-v0.8.18-windows-x64-slim.zip`
- Repository: `https://github.com/KPLiveDE/24-7-Playout-OBS-Plugin`
- OBS Resource: `https://obsproject.com/forum/resources/24-7-playout-obs-plugin.2530/`

Wenn die OBS-Resource-Seite den Namen der URL nicht sofort aendert, ist das normal. Wichtig ist der sichtbare Resource-Titel `24/7 Playout`.
