# 24/7 Playout

Aktuelle Version: `0.8.18`

`24/7 Playout` ist ein Drittanbieter-Plugin fuer OBS Studio. Es richtet sich an Creator, die lange oder dauerhafte Playout-Streams vorbereiten und direkt in OBS steuern moechten.

Das Plugin oeffnet seine Oberflaeche ueber `Werkzeuge > 24/7 Playout` und verwaltet Mediathek, Playlist/Rundown, Werbung, Twitch-Automation und Browser-Overlays in einem eigenen Fenster.

## Hauptfunktionen

- Mediathek fuer lokale Videos, Ordnerimporte und Video-Links.
- Drag and Drop fuer lokale Videos und Ordner in die Mediathek.
- Playlist/Rundown mit geplanten Start- und Endzeiten.
- Visuelle Marker direkt im Rundown als reine Orientierung, ohne Einfluss auf Playback oder Sortierung.
- Marker koennen verschoben, ausgewaehlt und entfernt werden.
- Now/Next-Anzeige mit Fortschritt und Restzeit.
- Dedizierte OBS Media Source `24/7 Playout Feed`.
- Automatisches Einfuegen des Playout-Feeds in die aktuelle OBS-Szene.
- Endlos-Loop, Shuffle-Modus, Autostart und optionales Fortsetzen des letzten Rundown-Eintrags.
- Metadaten pro Rundown-Eintrag: eigener Stream-Titel, Titel aus Videonamen, Chat-Nachricht, Info-Grafik und Werbung nach dem Video.
- Stream-Titel-Prefix und -Suffix mit frei waehlbaren Trennern, inklusive Leerzeichen oder Emojis.
- Twitch-Integration fuer automatische Kategorie-Wechsel, Stream-Titel, Chat-Nachrichten und Twitch-Werbepausen.
- Twitch OAuth direkt aus dem Plugin mit Statusanzeige fuer fehlende Scopes.
- Werbe-Modi: Twitch-Werbung, nur Werbeszene/Programmtafel oder Werbung aus.
- Eigene OBS-Werbeszene mit Vorlauf/Nachlauf.
- Browserquellen fuer Programmtafel, Info-Banner und Info-Grafik.
- Transparente Programmtafel, damit eigene Hintergruende oder Szenen darunter sichtbar bleiben.
- Responsive Browserquellen, damit Proportionen bei unterschiedlichen Quellgroessen erhalten bleiben.
- Overlay-Farben fuer Programmtafel und Info-Banner inklusive Farbdialog und Speicherung.
- Deutsch/Englisch umschaltbare Oberflaeche.
- Konfigurationsschutz mit Schutzkopie, Auto-Wiederherstellung und atomischem Speichern.
- Import, Export und Backup-Wiederherstellung der Konfiguration.
- Tastatursteuerung fuer Listen, Suche, Auswahl und Entfernen.

## Installation

1. OBS Studio vollstaendig schliessen.
2. ZIP herunterladen und entpacken.
3. Den Inhalt des Ordners `OBS-Studio` in den OBS-Studio-Installationsordner kopieren.
4. Ordner beim Kopieren zusammenfuehren.
5. OBS Studio starten.
6. In OBS `Werkzeuge > 24/7 Playout` oeffnen.

Die Zielstruktur sieht danach so aus:

```text
OBS-Studio/
  obs-plugins/
    64bit/
      playout-247-plugin.dll
  data/
    obs-plugins/
      playout-247-plugin/
        yt-dlp.exe
        ffmpeg.exe   optional, nur im Full-Paket enthalten
        locale/
          en-US.ini
```

## Full- und Slim-Paket

Das Full-Paket ist fuer OBS-Plugins/OBS-Forum gedacht und enthaelt:

- Plugin-DLL
- Debug-Symbole (`.pdb`)
- `yt-dlp.exe`
- `ffmpeg.exe`
- Dokumentation und Lizenz

Das Slim-Paket ist fuer GitHub oder kleinere Downloads gedacht und enthaelt keine `.pdb` und kein `ffmpeg.exe`.

`ffmpeg.exe` kann bei Bedarf ueber die offizielle FFmpeg-Seite nachinstalliert werden:

```text
https://www.ffmpeg.org/download.html
```

Danach die Datei hier ablegen:

```text
OBS-Studio\data\obs-plugins\playout-247-plugin\ffmpeg.exe
```

## Browserquellen

Die Browserquellen sollten in OBS als Browser Source eingebunden werden. Empfohlene Groesse:

```text
1920 x 1080
```

Die Quellen sind responsive aufgebaut. Andere Groessen funktionieren ebenfalls, die Proportionen bleiben erhalten.

Die Programmtafel ist transparent und kann in OBS ueber eigene Bilder, Videos oder Szenen gelegt werden.

## Twitch

Fuer Twitch-Funktionen muss das Plugin autorisiert werden. Danach kann es automatisch:

- Stream-Titel aktualisieren
- Twitch-Kategorie wechseln
- Chat-Nachrichten pro Video senden
- Twitch-Werbepausen ausloesen

Benutzte Scopes:

```text
channel:manage:broadcast channel:edit:commercial chat:read chat:edit user:write:chat
```

## Build-Hinweis

Der aktuelle lokale Build wurde mit dem offiziellen Template-Dependency-Stand `obs-studio 31.1.1` erstellt.

Typischer Build:

```powershell
cmake -S . -B build
cmake --build build --config RelWithDebInfo
```

Aktuelles Build-Ziel:

```text
build-template\RelWithDebInfo\playout-247-plugin.dll
dist\OBS-Studio\obs-plugins\64bit\playout-247-plugin.dll
```

## Release-Pakete erstellen

```powershell
.\tools\package-release.ps1
```

Wenn vorhandene Release-Artefakte ersetzt werden sollen:

```powershell
.\tools\package-release.ps1 -Overwrite
```

## Versionierung

- Sichtbare Plugin-Version: `src/plugin-version.hpp`
- Build-/Paket-Version: `buildspec.json`
- Projektstand: `PROJECT_MEMORY.md`

## Lizenz

This project is licensed under the GNU General Public License v2.0 or later.
See the `LICENSE` file for details.
