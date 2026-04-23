# SSH Keys

## Public/Private Key Verfahren bei SSH

SSH (Secure Shell) unterstützt neben der Passwort-Authentifizierung auch die Authentifizierung mittels asymmetrischem Schlüsselpaar.

- **Private Key**: Verbleibt ausschließlich auf dem Client-Rechner, darf niemals weitergegeben werden
- **Public Key**: Wird auf dem Server hinterlegt (in `~/.ssh/authorized_keys`)

## Ablauf der Key-Authentifizierung

1. Client sendet Login-Anfrage mit dem Public Key
2. Server prüft, ob der Public Key in `authorized_keys` eingetragen ist
3. Server sendet eine zufällige Challenge (verschlüsselt mit dem Public Key)
4. Client entschlüsselt die Challenge mit dem Private Key und sendet sie zurück
5. Server verifiziert die Antwort — bei Erfolg ist die Authentifizierung abgeschlossen

Der Private Key verlässt dabei nie den Client-Rechner.

## Keys generieren und einrichten

```bash
# Key-Paar generieren (Standard: RSA, empfohlen: ed25519)
ssh-keygen -t ed25519 -C "kommentar"

# Public Key zum Server kopieren
ssh-copy-id benutzer@server

# Alternativ manuell
cat ~/.ssh/id_ed25519.pub >> ~/.ssh/authorized_keys  # auf dem Server
```

Dateien:
- `~/.ssh/id_ed25519` — Private Key (Rechte: 600)
- `~/.ssh/id_ed25519.pub` — Public Key
- `~/.ssh/authorized_keys` — hinterlegte Public Keys auf dem Server

## Vorteile gegenüber Passwort-Login

- Kein Passwort über das Netz übertragen
- Resistent gegen Brute-Force-Angriffe (kein erratbares Passwort)
- Private Key kann mit einer Passphrase zusätzlich geschützt werden

## Key Logging

Key Logging bezeichnet das heimliche Aufzeichnen von Tastatureingaben. Bei SSH-Passwort-Authentifizierung kann ein Keylogger das Passwort abgreifen. Bei Key-Authentifizierung nützt das dem Angreifer nichts, solange der Private Key nicht direkt entwendet wird.

## Passwort-Login deaktivieren

In `/etc/ssh/sshd_config` auf dem Server:

```
PasswordAuthentication no
PubkeyAuthentication yes
```

Danach: `sudo systemctl restart sshd`

## Prüfungs-Hotspots

- Unterschied Public Key vs. Private Key bei SSH
- Warum ist Key-Auth sicherer als Passwort?
- Was ist Keylogging, und warum schützt Key-Auth davor besser?
- Wo wird der Public Key auf dem Server hinterlegt?
