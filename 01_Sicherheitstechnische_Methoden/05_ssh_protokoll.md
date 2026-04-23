# SSH-Protokoll

## Was ist SSH?

SSH (Secure Shell) ist ein Netzwerkprotokoll für den gesicherten Fernzugriff auf Systeme. Es verschlüsselt die gesamte Kommunikation und ersetzt unsichere Protokolle wie Telnet oder rsh.

Standard-Port: **22**

## Aufbau der Verbindung (Handshake)

### Phase 1: TCP-Verbindung

Client und Server bauen zunächst eine normale TCP-Verbindung auf.

### Phase 2: Protokoll-Aushandlung

Server und Client tauschen ihre unterstützten SSH-Versionen aus (SSH-2.0 ist Standard).

### Phase 3: Schlüsselaustausch (Key Exchange)

1. Client und Server einigen sich auf Algorithmen: Schlüsselaustausch (z. B. Diffie-Hellman), symmetrische Verschlüsselung (z. B. AES-256), MAC (Message Authentication Code)
2. Über Diffie-Hellman wird ein gemeinsamer Session Key berechnet — ohne diesen über das Netz zu übertragen
3. Ab diesem Punkt ist die gesamte Kommunikation symmetrisch verschlüsselt

### Phase 4: Server-Authentifizierung

Der Server beweist seine Identität mit seinem Host Key (öffentlicher Schlüssel). Beim ersten Verbindungsaufbau fragt SSH:

```
The authenticity of host '192.168.1.1' can't be established.
ED25519 key fingerprint is SHA256:...
Are you sure you want to continue connecting (yes/no)?
```

Nach Bestätigung wird der Host Key in `~/.ssh/known_hosts` gespeichert. Bei künftigen Verbindungen wird dieser automatisch geprüft.

### Phase 5: Benutzer-Authentifizierung

Entweder per Passwort oder per Public Key (siehe `04_ssh_keys.md`).

## Verschlüsselung der Übertragung

Nach dem Handshake ist der Tunnel aufgebaut. Alle Daten (Befehle, Ausgaben, Dateiübertragungen) laufen verschlüsselt durch diesen Tunnel:

- **Symmetrische Verschlüsselung**: AES, ChaCha20 (schnell, für Massendaten)
- **MAC (Message Authentication Code)**: Sichert Integrität jedes Pakets (z. B. HMAC-SHA2)

## SSH-Dienste

Über das SSH-Protokoll können mehrere Dienste genutzt werden:

| Dienst | Beschreibung |
|--------|-------------|
| Remote Shell | Interaktive Kommandozeile auf dem Server |
| SCP | Einfache Dateiübertragung (Secure Copy) |
| SFTP | Vollwertiges Datei-Transfer-Protokoll |
| Port Forwarding | Tunnel für andere Protokolle durch SSH |

## Prüfungs-Hotspots

- Phasen des SSH-Handshakes erklären
- Was ist `known_hosts` und warum ist es wichtig?
- Welche Verschlüsselung kommt nach dem Handshake zum Einsatz? (symmetrisch)
- Unterschied SSH-Protokoll (Verbindungsaufbau) vs. SSH-Keys (Authentifizierung)
