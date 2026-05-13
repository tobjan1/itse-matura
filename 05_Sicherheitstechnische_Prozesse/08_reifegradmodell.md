# Reifegradmodell

## Zweck

Ein Reifegradmodell hilft dem Prozessmanagement bei der **Bewertung und Verbesserung von Prozessen**. Mit Reifegraden lässt sich die Leistung von Prozessen vergleichen.

In der Informationssicherheit dient das Reifegradmodell dazu, IT-Security-Prozesse zu prüfen und zu bewerten: Wie gut ist ein bestimmter Prozess in einem Unternehmen etabliert? Der Zustand jedes Prozesses wird mit einer Zahl von 0 bis 5 ausgedrückt.

**Im ISMS-Audit** verwendet der Auditor das Reifegradmodell, um den IST-Zustand zu erheben und den Handlungsbedarf zu identifizieren.

## Die sechs Reifegrade (0–5)

### Reifegrad 0: Nicht angewandt

**Management-Prozesse werden nicht angewandt.**
Ein erkennbarer Prozess existiert nicht im Unternehmen. Zwei mögliche Ursachen:
- (a) Der Prozess ist im Unternehmen nicht relevant.
- (b) Das Unternehmen hat den Bedarf bis dato nicht erkannt.

### Reifegrad 1: Ad-hoc und unorganisiert

**Prozesse sind ad-hoc und unorganisiert.**
Der jeweilige Prozess existiert. Der Prozessablauf basiert jedoch nicht auf standardisierten Abläufen und ist nicht organisiert. Die Aufgaben werden **individuell gelöst** — jede Person macht es auf ihre eigene Weise.

### Reifegrad 2: Regelmäßiges Muster, aber nicht dokumentiert

**Prozesse folgen einem regelmäßigen Muster.**
Der Unternehmensablauf folgt einem regelmäßigen Muster und kann von unterschiedlichen Personen innerhalb der Organisation durchgeführt werden. Es fehlen jedoch die formalen Beschreibungen: Der Prozess ist **nicht dokumentiert** und es fehlt die Definition der Verantwortlichkeiten.

### Reifegrad 3: Dokumentiert und kommuniziert

**Prozesse sind dokumentiert und kommuniziert.**
Prozesse mit diesem Reifegrad sind definiert, standardisiert, dokumentiert und an die betreffenden Personen innerhalb der Organisation **kommuniziert**. Es fehlt aber die Vorgabe der Verpflichtungen. Weiters gibt es über diese Prozesse kein Controlling, um die Qualität des betreffenden Prozesses weiter zu verbessern.

### Reifegrad 4: Gemonitort und gemessen

**Prozesse sind gemonitort und gemessen.**
Die Rahmenbedingungen für diese Prozesse sind so definiert, dass es möglich ist, sie zu **managen und zu monitoren**. Somit kann sichergestellt werden, dass die Abläufe eingehalten werden können. Dieser Reifegrad ermöglicht erstmals, **Probleme eines Prozesses zu erkennen** und Korrekturmaßnahmen einzuleiten.

### Reifegrad 5: Good Practices, automatisiert, kontinuierliche Verbesserung

**Good Practices werden angewandt und automatisiert.**
Diese Prozesse basieren auf dem Ergebnis der immerwährenden **kontinuierlichen Verbesserung**. Bei Prozessen mit diesem Reifegrad erfolgt eine andauernde Weiterentwicklung, um die Effektivität und die Qualität zu verbessern.

## Übersichtstabelle

| Reifegrad | Bezeichnung | Schlüsselmerkmal |
|-----------|-------------|-----------------|
| **0** | Nicht angewandt | Prozess existiert nicht |
| **1** | Ad-hoc und unorganisiert | Existiert, aber individuell und unstrukturiert |
| **2** | Regelmäßiges Muster, nicht dokumentiert | Wiederholbar, aber nicht formalisiert |
| **3** | Dokumentiert und kommuniziert | Definiert, standardisiert, bekannt |
| **4** | Gemonitort und gemessen | Kontrollierbar, Probleme erkennbar |
| **5** | Good Practices, automatisiert | KVP, Weiterentwicklung, automatisiert |

## SOLL-IST-Vergleich

Das Reifegradmodell wird für einen **SOLL-IST-Vergleich** eingesetzt:
- **IST**: Welchen Reifegrad hat ein bestimmter Prozess heute?
- **SOLL**: Welchen Reifegrad soll er in einem definierten Zeitraum erreichen?

Die Lücke zwischen IST und SOLL zeigt den **Handlungsbedarf** auf. Dieser Vergleich fließt direkt in die Plan-Phase des PDCA-Zyklus ein.

## Spinnendiagramm (Netzdiagramm)

Zur Visualisierung mehrerer Reifegrade gleichzeitig wird ein **Spinnendiagramm** (auch Netzdiagramm oder Radar-Chart) verwendet. Das Diagramm sieht aus wie ein Spinnennetz:

- Jede "Achse" des Spinnennetzes entspricht einem **Themenfeld** (z. B. Zugangskontrolle, Backup, Incident Management, Patch Management, Netzwerksicherheit).
- Der Abstand vom Mittelpunkt auf jeder Achse entspricht dem **Reifegrad** (0 = Mitte, 5 = Außenrand).
- Die verbundenen Punkte ergeben eine Fläche — ein gleichmäßiges Sechseck wäre ein ideales ISMS auf Reifegrad 5 in allen Bereichen; Einbuchtungen zeigen schwache Bereiche.

**Interpretation:**
- Bereiche mit niedrigem Reifegrad = besonderer **Handlungsbedarf**
- Das Diagramm ermöglicht auch Personen ohne Detailwissen (z. B. Geschäftsleitung), den Sicherheitsstatus auf einen Blick zu erfassen.
- Es unterstützt dabei, **Schwerpunkte für die Weiterentwicklung** des ISMS zu setzen.

Der Vorteil: Auch Stakeholder, die den Prozess nicht im Detail kennen, können die Effektivität und Qualität des ISMS beurteilen — das Spinnendiagramm macht Reifegrade visuell zugänglich.

## Bezug zum ISMS-Audit

Ein ISMS-Auditor verwendet das Reifegradmodell, um:
1. Den aktuellen IST-Stand zu erheben (pro Themenfeld einen Reifegrad vergeben)
2. Diesen mit dem SOLL zu vergleichen
3. Handlungsbedarf und Prioritäten abzuleiten
4. Über Jahre hinweg Fortschritte zu dokumentieren

Das Reifegradmodell muss **über Jahre hinweg** angewandt werden, um einen aussagekräftigen Blick auf die Qualitätsentwicklung des ISMS zu erhalten.

## Prüfungs-Hotspots

- Alle sechs Reifegrade (0–5) mit Bezeichnung und Kernmerkmal nennen
- Reifegrad 4 ist der erste, bei dem Probleme erkannt und Korrekturmaßnahmen eingeleitet werden können
- Reifegrad 5 = kontinuierliche Verbesserung + Automatisierung
- Spinnendiagramm: Was ist es, was zeigt es, wie wird es interpretiert?
- SOLL-IST-Vergleich erklären
- Wer verwendet das Reifegradmodell? (Auditor im ISMS-Audit)
- Zusammenhang mit PDCA: Reifegrad-Messung fließt in die Plan-Phase ein
