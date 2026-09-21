# World Empire – Spiel und echter Multiplayer-Worker

Das Spiel ist fertig gebaut und vollständig in worker.js eingebettet.
Es gibt keinen public-Ordner, keine npm-Installation und keinen lokalen Build.
wrangler.json richtet die Klasse EmpireRoom und den Raumspeicher ein.

## Auf dem iPhone veröffentlichen

1. ZIP in der Dateien-App entpacken.
2. In deinem GitHub-Konto ein privates Repository namens world-empire-online erstellen.
3. Über Add file → Upload files die vier entpackten Dateien hochladen und mit
   Commit changes speichern. worker.js und wrangler.json müssen direkt auf der
   obersten Ebene liegen. Die ZIP selbst nicht ins Repository hochladen.
4. Bei Cloudflare zu Workers & Pages → Create application gehen und die
   GitHub-/Repository-Verbindung auswählen. NICHT Upload static files wählen.
5. Zugriff auf dieses Repository erlauben und es auswählen.
6. Folgende Einstellungen verwenden:
   - Worker-/Projektname: world-empire-online
   - Produktionsbranch: main
   - Build command: leer lassen
   - Deploy command: npx --yes wrangler@4.135.0 deploy
   - Root directory: Repository-Hauptverzeichnis (Standard)
7. Deploy starten. Cloudflare veröffentlicht Spiel, Server und Raumspeicher.

Die neue workers.dev-Adresse ist gleichzeitig Spiel- und Serveradresse.
Privaten Raum erstellen und Einladungslink teilen. Keine Serveradresse eintragen.
GitHub und Cloudflare müssen von dir verbunden werden; keine Passwörter oder
API-Tokens in Chat oder Projektdateien eintragen.

## Warum der bisherige Upload blockiert wurde

Der Dialog Upload static files führt keine Worker-Konfiguration aus.
Das Entfernen der wrangler.json würde den Online-Server nicht einrichten.
Der Repository-Weg führt die Konfiguration auf Cloudflare aus, auch ohne PC.

## Prüfung

Diese Fassung wurde lokal geprüft: identische Spieloberfläche, zwei Spieler
über echte WebSockets, Spielstart, Würfeln, Wiederverbinden und Hostwechsel.
Zugriffe von fremden Origins werden abgewiesen.
Ein echter Deploy in deinem Cloudflare-Konto wurde noch nicht ausgeführt.

Cloudflare-Dokumentation:
https://developers.cloudflare.com/workers/ci-cd/builds/configuration/
https://developers.cloudflare.com/workers/ci-cd/builds/git-integration/github-integration/
