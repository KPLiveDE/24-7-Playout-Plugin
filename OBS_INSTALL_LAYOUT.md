# OBS Plugin Install Layout

OBS Studio erwartet Plugins unterhalb des OBS-Installationsordners in einer festen Struktur.

Beispiel fuer deinen OBS-Ordner:

```text
D:\Programme\OBS-Studio-32.1.2-Windows-x64\
```

Ein installiertes Plugin liegt dort typischerweise so:

```text
D:\Programme\OBS-Studio-32.1.2-Windows-x64\
  obs-plugins\
    64bit\
      playout-247-plugin.dll
  data\
    obs-plugins\
      playout-247-plugin\
        locale\
          en-US.ini
```

## Bedeutung

- `obs-plugins\64bit\*.dll`
  - Native Plugin-Bibliothek, die OBS beim Start laedt.
- `data\obs-plugins\<plugin-id>\`
  - Plugin-Daten, Locale-Dateien, Icons, UI-Ressourcen und spaetere Assets.
- `data\obs-plugins\<plugin-id>\locale\*.ini`
  - Uebersetzungsdateien fuer `OBS_MODULE_USE_DEFAULT_LOCALE`.

## Installation per CMake

Wenn das Plugin erfolgreich gebaut wurde, kann es direkt in einen OBS-Ordner installiert werden:

```powershell
cmake --install build --config RelWithDebInfo --prefix "D:\Programme\OBS-Studio-32.1.2-Windows-x64"
```

Danach sollte die Datei hier liegen:

```text
D:\Programme\OBS-Studio-32.1.2-Windows-x64\obs-plugins\64bit\playout-247-plugin.dll
```

Und die Daten hier:

```text
D:\Programme\OBS-Studio-32.1.2-Windows-x64\data\obs-plugins\playout-247-plugin\
```

## Hinweis

Die gespeicherte Playout-Konfiguration gehoert nicht in den OBS-Programmordner.
Sie soll spaeter im Benutzer-Konfigurationsbereich liegen, damit OBS-Updates oder Plugin-Neuinstallationen die Sendelisten nicht ueberschreiben.



