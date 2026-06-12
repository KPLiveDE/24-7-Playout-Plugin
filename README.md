# OBS 24/7 Playout Plugin

Aktuelle Version: `0.7.98`

Ziel: ein echtes OBS-Plugin mit Dock, das einen 24/7 Twitch-Channel als Playout-System steuert.

Das OBS-Plugin soll:

- ein eigenes Dock in OBS anzeigen,
- Videos und Ordner per Drag and Drop direkt in die Mediathek uebernehmen,
- Videothek, Sendeliste und Timeline-Kategorien verwalten,
- Video-Links dauerhaft in der Videothek speichern,
- mehrere markierte Videothek-Eintraege gemeinsam entfernen,
- Entfernung aus der Videothek vor dem Loeschen bestaetigen,
- markierte Eintraege in Videothek, Sendeliste und Timeline-Kategorien per Entf-Taste mit Bestaetigung entfernen,
- sichtbare Eintraege in der fokussierten Liste per Strg+A auswaehlen,
- Auswahl in der fokussierten Liste per Esc aufheben,
- Suchfeld der fokussierten Liste per Strg+F anspringen,
- Hauptaktion der fokussierten Liste per Enter ausfuehren,
- Filter der fokussierten Liste per Strg+L leeren,
- Konfiguration per Strg+S speichern,
- Konfiguration im Dock auf fehlende Dateien, leere/unguelstige Sendelisten, Timeline-Probleme und fehlende Szenen/Twitch-Verbindung pruefen,
- aktuelle Konfiguration vor Import oder Backup-Wiederherstellung automatisch als datierte Schutzkopie sichern,
- Import und Backup-Wiederherstellung vor dem Ersetzen mit kurzer Inhaltsuebersicht bestaetigen,
- permanente Verbindungsanzeige oben im Dock fuer Twitch und Video-Link-Modus,
- optionaler Zufallsmodus fuer die Sendeliste,
- Twitch-Verbindungsstatus zeigt klar, wenn wegen fehlender Scopes neu autorisiert werden muss,
- Packaging-Skript fuer spaetere Release-ZIPs bereithalten,
- manuell gesetzten Stream-Titel direkt in der Sendeliste anzeigen,
- YouTube-/Video-Links ohne YouTube Data API in die Videothek einfuegen,
- Videotitel beim Einfuegen eines YouTube-Links automatisch auslesen,
- YouTube-Links zur Laufzeit per `yt-dlp` in abspielbare Stream-URLs aufloesen, ohne die Videos dauerhaft herunterzuladen,
- YouTube-Stream-Aufloesung im Hintergrund ausfuehren, damit das Dock nicht einfriert,
- Link-Titel mit Slashes/Emojis unverkuerzt als Stream-Titel verwenden,
- Netzwerkvideos beim Start kurz gegen versehentliches Sofort-Ueberspringen schuetzen,
- Sendeplan-Tab mit Startzeit, echter Uhrzeit, Gesamtlaufzeit und berechneten Start-/Endzeiten anzeigen,
- Sendeplan-Kapitel/Dayparts mit frei benennbaren Uhrzeitbloecken anzeigen,
- Sendelisten-Eintraege Kapiteln zuweisen und nach Kapitel-Zeiten sortieren,
- Sendelisten-Eintraege innerhalb ihrer Kapitel mischen,
- Sendeliste durch Auswahl eines Sendeplan-Kapitels filtern,
- Kapitel-Konflikte im Sendeplan anzeigen,
- zwischen Videos automatisch einen Werbeblock einplanen,
- eine dedizierte OBS Media Source namens `24/7 Playout Feed` erstellen,
- diese Quelle in eine Szene einfuegen,
- spaeter Twitch-Kategorie, Stream-Metadaten und Chat-Infos automatisch setzen,
- spaeter YouTube-Metadaten aus dem eigenen Kanal importieren.

## Warum zuerst OBS Media Source?

Fuer Version 1 ist eine vom Plugin gesteuerte Media Source am sinnvollsten.
OBS bringt damit Video-Decoding, Audio, Playback und Szenen-Integration bereits mit.
Das Plugin kann diese Quelle vorbereiten und spaeter beim Playout von Video zu Video umschalten.

Eine komplett eigene OBS Source bleibt moeglich, ist aber eher Phase 2.

## Projektstruktur

- `CMakeLists.txt` - Build-Datei fuer das OBS-Plugin.
- `src/plugin-main.cpp` - OBS Plugin Entry Point und Dock-Registrierung.
- `src/playout-dock.hpp` - Dock-Klasse.
- `src/playout-dock.cpp` - Dock UI, Speicherung und Media-Source-Steuerung.
- `docs/OBS_PLUGIN_ARCHITECTURE.md` - Architekturentscheidung und Roadmap.
- `docs/OBS_INSTALL_LAYOUT.md` - Zielstruktur im OBS-Studio-Ordner.
- `PROJECT_MEMORY.md` - Projektgedaechtnis.

## Build-Hinweis

Zum Kompilieren werden OBS Studio Build-Dependencies und das OBS Plugin Template/SDK benoetigt.
Das Projekt nutzt die offiziellen Build-Hilfsdateien aus `obs-plugintemplate`.

Typischer Build-Ablauf, sobald OBS-Dependencies eingerichtet sind:

```powershell
cmake -S . -B build
cmake --build build --config RelWithDebInfo
```

Der aktuelle lokale Build wurde mit dem offiziellen Template-Dependency-Stand `obs-studio 31.1.1`
erstellt und erzeugt:

```text
build-template\RelWithDebInfo\obs-247-playout-plugin.dll
dist\OBS-Studio\obs-plugins\64bit\obs-247-playout-plugin.dll
```

## Slim-Paket und ffmpeg.exe

Fuer GitHub- oder OBS-Uploads kann es ein kleineres Slim-Paket geben. Dieses enthaelt die Plugin-DLL, `yt-dlp.exe`, die Locale-Datei und die Anleitungen, aber keine Debug-Symbole (`.pdb`) und kein `ffmpeg.exe`.

Das Plugin funktioniert fuer lokale Videos und direkte Video-Dateilinks auch ohne `ffmpeg.exe`. Sinnvoll ist `ffmpeg.exe` trotzdem fuer bestimmte Dauererkennungen, Netzwerkvideo-Fallbacks und spaetere Analysefunktionen.

`ffmpeg.exe` kann ueber die offizielle FFmpeg-Downloadseite bezogen werden:

```text
https://www.ffmpeg.org/download.html
```

Danach einen Windows-Build herunterladen, entpacken und die Datei `bin\ffmpeg.exe` in den Plugin-Datenordner der OBS-Installation kopieren:

```text
OBS-Studio\data\obs-plugins\obs-247-playout-plugin\ffmpeg.exe
```

Beispiel:

```text
D:\Programme\OBS-Studio-32.1.2-Windows-x64\data\obs-plugins\obs-247-playout-plugin\ffmpeg.exe
```

Danach OBS Studio komplett neu starten.

Installation in einen OBS-Ordner wie `D:\Programme\OBS-Studio-32.1.2-Windows-x64`:

```powershell
cmake --install build --config RelWithDebInfo --prefix "D:\Programme\OBS-Studio-32.1.2-Windows-x64"
```

Die installierte Struktur muss danach so aussehen:

```text
D:\Programme\OBS-Studio-32.1.2-Windows-x64\
  obs-plugins\
    64bit\
      obs-247-playout-plugin.dll
  data\
    obs-plugins\
      obs-247-playout-plugin\
        locale\
          en-US.ini
```

Im Projekt liegt diese Struktur bereits vorbereitet unter:

```text
dist\OBS-Studio\
```

## Naechste Schritte

1. Konfiguration/Sicherheit weiter verbessern, vor allem Schutz vor versehentlichem Ueberschreiben und Wiederherstellungsdetails.
2. UI weiter verdichten, sobald im Dock wieder Breite/Platz knapp wird.
3. Release-ZIP/Installer erst wieder anfassen, wenn der Funktionsstand stabil genug ist.
4. YouTube-HD/ffmpeg und Werbung/Transition-Feinschliff bleiben bewusst zurueckgestellt.

## Aktueller MVP-Stand

- Mehrere lokale Videos koennen in die Videothek geladen werden.
- Ganze Video-Ordner koennen rekursiv importiert werden.
- Die Videothek kann per Suchfeld nach Titel oder Dateipfad gefiltert werden.
- Videothek und Sendeliste zeigen sichtbare und gesamte Eintragsanzahl.
- Videothek, Sendeliste und Timeline zeigen zusaetzlich die Anzahl ausgewaehlter Eintraege.
- Videothek- und Sendelisten-Filter koennen per Button geleert werden.
- Alle aktuell sichtbaren Videothek-Eintraege koennen ausgewaehlt oder wieder abgewählt werden.
- Einzeln ausgewaehlte Videos koennen per `Datei ersetzen` neu verknuepft werden; Mehrfachauswahl wird dabei abgefangen.
- Doppelte Videopfade werden beim Import vermieden.
- Videos koennen einzeln oder per Mehrfachauswahl in eine Sendeliste uebernommen, sortiert und entfernt werden.
- Die Sendeliste kann per Suchfeld nach Titel, Dateipfad, Stream-Titel oder Chat-Nachricht gefiltert werden.
- Alle aktuell sichtbaren Sendelisten-Eintraege koennen fuer Massenaktionen ausgewaehlt werden.
- Die Sendelisten-Auswahl kann per Button wieder aufgehoben werden.
- Videothek-, Sendelisten- und Timeline-Aktionsbuttons sind kompakter in mehreren Reihen angeordnet.
- Mehrere Sendelisten-Eintraege koennen gemeinsam aktiviert/deaktiviert oder nach Bestaetigung entfernt werden.
- Sendelisten-Eintraege koennen inklusive Metadaten dupliziert werden.
- Sendelisten-Eintraege koennen aktiv/inaktiv geschaltet werden.
- Werbung nach Sendelisten-Eintraegen kann direkt fuer einen oder mehrere markierte Eintraege umgeschaltet werden.
- Die Sendeliste kann endlos wiederholt werden oder am Ende stoppen.
- Die Sendeliste kann optional im Zufallsmodus weiterlaufen.
- Fehlende Videodateien werden in Videothek/Sendeliste rot als `[fehlt]` markiert.
- Optionaler Autostart beim OBS-Start.
- Now/Next-Anzeige fuer aktuelles und naechstes Playout-Element.
- Pro Video koennen Timeline-Kategorien angelegt, bearbeitet und geloescht werden.
- Timeline-Kategorien koennen pro Video gefiltert und per Button wieder ungefiltert angezeigt werden.
- Timeline-Kategorien koennen per Mehrfachauswahl gemeinsam ausgewaehlt, dupliziert oder entfernt werden.
- Neue Timeline-Kategorien nutzen eine speicherbare Standard-Kategorie.
- Timeline-Kategorien koennen dupliziert werden; bei gesetzter Endzeit wird die Kopie direkt danach platziert.
- `Play`, `Naechstes` und `Stop` steuern die dedizierte OBS Media Source.
- `Naechstes` und die automatische Wiedergabe ueberspringen deaktivierte oder fehlende Eintraege.
- `Feed in Szene einfuegen` erstellt die Quelle automatisch und fuegt sie in die aktuelle OBS-Szene ein.
- Waehrend der Wiedergabe wird die aktuelle Media-Zeit gelesen und die passende Timeline-Kategorie markiert.
- Kategorie-/Chat-Aktionen werden aktuell als Status/OBS-Log vorbereitet, bis die Twitch-Anbindung folgt.
- Konfiguration kann per Import/Export gesichert oder wiederhergestellt werden.
- Konfiguration wird als JSON im Benutzer-Konfigurationsbereich gespeichert.
- Aenderungen an Videothek, Sendeliste, Timeline und wichtigen Optionen werden still automatisch gespeichert.
- Timeline-Kategorien werden nach Startzeit sortiert und koennen per `Zur Kategorie` direkt angesprungen werden.
- Timeline-Kategorien mit Luecken oder Overlaps werden markiert.
- `Auto-Enden` setzt Kategorie-Endzeiten automatisch auf den naechsten Kategoriestart.
- Twitch-Konfiguration fuer Client-ID, OAuth Token und Broadcaster ID.
- Permanente Kopfzeile zeigt den Twitch-Verbindungsstatus unabhaengig vom aktiven Tab.
- `Twitch Autorisieren` oeffnet Twitch im Browser und uebernimmt den OAuth Token ueber `http://localhost:3000`.
- Falls noch keine Client ID gespeichert ist, fragt `Twitch Autorisieren` sie einmalig ab und speichert sie.
- Twitch OAuth zeigt jetzt konkrete Fehler fuer abgelehnte Autorisierung, State-Mismatch oder fehlenden Token.
- Die benoetigte Twitch Redirect URL wird im Dock sichtbar angezeigt.
- `Twitch Verbinden` validiert den gespeicherten Token und verweist ohne Token auf die automatische Autorisierung.
- Beim Dock-Start wird Twitch automatisch verbunden, wenn Client ID und Token gespeichert sind.
- Twitch-Token-Test zeigt konkrete Netzwerkfehler, HTTP-Statuscodes und Twitch-Meldungen an.
- Twitch-API-Requests nutzen Windows HTTPS/WinHTTP statt Qt/OpenSSL, damit OBS keine separaten OpenSSL-DLLs benoetigt.
- Twitch-Verbindungstest validiert den Token und liest den Twitch-User ueber Helix.
- Timeline-Kategorien setzen beim aktiven Wechsel automatisch die Twitch-Kategorie.
- Der Timeline-Kategorie-Editor kann Twitch-Kategorien suchen und aus einer Trefferliste uebernehmen.
- Sendelisten-Eintraege koennen eigene Stream-Titel und Chat-Nachrichten speichern.
- Manuelle Stream-Titel werden direkt in der Sendeliste als Vorschau angezeigt.
- Chat-Nachrichten von Sendelisten-Eintraegen werden beim Videostart an Twitch gesendet.
- Twitch-Verbindung zeigt an, wenn Kategorie-/Titel-, Chat- oder Werbe-Scopes im aktuellen Token fehlen.
- Stream-Titel koennen pro Video aus Videonamen oder eigenem Titel gebaut werden.
- Bei Videonamen als Stream-Titel werden Dateiendungen wie `.mp4` oder `.webm` entfernt.
- Globale Stream-Titel-Zusaetze koennen vor und nach dem Video-/Eigentitel gesetzt werden; Trenner wie Leerzeichen, Bindestrich, Pipe oder Emoji werden bei Bedarf direkt in diese Felder geschrieben und bleiben erhalten.
- Der alte Button `Verbindung testen` heisst jetzt `Twitch Verbinden`.
- Twitch Autoconnect laeuft beim Start automatisch mit gespeicherten Zugangsdaten.
- Fuer Kategorie/Titel, Chat-Nachrichten und Werbepausen braucht die Twitch-Autorisierung die passenden Scopes; bei fehlenden Scopes zeigt die Kopfzeile `neu autorisieren noetig`.
- Chat-Sendefehler zeigen HTTP-Status und Twitch-Antwort im Statuslog.
- Twitch Chat-Antworten werden auf `is_sent` und `drop_reason` geprueft.
- Doppelklick auf einen Sendelisten-Eintrag oeffnet die Metadaten.
- Sendelisten-Eintraege markieren vorhandene Chat-/Titel-Metadaten und zeigen eine Tooltip-Vorschau.
- Neue Sendelisten-Eintraege uebernehmen optional eine globale Standard-Chatnachricht.
- Autostart kann optional den zuletzt gespielten Sendelisten-Eintrag fortsetzen.
- Autostart kann ungefaehr an der zuletzt gespeicherten Videoposition fortsetzen.
- Wiederaufnahme meldet klar, wenn der letzte Eintrag fehlt, deaktiviert ist oder die Datei fehlt.
- Autosave fuer Wiedergabepositionen laeuft still und ueberschreibt den Statusbereich nicht mehr.
- Sendelisten-Eintraege koennen Werbung nach dem Video einzeln aktivieren/deaktivieren.
- Werbepausen koennen eine auswählbare OBS-Werbeszene anzeigen und danach zur Playout-Szene zurueckschalten.
- Twitch-Werbepausen werden per API mit festen Laengen von 30 bis 180 Sekunden gestartet.
- Ausgewaehlte Playout-/Werbeszenen werden direkt gespeichert.
- Gespeicherte Szenen bleiben beim OBS-Neustart erhalten, auch wenn OBS die Szenenliste erst spaeter liefert.
- Dock-UI ist in erste Tabs aufgeteilt: `Playout` und `Twitch`.
- Autosave ist waehrend des Config-Ladens blockiert, damit gespeicherte Twitch-Daten nicht leer ueberschrieben werden.
- Stille Autosaves duerfen eine vorhandene gefuellte Config nicht mit leerer Videothek/Sendeliste ueberschreiben.
- Vor jedem Speichern wird eine `.bak`-Sicherung der Config angelegt.
- Backup-Datei kann direkt im Dock wiederhergestellt werden.
- Import, Export, Speichern und Backup liegen im eigenen Tab `Konfiguration`.
- Der Konfigurations-Tab kann die aktuelle Einrichtung vor dem 24/7-Lauf pruefen und Warnungen anzeigen.
- Playout-/Werbeszene und Twitch-Werbepausen-Dauer liegen im eigenen Tab `Werbung`.
- Release-Pakete koennen spaeter per `tools\package-release.ps1` als ZIP mit Versionsnummer erzeugt werden.
- YouTube Data API ist aus dem sichtbaren Workflow entfernt; der separate `Links`-Tab ist nicht mehr sichtbar.
- Link-Import liest YouTube-Titel per oEmbed ohne OAuth/Google-Cloud-App aus und speichert den Link dauerhaft in der Videothek.
- YouTube-Watch-Links werden beim Abspielen optional ueber `yt-dlp` in direkte Stream-URLs aufgeloest; es wird nichts heruntergeladen.
- YouTube-Resolver nutzt wieder den einfachen progressiven Audio+Video-Stream und loggt die gewaehlte Format-ID/Hoehe.
- YouTube-Resolver versucht bei vorhandenem `ffmpeg.exe` zuerst 1080p Video+Audio lokal zusammenzufuehren und faellt bei Fehlern auf den progressiven Stream zurueck.
- Der alte `Links`-Tab ist entfernt; YouTube-/Video-Links werden weiterhin ueber `Link +` im Playout-Tab eingefuegt.
- Nach jedem Update wird ein eigenes fortlaufendes Backup unter `backups/` abgelegt.
- Remote-/YouTube-Links erhalten beim Start eine kurze Lade-Schutzzeit, damit OBS nicht sofort zum naechsten Eintrag springt.

## Offene To-dos

- Aktuell weiter: Konfigurationsschutz und Wiederherstellung weiter absichern.
- Zurueckgestellt: YouTube-HD/1080p mit ffmpeg stabilisieren; progressiver Stream bleibt der stabile Fallback.
- Zurueckgestellt: Werbung/Transition-Feinschliff weiter testen, falls im echten Betrieb Timing-Probleme auftreten.
- Zurueckgestellt: Release-ZIP/Installer erst wieder erzeugen, wenn der Funktionsstand finaler ist.
- Dauerhaft beibehalten: Fortlaufende Backups nach jedem Update unter `backups/`.

## Erledigter Sendeplan-Stand

- Sendeplan mit echter Uhrzeit, Startzeit, Gesamtlaufzeit und geplanten Slot-Zeiten.
- Frei benennbare Kapitel/Dayparts mit Uhrzeitfenstern.
- Sendelisten-Eintraege koennen Kapiteln zugewiesen, nach Kapiteln sortiert und innerhalb von Kapiteln gemischt werden.
- Kapitel-Auswahl filtert die Sendeliste; gefilterte Wiedergabe bleibt im Kapitel.
- Sendeplan zeigt Kapitel-Konflikte, Kapitel-Laufzeiten, aktuellen Slot, Live-Abgleich und Drift-Warnung.
- Die Sendeplan-Synchronisierung erfolgt automatisch bei Play, Video-Wechsel und manuellem Spulen; `Aktuellen Slot starten` bleibt fuer gezieltes Einspringen verfuegbar.

## Twitch OAuth

Fuer die Browser-Autorisierung muss in der Twitch Developer Console bei deiner App diese Redirect URL eingetragen sein:

```text
http://localhost:3000
```

Der Button `Twitch Autorisieren` nutzt den offiziellen Implicit Grant Flow mit `response_type=token`.
Twitch verlangt trotzdem eine Client ID, weil Twitch wissen muss, welche App autorisiert wird.
Das Plugin fragt aktuell diese Scopes an:

```text
channel:manage:broadcast channel:edit:commercial chat:read chat:edit user:write:chat
```

## Versionierung

- Die sichtbare Plugin-Version steht in `src/plugin-version.hpp`.
- Die Build-/Package-Version steht in `buildspec.json`.
- Beide werden bei jedem neuen Update gemeinsam aktualisiert.
- Die JSON-Konfigurationsversion ist davon getrennt und dient nur fuer Datenmigrationen.

