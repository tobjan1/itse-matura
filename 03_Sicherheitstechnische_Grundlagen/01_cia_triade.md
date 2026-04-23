# CIA-Triade

Die CIA-Triade ist das grundlegende Schutzmodell der Informationssicherheit. Sie definiert drei Schutzziele, die bei jedem Sicherheitskonzept berücksichtigt werden müssen.

## Die drei Schutzziele

### Confidentiality (Vertraulichkeit)

Informationen dürfen nur für autorisierte Personen zugänglich sein.

- Umsetzung: Verschlüsselung, Zugriffskontrollen, Need-to-know-Prinzip
- Verletzung: Datenleak, unverschlüsselte Übertragung, unbefugter Zugriff

### Integrity (Integrität)

Daten dürfen nur von autorisierten Personen auf definierte Weise verändert werden. Unbemerkte Manipulation muss verhindert werden.

- Umsetzung: Digitale Signaturen, Hashing (SHA-256), MACs, Versionskontrolle
- Verletzung: Tampering, Man-in-the-Middle-Angriff, fehlerhafte Übertragung

### Availability (Verfügbarkeit)

Systeme und Daten müssen für autorisierte Benutzer jederzeit erreichbar sein.

- Umsetzung: Redundanz, Backups, DDoS-Schutz, Failover
- Verletzung: DDoS-Angriff, Hardware-Ausfall, Ransomware

## Zusammenhang mit Angriffen

| Angriff | Verletztes Schutzziel |
|---------|----------------------|
| Datenleak / Sniffing | Confidentiality |
| Man-in-the-Middle (Manipulation) | Integrity |
| DDoS | Availability |
| Ransomware | Availability (+ Confidentiality) |

## Erweiterung: Parkerian Hexad

Die CIA-Triade wurde von Donn Parker um drei weitere Schutzziele erweitert:

| Ziel | Beschreibung |
|------|-------------|
| **Possession / Control** | Physische Kontrolle über Daten/Medien, unabhängig von Vertraulichkeit |
| **Authenticity** | Echtheit und Herkunft von Daten ist verifizierbar |
| **Utility** | Daten müssen in einer nutzbaren Form vorliegen (z. B. kein Verlust des Entschlüsselungsschlüssels) |

## Erweiterung: AAA-Modell

Ergänzend zur CIA-Triade beschreibt das AAA-Modell den Zugriffssteuerungsprozess:

- **Authentication (Authentifizierung)**: Wer bist du? (Passwort, Biometrie, Token)
- **Authorization (Autorisierung)**: Was darfst du? (Berechtigungen, Rollen)
- **Accounting / Auditing**: Was hast du getan? (Logging, Protokollierung)

## Prüfungs-Hotspots

- CIA erklären und je ein Beispiel für Verletzung nennen
- Welches Schutzziel verletzt ein DDoS? (Availability)
- Welches Schutzziel verletzt ein Datenleak? (Confidentiality)
- CIA vs. AAA: Was ist der Unterschied?
