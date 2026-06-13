# Slim-Paket-Hinweis

Dieses Slim-Paket enthaelt die Dateien fuer 24/7 Playout, aber keine Debug-Symbole (.pdb) und kein fmpeg.exe.

Enthalten:

- OBS-Studio\obs-plugins\64bit\playout-247-plugin.dll
- OBS-Studio\data\obs-plugins\playout-247-plugin\yt-dlp.exe
- OBS-Studio\data\obs-plugins\playout-247-plugin\locale\en-US.ini
- README, Lizenz und Dokumentation

fmpeg.exe ist optional. Fuer lokale Videos und viele direkte Videolinks funktioniert das Plugin auch ohne diese Datei.
Wenn du fmpeg.exe nachinstallieren moechtest, lade FFmpeg ueber die offizielle Seite herunter:

https://www.ffmpeg.org/download.html

Kopiere danach nur die Datei fmpeg.exe in diesen Ordner deiner OBS-Installation:

OBS-Studio\data\obs-plugins\playout-247-plugin\ffmpeg.exe

OBS Studio danach komplett neu starten.
