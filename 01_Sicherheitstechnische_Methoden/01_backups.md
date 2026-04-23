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

Eine Datensicherung ist weit mehr als das Kaufen eines Laufwerks und das Wechseln eines Bandes. Ohne vorab geklärte Regeln sind Backups zufällig, lückenhaft und im Ernstfall unbrauchbar. Das **Datensicherungskonzept** ist das schriftliche Dokument, in dem eine Organisation diese Regeln festlegt.

Es ist Teil des Informationssicherheits-Management-Systems (ISMS) und wird regelmäßig (meist jährlich) überprüft und angepasst.

### Ziele eines Datensicherungskonzepts

- Einheitliche, nachvollziehbare Backup-Strategie
- Klare Verantwortlichkeiten — im Ernstfall weiß jeder, wer was macht
- Einhaltung rechtlicher Vorgaben (DSGVO, Aufbewahrungspflichten in der Buchhaltung, etc.)
- Grundlage für die Wiederherstellung (Disaster Recovery)
- Regelmäßige Überprüfung der Sicherungen (sind sie wirklich wiederherstellbar?)

## Die 7 W-Fragen

Die 7 W-Fragen sind das Raster, nach dem ein Datensicherungskonzept aufgebaut wird. Jede Frage muss individuell für die jeweilige Organisation beantwortet werden — ein Datensicherungskonzept einer Bank sieht anders aus als das einer Schule.

| # | W-Frage | Inhalt |
|---|---------|--------|
| 1 | **WAS** | Welche Daten sollen gesichert werden? |
| 2 | **WANN** | Tagsüber, in der Nacht, online oder offline (bei Datenbanken)? |
| 3 | **WIE OFT** | Stündlich, täglich, wöchentlich, jährlich? |
| 4 | **WIE VIEL** | Wie viele verschiedene Sicherungen werden aufbewahrt? |
| 5 | **WER** | Wer trägt die Verantwortung für Sicherung und Kontrolle? |
| 6 | **WIE** | Welches Medium wird eingesetzt, welche Software? |
| 7 | **WO** | Wie ist die Aufbewahrung geregelt? |

### 1. WAS — welche Daten?

Nicht alle Daten sind gleich wichtig. Vorab wird klassifiziert:

- **Kritisch**: Datenbanken (CRM, ERP), Finanzbuchhaltung, Kundendaten, Verträge
- **Wichtig**: E-Mails, Fileserver-Dokumente, Konfigurationen von Servern
- **Nice-to-have**: Temporäre Arbeitsdateien, Caches, Logs
- **Nicht sichern**: Betriebssystem-Dateien, die man neu installieren kann; personenbezogene Daten nach Ablauf der Aufbewahrungsfrist (DSGVO)

### 2. WANN — Zeitpunkt und Zustand

- **Tagsüber**: Betrieb läuft, Backups können Performance beeinflussen; sinnvoll für inkrementelle Sicherungen kleiner Datenmengen
- **Nachts/am Wochenende**: Kein Benutzerbetrieb, Voll-Backups möglich, keine Konflikte mit aktiven Datenbank-Transaktionen
- **Online (hot backup)**: System läuft während der Sicherung weiter. Möglich z. B. mit Datenbank-Snapshots
- **Offline (cold backup)**: System/Datenbank wird gestoppt. Konsistent, aber verursacht Ausfallzeit

### 3. WIE OFT — Häufigkeit

Hängt direkt am **Recovery Point Objective (RPO)** — wie viel Datenverlust ist akzeptabel?

- Finanzsystem einer Bank: RPO praktisch 0 → kontinuierliche Replikation
- CRM einer Firma: RPO ca. 4 h → inkrementell alle paar Stunden
- Fileserver: RPO 1 Tag → tägliches inkrementelles Backup + wöchentliches Full
- Archivdaten: RPO 1 Woche oder länger

### 4. WIE VIEL — Anzahl der aufbewahrten Sicherungen

Es reicht nicht, nur die letzte Sicherung zu haben (Ransomware-Verschlüsselung wird sonst einfach mitgesichert). Klassische Rotationsschemata:

- **Großvater-Vater-Sohn (GVS)**: täglich (Sohn), wöchentlich (Vater), monatlich (Großvater). Z. B. 7 Tages- + 4 Wochen- + 12 Monats-Sicherungen
- **Türme von Hanoi**: komplexer, mehr Medien, längere Rückreichweite

### 5. WER — Verantwortung

- **Durchführung**: meist der IT-Betrieb / Administrator
- **Kontrolle**: **wichtig, dass Durchführung und Kontrolle getrennt sind** (Vier-Augen-Prinzip, Revisionssicherheit)
- **Zurückspielen (Restore)**: klar definieren, wer im Ernstfall zugreifen darf
- **Eskalation**: wer wird bei Problemen informiert?

### 6. WIE — Medium und Software

- **Medium**: Tape (LTO), HDD, SSD, NAS, Cloud-Storage (S3, Azure Blob)
- **Software**: Veeam, Bacula, Veritas NetBackup, ArcServe, BorgBackup, restic
- **Verschlüsselung**: Backups immer verschlüsselt speichern (AES-256)
- **Backup-Typ**: Full / differenziell / inkrementell (siehe oben)

### 7. WO — Aufbewahrungsort

- **Lokal (onsite)**: schneller Restore, aber bei Brand/Hochwasser/Ransomware mit verloren
- **Offsite**: zweites Rechenzentrum, Bankschließfach, Cloud — Schutz vor lokalen Katastrophen
- **3-2-1-Regel** (siehe oben): 3 Kopien, 2 Medien, 1 offsite
- **Aufbewahrungsdauer**: gesetzlich teils vorgegeben (z. B. Steuerunterlagen 7 Jahre in Österreich), teils aus Business-Sicht (CRM-Historie 3 Jahre)

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
- Ein beispielhaftes Konzept für eine kleine Firma skizzieren können
- Warum müssen Durchführung und Kontrolle getrennt sein?
- Warum ist ein Restore-Test wichtig?
