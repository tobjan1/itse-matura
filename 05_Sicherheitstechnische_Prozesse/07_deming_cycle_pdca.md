# Deming-Cycle / PDCA

## Hintergrund und Warum

Es reicht nicht, ein ISMS einmal aufzusetzen und dann anzunehmen, dass alles passt. Das gesamte ISMS unterliegt einer Dynamik: geänderte Rahmenbedingungen, neue Bedrohungen, neue Gesetze — all das erfordert eine kontinuierliche Weiterentwicklung.

**ISO/IEC 27001 fordert ausdrücklich kontinuierliche Verbesserung** als elementaren Bestandteil. Das Werkzeug dafür ist der **Deming-Cycle**, auch bekannt als **PDCA-Methodik** (Plan-Do-Check-Act) oder **KVP** (Kontinuierlicher Verbesserungsprozess).

**William Edwards Deming (1900–1993)** gilt als Pionier auf dem Gebiet des prozessorientierten Qualitätsmanagements und ist Namensgeber dieser Methodik.

## Das Rad-Bild

Die vier Phasen bilden ein Rad, das sich in **ständiger Vorwärtsbewegung** befindet. Jede Umdrehung führt zu einer **höheren Reife und Qualität**. Was geplant wird, muss umgesetzt werden. Was umgesetzt wurde, muss überprüft und gemessen werden. Was gemessen wurde, wird verbessert — und dann beginnt der Zyklus neu.

```
        PLAN
       /    \
      /      \
    ACT      DO
      \      /
       \    /
        CHECK
```

Der Zyklus läuft endlos: P → D → C → A → P → D → C → A → ...

Die Methodik ist so generisch, dass sie sich auf nahezu jedes Betrachtungsobjekt anwenden lässt: auf das gesamte ISMS, einzelne Prozesse, Verfahren oder konkrete Maßnahmen.

---

## Phase 1: Plan (Planen)

**ISO/IEC 27001 Abschnitt 6**

### Wann wird geplant?
- Noch nicht existierendes ISMS (Neuaufbau)
- Anpassung eines bestehenden ISMS

### Inhalt der Planungsphase
- Neue oder geänderte Bestandteile des ISMS werden geplant
- Das Ergebnis der Planung wird **dokumentiert**
- Klare Ziele und Zielvorgaben (**SMART**, siehe Datei 04)

### Was wird geplant?
1. **Ziele**: Was soll erreicht werden? (Beispiel: Reduzierung der Eintrittswahrscheinlichkeit von Risiken)
2. **Ressourcen**: Personal, Budget, andere laufende Projekte, die Personal binden
3. **Zeitlicher Ablauf**: Zeitraum der Umsetzung, Meilensteine, in denen Teile des großen Ziels abgeschlossen sind
4. **Umsetzung durchdenken**: Grobe Definition, wie die Umsetzung erfolgen kann (z. B. Bestellungen und Lieferzeiten, Urlaube, Produkt-Know-how)

### Beispiel
Geplant ist die **Erhöhung der Informationssicherheit**:
- Ziel: Reduzierung der Eintrittswahrscheinlichkeit von Risiken
- Ressourcen: IT-Personal (2 FTE), Budget 80.000 Euro, kein Überschneidung mit laufendem ERP-Projekt
- Zeitplan: Umsetzung in Q3, Meilensteine monatlich
- Umsetzungsidee: Redundante Router und Switches — Lieferzeiten bereits in Planung berücksichtigen

---

## Phase 2: Do (Umsetzen)

**ISO/IEC 27001 Abschnitte 7 + 8**

### Inhalt der Umsetzungsphase
Die geplanten Maßnahmen werden **verwirklicht und gesteuert**:
- Budgets müssen bereitgestellt und abrufbar sein (Personalkosten, Rechnungen, etc.)
- Es gibt **verantwortliche Personen** für jede Aufgabe
- **Aufzeichnungen** in sinnvollem Maße (nicht alles dokumentieren, aber das Wesentliche)

### Beispiel: Installation redundanter Router und Switches

| Schritt | Beteiligte |
|---------|-----------|
| Auswahl und Bestellung der neuen Geräte | IT Person A + Einkauf Person B |
| Bestandsaufnahme Patchpanels in den Technikräumen | IT Person B |
| Sicherung und Aktualisierung der bestehenden Konfigurationsdokumentation | IT Person A |
| SW-Update und Konfiguration der neuen Geräte | IT Person A + B |
| Probebetrieb in nicht kritischer Testumgebung | IT Person B + Fachabteilung Person C |
| **Meilenstein 1** | |
| Veröffentlichung "Wartungsfenster für ..." | IT Person A |
| Einbau der ersten Geräte, Patchen und Umstellung auf neue Geräte für Bereich A | IT Person B |
| Probebetrieb und Funktionscheck | IT Person A + B + Fachabteilung Person D |
| **Meilenstein 2** | |
| Umstellung der restlichen Komponenten in den anderen Bereichen | IT Person A + B + Fachabteilung D, E, F |
| Finale Dokumentation (Konfiguration, Patchpanels, etc.) | IT Person A + B |
| **Meilenstein 3** | |

---

## Phase 3: Check (Überprüfen)

**Phase der Überwachung, Messung und Überprüfung**

Es können nur Ziele geprüft werden, die in der Planungsphase klar definiert wurden. Die Check-Phase hat **drei Aspekte**:

### 3.1 Zielerreichung

Wurden die in der Plan-Phase definierten Ziele erreicht?

Zwei Arten von Messungen:

| Art | Beschreibung |
|-----|-------------|
| **Quantitative Ziele** | Können mit Zahlen belegt/geprüft werden (z. B. Verfügbarkeit 99,99 %) |
| **Qualitative Ziele** | Sind meist nur indirekt prüfbar (z. B. Nutzerzufriedenheit, Image, UX) |

**Beispiel — Messungen nach Router/Switch-Installation:**
- Verfügbarkeit ist auf 99,99 % gestiegen
- Packet Loss, Jitter, Delay zumindest gleich oder um 10 % verbessert
- Updates sind ohne Downtime bei redundanter Verkabelung möglich
- Konfigurationsänderungen erfordern keine Nacharbeit aufgrund von Folgefehlern
- Langfristig: Hardware-Tausch um 2 Jahre verlängert
- Trotz redundanter Ausführung Anzahl der Geräte nur um 30 % erhöht (durch mehr VLANs)
- Durch neue energiesparende Geräte nur 10 % mehr Stromverbrauch

### 3.2 Konformität

Wurden Prozesse, Verfahren und Maßnahmen **eingehalten oder umgesetzt**?

Ob das Ziel erreicht wurde, ist in diesem Aspekt irrelevant — hier geht es nur darum, ob der definierte Ablauf befolgt wurde.

**Beispiel — Externe Besucher in der Firma:**
Vorgeschriebene Prozedur: zu erwartende Personen beim Empfang anmelden → Empfang macht Sicherheitsunterweisung und Eintragung in Besucherliste → Person bekommt Besucherausweis → Mitarbeiter holt Person beim Empfang ab → Mitarbeiter begleitet Person im gesamten Gebäude → Abmeldung beim Empfang → Abgabe Besucherausweis → Austragung aus Besucherliste → Person verlässt Gebäude.

Konformitätsprüfung: Wurden **alle** Schritte genau eingehalten?

### 3.3 Effektivität

Wurde das **tatsächliche Ziel** erreicht? Hat der Prozess/die Maßnahme den gewünschten Effekt erzielt?

**Beispiel — Externe Besucher:**
Der konforme Ablauf sagt noch nicht aus, ob das Ziel erreicht wurde. Das eigentliche Ziel ist: **unbefugte Personen laufen nicht unbeaufsichtigt herum**. Die Effektivitätsprüfung bewertet, ob dieses Ziel tatsächlich erreicht wurde — unabhängig davon, ob der Prozess formal eingehalten wurde.

### 3.4 Effizienz

Wird das Ziel mit **optimalen Ressourceneinsatz** erreicht?

- Effizienz = Wirkungsgrad
- Ressourcen: Personal, Finanzmittel, Rohstoffe, Zeit

**Beispiel — Router/Switches:**
Nicht alle Netze müssen mit eigenen Switches ausgestattet werden. Bestehende Netze können vereinfacht werden, indem VLANs konfiguriert werden, wo vorher eigene Switches waren — gleiche Wirkung, weniger Hardware.

---

## Phase 4: Act (Handeln / Verbessern)

**ISO/IEC 27001 Abschnitt 10**

### Inhalt

Die Ergebnisse aus der Check-Phase sind der wichtigste Input für die Act-Phase. Hier werden **Verbesserungsmaßnahmen** aufgegriffen.

**Zwei Arten von Verbesserungsmaßnahmen:**

| Art | Bedeutung |
|-----|-----------|
| **Korrigierende Maßnahmen** | Reaktiv — auf ein bereits eingetretenes Problem reagieren |
| **Vorbeugende Maßnahmen** | Proaktiv — ein mögliches Problem verhindern, bevor es eintritt |

### Wichtig: Priorisierung erst in der nächsten Plan-Phase

In der Act-Phase entstehen viele neue Arbeitspakete. Diese haben zunächst **alle dieselbe Wertigkeit** — es gibt noch keine Priorisierung. Die tatsächliche Priorisierung und Planung der Umsetzung erfolgt erst wieder in der nächsten **Plan-Phase**.

### Beispiele

**Beispiel 1 — Router/Switches (korrigierend):**
Während der Installation wurden viele ungepatchte Kabel in den Patchpanels entdeckt. Diese müssen nachverfolgt, beschriftet oder entfernt werden.

**Beispiel 2 — Externe Besucher (vorbeugend):**
Bauarbeiter sind schwer jederzeit zu kontrollieren. Unter folgenden Voraussetzungen dürfen sie sich ohne Begleitung bewegen: Ansprechperson definiert, eindeutige Firmenbekleidung und Besucherausweis, eigener Chip für nur definierte Bereiche, unterzeichnete Verschwiegenheitserklärung.

---

## Zusammenfassung: PDCA auf einen Blick

| Phase | ISO 27001 | Kernfrage | Ergebnis |
|-------|-----------|-----------|---------|
| **Plan** | Abschnitt 6 | Was soll wie und bis wann erreicht werden? | Dokumentierter Plan mit SMART-Zielen |
| **Do** | Abschnitt 7+8 | Wie wird der Plan umgesetzt? | Umgesetzte Maßnahmen mit Aufzeichnungen |
| **Check** | — | Wurde das Ziel erreicht? Konform? Effektiv? Effizient? | Messergebnisse, Abweichungen |
| **Act** | Abschnitt 10 | Was muss verbessert werden? | Liste von Verbesserungsmaßnahmen |

---

## Prüfungs-Hotspots

- PDCA ausschreiben und jede Phase erklären
- William Edwards Deming (1900–1993) als Namensgeber
- ISO 27001 Abschnitte zuordnen: Plan = 6, Do = 7+8, Act = 10
- **Check hat drei Aspekte**: Zielerreichung, Konformität, Effektivität (+ Effizienz als vierter)
- Unterschied Konformität vs. Effektivität erklären (Ablauf eingehalten vs. Ziel erreicht)
- Effizienz = Wirkungsgrad, optimaler Ressourceneinsatz
- Zwei Arten von Verbesserungsmaßnahmen: korrigierend (reaktiv) vs. vorbeugend (proaktiv)
- Priorisierung der Act-Maßnahmen erfolgt in der nächsten Plan-Phase
- PDCA ist für das gesamte ISMS, aber auch für einzelne Prozesse/Maßnahmen anwendbar
