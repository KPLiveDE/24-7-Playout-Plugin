# Slim-Paket Hinweis

Dieses Paket enthaelt das OBS 24/7 Playout Plugin ohne `ffmpeg.exe` und ohne Debug-Datei (`.pdb`).

Geeignet fuer Nutzer, die ein kleineres Download-Paket bevorzugen oder FFmpeg bereits separat installiert haben.

Wenn lokale/Online-Videoanalyse oder spaetere Diagnosefunktionen FFmpeg benoetigen, nutze stattdessen das normale Full-Paket.

Alternativ kann FFmpeg separat heruntergeladen werden:

https://www.gyan.dev/ffmpeg/builds/ffmpeg-release-essentials.zip

Nach dem Entpacken liegt die Datei unter `bin\ffmpeg.exe`.
Diese `ffmpeg.exe` kann in den Plugin-Datenordner kopiert werden:

`OBS-Studio\data\obs-plugins\obs-247-playout-plugin\ffmpeg.exe`
