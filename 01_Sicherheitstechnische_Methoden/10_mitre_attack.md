# MITRE ATT&CK

## Was ist MITRE ATT&CK?

MITRE ATT&CK ist eine weltweit zugängliche Wissensdatenbank zu Taktiken und Techniken von Angreifern, basierend auf Beobachtungen aus der Praxis. Sie dient als Grundlage für Bedrohungsmodelle und Methoden in der Cybersicherheitsbranche. Die Datenbank ist offen und kostenlos verfügbar.

Link: https://attack.mitre.org/

## Entstehung

MITRE ist eine US-amerikanische Non-Profit-Organisation. ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge) wurde aus realen Beobachtungen von Angriffen auf Windows-Systeme entwickelt und kontinuierlich erweitert.

## Aufbau: Matrizen

ATT&CK gibt es für drei Plattformen (Matrizen):

| Matrix | Zielbereich |
|--------|-------------|
| **Enterprise** | Unternehmensinfrastruktur: Windows, macOS, Linux, Cloud, Netzwerk |
| **Mobile** | Android und iOS Geräte |
| **ICS** | Industrial Control Systems — Industrie- und SCADA-Systeme |

## Hierarchie: Taktiken → Techniken → Sub-Techniken

### Taktiken
Taktiken beschreiben das *Warum* — das übergeordnete Ziel des Angreifers in einer Phase. Beispiele aus Enterprise:

- **Reconnaissance**: Informationen sammeln
- **Initial Access**: Erstzugang zum System erlangen
- **Execution**: Schadcode ausführen
- **Persistence**: Zugang auch nach Neustart sichern
- **Privilege Escalation**: Höhere Rechte erlangen
- **Credential Access**: Zugangsdaten stehlen
- **Lateral Movement**: Sich im Netzwerk ausbreiten
- **Exfiltration**: Daten stehlen
- **Impact**: System stören, verschlüsseln, zerstören

### Techniken
Techniken beschreiben das *Wie* — die konkrete Methode des Angreifers. Jede Technik hat eine ID (z. B. T1566 = Phishing).

Eine Technik kann in mehreren Taktiken angewendet werden.

### Pro Technik gibt es:
- **Examples**: Bekannte Malware/Gruppen, die diese Technik nutzen
- **Mitigations**: Empfohlene Gegenmaßnahmen
- **Detection**: Hinweise zur Erkennung
- **References**: Quellen und Berichte

## Navigation

Die Matrix wird als Tabelle dargestellt: Spalten = Taktiken, Zellen = Techniken. Der ATT&CK Navigator ermöglicht das Einfärben und Filtern von Techniken, um z. B. die eigene Abdeckung durch Sicherheitsmaßnahmen darzustellen.

## Wichtig: Reihenfolge ist nicht zwingend

Die Taktiken müssen nicht nacheinander durchlaufen werden. Ein Angreifer kann Phasen überspringen, wenn er sein Ziel (Impact) auf anderem Weg erreicht.

## Prüfungs-Hotspots

- Was ist MITRE ATT&CK und wozu dient es?
- Welche drei Matrizen gibt es? (Enterprise, Mobile, ICS)
- Aufbau: Taktik → Technik erklären
- Was findet man bei einer Technik? (Examples, Mitigations, Detection, References)
- Kann ein Angreifer Taktiken überspringen? (Ja)
