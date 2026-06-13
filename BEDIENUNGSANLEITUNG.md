# 24/7 Playout - Bedienungsanleitung

Diese Anleitung erklaert die Installation und die wichtigsten Funktionen des Drittanbieter-Plugins `24/7 Playout` fuer OBS Studio.

## Was macht das Plugin?

`24/7 Playout` ist ein Playout-Dashboard direkt in OBS Studio. Es kann Videos in einer Sendeliste abspielen, automatisch zum naechsten Video wechseln, Werbung ueber eine eigene OBS-Szene einplanen, Twitch-Kategorien, Stream-Titel und Chat-Nachrichten aktualisieren und Overlays wie Programmtafel, Info-Banner und Info-Grafik bereitstellen.

## Voraussetzungen

- Windows 64-bit
- OBS Studio 32.x oder kompatibel
- Fuer Twitch-Funktionen: ein Twitch-Konto und Autorisierung im Plugin
- Fuer Video-Links: erreichbare direkte Videodateien, z.B. `https://domain.de/video.mp4`

## Installation

1. OBS Studio vollstaendig schliessen.
2. ZIP-Datei entpacken.
3. Den Inhalt des Ordners `OBS-Studio` in deinen OBS-Studio-Installationsordner kopieren.
   Beispiel:

```text
D:\Programme\OBS-Studio-32.1.2-Windows-x64
```

4. Beim Kopieren duerfen die Ordner zusammengefuehrt werden.
5. OBS Studio starten.
6. In OBS unter `Werkzeuge > 24/7 Playout` das Plugin-Fenster oeffnen.

Die Zielstruktur sieht danach ungefaehr so aus. Je nach Release-Paket koennen optionale Hilfsprogramme wie `ffmpeg.exe` fehlen; das Plugin selbst besteht aus der DLL und den Daten im Plugin-Ordner.

```text
OBS-Studio/
  obs-plugins/
    64bit/
      playout-247-plugin.dll
  data/
    obs-plugins/
      playout-247-plugin/
        yt-dlp.exe
        ffmpeg.exe   optional
        locale/
          en-US.ini
```

## Erster Start

Beim ersten Start ist die Videothek leer. Du kannst lokale Videos, Ordner oder Video-Links hinzufuegen.

Empfohlener Ablauf:

1. Im Tab `Playout` Videos oder Ordner zur Mediathek hinzufuegen.
2. Gewuenschte Videos markieren.
3. Mit `Zur Sendeliste` in die Playlist uebernehmen.
4. Mit `Feed erstellen` die OBS-Media-Source erzeugen.
5. Mit `Playout in Szene +` den Feed in die aktuelle OBS-Szene einfuegen.
6. Mit `Play` starten.

## Playout-Tab

Der Playout-Tab ist die Hauptansicht.

### Mediathek

Hier liegen alle verfuegbaren Medien:

- lokale Videodateien
- Ordnerimporte
- direkte Video-Links

Wichtige Buttons:

- `+ Video`: einzelne lokale Videos hinzufuegen
- `+ Ordner`: Videos aus einem Ordner laden
- `+ Link`: Video per direktem Link hinzufuegen
- `Datei ersetzen`: fehlende oder geaenderte Datei ersetzen
- `Entfernen`: markierte Eintraege aus der Mediathek entfernen
- `Zur Sendeliste`: markierte Videos in die Sendeliste uebernehmen

### Playlist / Rundown

Die Sendeliste bestimmt, was abgespielt wird.

Wichtige Buttons:

- `Hoch` / `Runter`: Reihenfolge aendern
- `Duplizieren`: Eintrag kopieren
- `Aktiv an/aus`: Eintrag aktivieren oder deaktivieren
- `Werbung an/aus`: Werbung nach diesem Video aktivieren oder deaktivieren
- `Metadaten`: Titel, Info-Grafik und Chat-Nachricht pro Video bearbeiten
- `Marker`: visuelle Orientierung direkt im Rundown setzen
- `Entfernen`: Eintrag aus der Sendeliste entfernen

Marker sind reine Orientierungshilfen. Sie beeinflussen weder Playback noch Reihenfolge. Die angezeigte Marker-Zeit stammt vom geplanten Start des darunterliegenden Videos.

### Metadaten pro Video

Im Dialog `Metadaten` kannst du pro Sendelisten-Eintrag festlegen:

- ob der Videoname als Stream-Titel genutzt wird
- eigener Stream-Titel
- Info-Grafik fuer die Browserquelle
- ob nach dem Video Werbung abgespielt werden soll
- ob eine Chat-Nachricht gesendet werden soll
- individuelle Chat-Nachricht

Wenn `Chat-Nachricht senden` deaktiviert ist, werden Twitch-Kategorie und Stream-Titel weiterhin aktualisiert, aber fuer dieses Video wird kein Chatpost gesendet.

## Werbung

Im Tab `Werbung` legst du fest:

- welche OBS-Szene waehrend der Werbung angezeigt wird
- wie lange die Twitch-Werbepause dauert
- Vorlaufzeit: Werbung kann kurz vor Videoende starten
- Nachlaufzeit: neues Video kann nach der Werbung leicht verzoegert starten

Typischer Ablauf:

1. In OBS eine eigene ADS-/Werbe-Szene bauen.
2. Im Plugin diese Szene als Werbe-Szene auswaehlen.
3. Werbedauer einstellen, z.B. 30 Sekunden.
4. Optional Vorlauf/Nachlauf fuer Stinger-Transitions einstellen.

## Marker im Rundown

Marker sind bewusst einfach gehalten und dienen nur als visuelle Orientierung:

- Marker stehen direkt in der Playlist/Rundown-Liste.
- Marker koennen zwischen Videos verschoben werden.
- Marker koennen wie Videos ausgewaehlt und entfernt werden.
- Marker sind gruen hervorgehoben.
- Marker haben keine automatische Abspielfunktion.
- Die Videos laufen weiterhin in der normalen Rundown-Reihenfolge.

## Twitch

Im Tab `Twitch` verbindest du das Plugin mit deinem Twitch-Konto.

Wichtige Buttons:

- `Twitch Autorisieren`: Browser oeffnet Twitch-Login
- `Twitch Verbinden`: gespeicherten Token pruefen und Verbindung herstellen

Wenn Twitch verbunden ist, kann das Plugin automatisch:

- Kategorie/Game aendern
- Stream-Titel aktualisieren
- Chat-Nachrichten senden
- Werbung ausloesen, sofern Twitch es erlaubt

## Overlays / Browserquellen

Das Plugin erzeugt lokale Browserquellen fuer:

- Programmtafel
- Info-Banner
- Info-Grafik

Diese Quellen koennen in OBS als Browser Source eingebunden werden.

Beispiel:

```text
http://127.0.0.1:24713/programmtafel.html
http://127.0.0.1:24713/infobanner.html
```

Die Programmtafel aktualisiert sich passend zum Playout, z.B. bei Werbung oder Video-Wechsel.

Empfohlene Browserquellen-Aufloesung:

```text
1920 x 1080
```

Die Browserquellen sind responsive. Wenn eine andere Groesse verwendet wird, bleiben Proportionen und Layout erhalten. Die Programmtafel ist transparent, sodass eigene Bilder, Videos oder Szenen darunter liegen koennen.

## Tastatursteuerung

Einige Tastenkombinationen erleichtern die Bedienung:

- `Entf`: markierte Eintraege entfernen
- `Strg+A`: sichtbare Eintraege in der fokussierten Liste auswaehlen
- `Esc`: Auswahl aufheben
- `Strg+F`: Suchfeld der fokussierten Liste anspringen
- `Enter`: Hauptaktion der fokussierten Liste ausfuehren
- `Strg+L`: Filter der fokussierten Liste leeren
- `Strg+S`: Konfiguration speichern

## Konfiguration und Backups

Die Konfiguration wird lokal in deinem OBS-Profilbereich gespeichert.
Typischer Pfad:

```text
C:\Users\<Name>\AppData\Local\obs64\obs-247-playout-config.json
```

Das Plugin erzeugt bei bestimmten Aktionen automatisch Schutzkopien. Trotzdem ist es sinnvoll, vor grossen Updates eine eigene Sicherung zu erstellen.

## Wichtige Hinweise

- OBS nach Plugin-Updates immer neu starten.
- Wenn Videos als fehlend angezeigt werden, pruefe die Dateipfade.
- Direkte Video-Links sollten auf echte Videodateien zeigen, z.B. `.mp4`.
- YouTube-Links koennen je nach YouTube-Schutz, Cookies oder Verfuegbarkeit unzuverlaessig sein.
- Fuer stabilen 24/7-Betrieb sind lokale Videos oder direkte Video-Dateilinks am sichersten.

## Optional: ffmpeg.exe nachinstallieren

Manche Release-Pakete werden als kleinere Slim-Version ausgeliefert. In diesen Paketen kann `ffmpeg.exe` fehlen, damit die ZIP-Datei kleiner bleibt.

Das Plugin funktioniert fuer normale lokale Videos und direkte Video-Dateilinks auch ohne `ffmpeg.exe`. Sinnvoll ist `ffmpeg.exe` aber fuer:

- genauere Dauererkennung bei manchen Medien
- bestimmte Netzwerkvideo-/YouTube-Fallbacks
- spaetere Videoanalyse- oder Konvertierungsfunktionen

### Download

1. Offizielle FFmpeg-Downloadseite oeffnen:

```text
https://www.ffmpeg.org/download.html
```

2. Dort den Windows-Bereich auswaehlen.
3. Einen Windows-Build herunterladen, z.B. einen `release full` oder `essentials` Build als ZIP/7z.
4. Archiv entpacken.
5. Im entpackten Ordner nach `bin\ffmpeg.exe` suchen.

### Wohin muss ffmpeg.exe?

Kopiere nur die Datei `ffmpeg.exe` in diesen Plugin-Ordner innerhalb deiner OBS-Installation:

```text
OBS-Studio\data\obs-plugins\playout-247-plugin\ffmpeg.exe
```

Beispiel:

```text
D:\Programme\OBS-Studio-32.1.2-Windows-x64\data\obs-plugins\playout-247-plugin\ffmpeg.exe
```

Danach OBS Studio komplett neu starten.

### Alternative

Fortgeschrittene Nutzer koennen `ffmpeg.exe` auch in einen Ordner legen, der in der Windows-Umgebungsvariable `PATH` eingetragen ist. Fuer normale Nutzer ist die direkte Ablage im Plugin-Ordner einfacher und sicherer.

## Fehlerbehebung

### Plugin-Fenster wird nicht angezeigt

- OBS neu starten.
- Unter `Werkzeuge` nach `24/7 Playout` suchen.
- Pruefen, ob die DLL im richtigen OBS-Ordner liegt.

### Video startet nicht

- Datei existiert noch?
- Video-Link erreichbar?
- Feed mit `Feed erstellen` neu erzeugen.
- Feed mit `Playout in Szene +` erneut in die Szene einfuegen.

### Twitch sendet keine Chat-Nachricht

- Twitch verbunden?
- Hat das Video den Haken `Chat-Nachricht senden`?
- Ist eine Chat-Nachricht oder Standard-Chat-Nachricht eingetragen?
- Wurde Twitch nach Scope-Aenderungen neu autorisiert?

### Werbung startet nicht

- Twitch verbunden?
- Werbe-Szene gesetzt?
- Werbung fuer den Sendelisten-Eintrag aktiviert?
- Twitch erlaubt Werbung nicht unbegrenzt oft hintereinander.

## Update

1. OBS Studio schliessen.
2. Neue Plugin-Version entpacken.
3. Inhalt des Ordners `OBS-Studio` ueber die bestehende OBS-Installation kopieren.
4. OBS Studio starten.
5. Version oben im Plugin-Fenster pruefen.



