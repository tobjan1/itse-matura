# Linux User- und Passwortspeicherung

## Benutzerverwaltung unter Linux

Benutzerdaten werden in zwei zentralen Dateien gespeichert:

### /etc/passwd

Enthält Basisinformationen zu jedem Benutzer. Format pro Zeile:

```
benutzername:x:UID:GID:Kommentar:Home-Verzeichnis:Shell
```

Beispiel:
```
tobi:x:1000:1000:Tobi,,,:/home/tobi:/bin/bash
```

- `x` im Passwort-Feld bedeutet: das Passwort-Hash liegt in `/etc/shadow`
- Früher stand der Hash direkt hier — für alle lesbar, daher wurde `/etc/shadow` eingeführt

### /etc/shadow

Enthält die Passwort-Hashes. Nur für root lesbar. Format:

```
benutzername:$id$salt$hash:letzte_änderung:min:max:warn:...
```

Beispiel:
```
tobi:$6$xyz123$abcdef....:19800:0:99999:7:::
```

- `$6$` = SHA-512 (aktuell empfohlen)
- `$5$` = SHA-256
- `$1$` = MD5 (veraltet, unsicher)
- Das `salt` ist ein zufälliger Zusatz, der verhindert, dass zwei Benutzer mit gleichem Passwort denselben Hash haben

## Ablauf der Passwortprüfung

1. Benutzer gibt Passwort ein
2. System liest den Salt aus `/etc/shadow`
3. Passwort + Salt werden gehashed
4. Ergebnis wird mit dem gespeicherten Hash verglichen
5. Bei Übereinstimmung: Login erfolgreich

## Wichtige Befehle

| Befehl | Funktion |
|--------|----------|
| `useradd benutzername` | Neuen Benutzer anlegen |
| `passwd benutzername` | Passwort setzen/ändern |
| `usermod -aG gruppe user` | Benutzer zur Gruppe hinzufügen |
| `cat /etc/passwd` | Benutzer auflisten |
| `sudo cat /etc/shadow` | Hashes anzeigen (root nötig) |

## Prüfungs-Hotspots

- Inhalt und Zweck von `/etc/passwd` und `/etc/shadow` erklären
- Warum wurde Shadow-Datei eingeführt? (Sicherheit: Hash nicht für alle lesbar)
- Was bedeutet `$6$salt$hash`? (Algorithmus-ID + Salt + Hash)
- Warum wird ein Salt verwendet? (Verhindert Rainbow-Table-Angriffe)
