# Generisches Prozessmodell

Bei der Neugestaltung von Prozessen innerhalb einer IT-Organisation dienen generische Prozessmodelle als Basis für eine konsistente Prozessbeschreibung. Sie stellen Prozesse auf abstrakter Ebene dar und legen fest, was in einer Prozessdefinition beschrieben werden muss.

Das Modell besteht aus **drei Ebenen**:
1. Prozesssteuerung
2. Prozess
3. Prozess-Enabler

## Ebene 1: Prozesssteuerung

Die Prozesssteuerung enthält das **Ziel** sowie wichtige **Erfolgsfaktoren** und **Kennzahlen**.

### Prozessziel

Das Prozessziel beschreibt, was dieser Prozess leisten soll: Warum gibt es diesen Prozess, und was kann als Ergebnis erwartet werden?

**Beispiel:** "Abgabe aller Arbeitsmaterialien und Zertifikate bei den entsprechenden Personen, damit alle unternehmensrelevanten Informationen und Gegenstände im Unternehmen bleiben — spätestens beim Austritt eines Mitarbeiters."

### Critical Success Factor (CSF) — Kritischer Erfolgsfaktor

Um den Prozess steuern zu können, werden CSFs definiert, die zur Erreichung des Prozesszieles beitragen. Ein CSF beschreibt eine Bedingung, die erfüllt sein muss, damit der Prozess erfolgreich ist.

### Key Performance Indicator (KPI) — Kennzahl

KPIs sind messbare Kennzahlen, mit denen überprüft wird, ob ein CSF erreicht wird.

**Beispiel CSF/KPI:**
- CSF: Die Verfügbarkeit des Online-Shops bleibt auch unter DDoS-Last erhalten.
- KPI: Die Ladezeiten überschreiten bei DDoS-Attacken mit X Abfragen/sec nicht 1000 ms.

| Begriff | Bedeutung | Beispiel |
|---------|-----------|---------|
| **Prozessziel** | Was soll der Prozess erreichen? | Mitarbeiter-Offboarding vollständig und fristgerecht |
| **CSF** | Welche Bedingung muss erfüllt sein? | Alle Zugänge werden bei Austritt deaktiviert |
| **KPI** | Wie wird Erfolg gemessen? | 100 % der Zugänge innerhalb von 24 h nach Austritt deaktiviert |

## Ebene 2: Prozess

Die zweite Ebene beschreibt den eigentlichen Prozessablauf: **Input/Trigger → Aktivitäten → Output**.

Ein Prozess ist ein System, das einen definierten Input zu einem definierten Output **transformiert**. Der Output ist vollständig vom Input abhängig.

| Element | Beschreibung |
|---------|-------------|
| **Input** | Was geht in den Prozess hinein? (Daten, Anfragen, Materialien) |
| **Trigger** | Welches Ereignis startet den Prozess? |
| **Aktivitäten** | Die einzelnen Schritte, die zum gewünschten Output führen |
| **Output** | Das spezifisch definierte Ergebnis des Prozesses |

Auch der Output muss spezifisch definiert werden — nicht nur "Ergebnis vorhanden", sondern was genau und in welcher Form.

## Ebene 3: Prozess-Enabler

Die dritte Ebene beschreibt die **Enabler** — also die Dinge, die es ermöglichen, einen Prozess zu betreiben. Das sind die **Ressourcen**, die zur Durchführung benötigt werden.

Drei Arten von Ressourcen:

| Art | Beispiele |
|-----|----------|
| **Technische Ressourcen** | Backup-System, Firewall, Monitoring-Tool |
| **Personen** | Entwickler, IT-Leitung, Geschäftsführung, Forensiker |
| **Fähigkeiten** | Überblick, Empathie, Entscheidungsfreude, Produkt-Know-how |

## Zusammenfassung: Die drei Ebenen

```
Ebene 1 — PROZESSSTEUERUNG
  └── Prozessziel (Warum existiert dieser Prozess?)
  └── CSF (Kritische Erfolgsfaktoren)
  └── KPI (Messbare Kennzahlen)

Ebene 2 — PROZESS
  └── Input / Trigger
  └── Aktivitäten
  └── Output

Ebene 3 — PROZESS-ENABLER
  └── Technische Ressourcen
  └── Personen
  └── Fähigkeiten
```

## Prüfungs-Hotspots

- Die drei Ebenen des generischen Prozessmodells nennen und erklären
- Unterschied CSF vs. KPI: CSF = Erfolgsbedingung, KPI = messbare Kennzahl dazu
- Prozess = Transformation von Input zu Output
- Enabler = Ressourcen (technisch, Personen, Fähigkeiten)
- Konkretes Beispiel für CSF/KPI nennen (DDoS, Ladezeiten unter 1000 ms)
