# Backups

Ein Backup ist eine Sicherungskopie von Daten, die im Fehlerfall (Hardware-Ausfall, Ransomware, versehentliches Löschen) die Wiederherstellung ermöglicht.

## Backup-Typen

| Typ | Was wird gesichert | Dauer | Wiederherstellung |
|-----|-------------------|-------|-------------------|
| Vollbackup (Full) | Alle Daten | Lange | Einfach (eine Sicherung) |
| Differenzielles Backup | Alle Änderungen seit dem letzten Full | Mittel | Full + letzte Differenz |
| Inkrementelles Backup | Nur Änderungen seit dem letzten Backup (egal welchem) | Kurz | Full + alle Inkremente der Reihe nach |

## 3-2-1-Regel

Die 3-2-1-Regel ist die Grundregel für eine zuverlässige Backup-Strategie:

- **3** Kopien der Daten (Original + 2 Backups)
- **2** verschiedene Speichermedien (z. B. Festplatte + Tape)
- **1** Kopie an einem anderen Ort (offsite, Cloud, externes Rechenzentrum)

## Recovery Point Objective (RPO) und Recovery Time Objective (RTO)

- **RPO**: Wie viel Datenverlust ist akzeptabel? (Zeitraum bis zum letzten Backup)
- **RTO**: Wie lange darf die Wiederherstellung dauern?

Beide Werte sind Teil des Business Continuity Plans.

## Backup-Medien

- **Festplatten (HDD/SSD)**: Schnell, aber anfällig für physische Schäden
- **Magnetbänder (Tape)**: Guenstig pro GB, langlebig, häufig für Archivierung
- **Cloud**: Ortsunabhängig, skalierbar, Abhängigkeit vom Anbieter
- **NAS (Network Attached Storage)**: Einfacher Netzwerkzugriff

## Gegenmaßnahmen / Best Practices

- Backups regelmäßig auf Wiederherstellbarkeit testen
- Backup-Daten ebenfalls verschlüsseln
- Zugang zu Backup-Systemen einschränken (Ransomware verschlüsselt auch erreichbare Backups)
- Backup-Logs überwachen


## Datensicherungskonzept

Eine Datensicherung ist weit mehr als das Kaufen eines Laufwerks und das Wechseln eines Bandes. Vorab müssen wichtige konzeptionelle Fragen geklärt werden — das Ergebnis ist das **Datensicherungskonzept**. Diese Fragen müssen individuell für den Anwendungszweck der jeweiligen Organisation (Firma, Behörde, etc.) definiert werden.

Ohne Konzept sind Backups zufällig, lückenhaft und im Ernstfall unbrauchbar. Das Konzept ist Teil des Informationssicherheits-Management-Systems (ISMS).

## Die 7 W-Fragen

| # | W-Frage | Inhalt |
|---|---------|--------|
| 1 | **WAS** | Welche Daten sollen gesichert werden? |
| 2 | **WANN** | Tagsüber, in der Nacht, online oder offline (bei Datenbanken)? |
| 3 | **WIE OFT** | Stündlich, täglich, wöchentlich, jährlich? |
| 4 | **WIE VIEL** | Wie viele verschiedene Sicherungen werden aufbewahrt? |
| 5 | **WER** | Wer trägt die Verantwortung für Sicherung und Kontrolle? |
| 6 | **WIE** | Welches Medium wird eingesetzt, welche Software? |
| 7 | **WO** | Wie ist die Aufbewahrung geregelt? |


## Beispiel: Datensicherungskonzept "HTL Muster GmbH"

Fiktive mittelständische Firma mit Fileserver, Mailserver, CRM-Datenbank, 50 Mitarbeiter.

| W-Frage | Antwort für HTL Muster GmbH |
|---------|---------------------------|
| **WAS** | CRM-Datenbank (kritisch), Exchange-Mailserver (kritisch), Fileserver (wichtig), AD-Konfiguration (kritisch). Keine Sicherung: Client-PCs (werden aus Image neu aufgesetzt) |
| **WANN** | Montag–Freitag jeweils 22:00–05:00 Uhr (Wartungsfenster); CRM als Online-Backup via SQL-Snapshot, alle anderen offline |
| **WIE OFT** | CRM: alle 2 Stunden inkrementell, täglich Voll; Exchange: täglich Voll; Fileserver: täglich inkrementell, Sonntags Voll; AD: täglich |
| **WIE VIEL** | Großvater-Vater-Sohn: 14 Tages-Sicherungen, 8 Wochen-Sicherungen, 24 Monats-Sicherungen, 7 Jahres-Sicherungen (Buchhaltung) |
| **WER** | Durchführung: IT-Admin Herr Schmidt; Kontrolle (Log-Review): IT-Leiterin Frau Müller; Restore-Berechtigung: nur Admin + Geschäftsführung; Eskalation: CIO |
| **WIE** | Veeam Backup & Replication auf NAS (Synology, AES-256 verschlüsselt) + wöchentlicher Offsite-Sync in Azure Blob Storage |
| **WO** | Primär: NAS im Serverraum (onsite); Sekundär: Azure (offsite, EU-Region Wien); Tapes mit Jahres-Sicherungen im Bankschließfach |

Zusätzlich: **quartalsweiser Restore-Test** — eine zufällige Sicherung wird auf einem Test-Server komplett wiederhergestellt und Funktionsfähigkeit geprüft. Ergebnis wird dokumentiert.

## Prüfungs-Hotspots

- Unterschied inkrementell vs. differenziell
- 3-2-1-Regel erklären
- RPO und RTO definieren können
- Was ist ein Datensicherungskonzept und warum ist es nötig?
- Die 7 W-Fragen aufzählen und je kurz erklären können (WAS, WANN, WIE OFT, WIE VIEL, WER, WIE, WO)
