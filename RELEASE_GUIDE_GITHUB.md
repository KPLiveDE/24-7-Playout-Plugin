# GitHub Release-Anleitung

Diese Anleitung beschreibt, wie `24/7 Playout` als GitHub-Projekt vorbereitet und mit Releases veroeffentlicht wird.

## Ziel

GitHub dient als zentrale Projektseite fuer:

- Quellcode
- Changelog
- Release-ZIPs oder Installer
- Issues und Fehlerberichte
- Dokumentation

OBS-Nutzer koennen GitHub Releases beobachten und bekommen dann GitHub-Benachrichtigungen, wenn eine neue Version veroeffentlicht wird.

## Repository vorbereiten

1. Repository auf GitHub erstellen.
2. Projektdateien hochladen.
3. README pruefen:
   - kurzer Zweck des Plugins
   - OBS-Version
   - Windows-Unterstuetzung
   - Installation
   - wichtige Hinweise zu Twitch, Video-Links und OBS-Szenen
4. Lizenz festlegen.
5. Screenshots oder Preview-Bilder hinzufuegen.
6. `docs/` mit Installations- und Bedienungsanleitungen aktuell halten.

## Versionierung

Jede veroeffentlichte Version sollte eindeutig sein, z.B.:

```text
0.7.71
0.8.0
1.0.0
```

Vor jedem Release aktualisieren:

- `src/plugin-version.hpp`
- `buildspec.json`
- `README.md`
- `PROJECT_MEMORY.md`

## Release-Paket

Ein Windows-Release sollte spaeter mindestens enthalten:

```text
OBS-Studio/
  obs-plugins/
    64bit/
      playout-247-plugin.dll
      playout-247-plugin.pdb
  data/
    obs-plugins/
      playout-247-plugin/
        locale/
          en-US.ini
```

Optional:

- Installer
- ZIP mit klarer Ordnerstruktur
- Kurzanleitung `INSTALL.md`
- Changelog `CHANGELOG.md`

## GitHub Release erstellen

1. Build erstellen und testen.
2. Release-ZIP bauen.
3. GitHub: `Releases` > `Draft a new release`.
4. Tag setzen, z.B. `v0.8.18`.
5. Titel setzen, z.B. `24/7 Playout v0.8.18`.
6. Changelog eintragen:
   - neue Funktionen
   - Bugfixes
   - bekannte Probleme
7. ZIP oder Installer als Asset hochladen.
8. Release veroeffentlichen.

## Changelog-Vorlage

```markdown
## 24/7 Playout v0.8.18

### Neu
- Plugin-Fenster wird ueber `Werkzeuge > 24/7 Playout` geoeffnet.
- Visuelle Marker dienen als einfache Orientierung direkt im Rundown.
- Browserquellen bleiben responsive und transparent.

### Geaendert
- Technischer Plugin-/Paketname ist `playout-247-plugin`.
- Full- und Slim-Pakete werden getrennt erzeugt.

### Hinweise
- Nach dem Update OBS Studio neu starten.
- Fuer OBS-Plugins das Full-Paket verwenden.
- Fuer GitHub kann das kleinere Slim-Paket verwendet werden.
```

## Update-Hinweis fuer Nutzer

GitHub kann Nutzer ueber neue Releases benachrichtigen, wenn sie das Repository beobachten.
Trotzdem sollte die OBS-Resource-Seite ebenfalls aktualisiert werden, weil viele OBS-Nutzer eher dort nach Updates suchen.

## Empfohlener Release-Ablauf

1. Lokaler Test in OBS.
2. Backup der funktionierenden Version erstellen.
3. Version erhoehen.
4. Build erstellen.
5. ZIP/Installer erstellen.
6. GitHub Release veroeffentlichen.
7. OBS-Resource-Seite aktualisieren.
8. Optional: Hinweis im Twitch/Discord/Ko-fi posten.



