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

## Prüfungs-Hotspots

- Unterschied inkrementell vs. differenziell
- 3-2-1-Regel erklären
- RPO und RTO definieren können
