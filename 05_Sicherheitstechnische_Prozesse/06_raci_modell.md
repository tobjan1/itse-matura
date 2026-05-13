# RACI-Modell

Das RACI-Modell beschreibt Verantwortlichkeiten innerhalb von Prozessen. Es legt fest, welche Rollen an welchen Aufgaben beteiligt sind und in welcher Form.

**Wichtig:** Rollenbeschreibungen werden zwar häufig mit Stellenbeschreibungen verknüpft, sind aber **nicht** einer spezifischen Person fest zugeordnet. Mehrere Personen können dieselbe Rolle innehaben, und eine Person kann in verschiedenen Prozessen verschiedene RACI-Rollen haben.

## Die vier RACI-Rollen

| Buchstabe | Begriff | Bedeutung | Kommunikation |
|-----------|---------|-----------|---------------|
| **R** | **Responsible** | Verantwortlich für die **Durchführung** der Aufgabe (operativ: "wer macht's") | — |
| **A** | **Accountable** | Rechtlich oder kaufmännisch verantwortlich; der **Genehmiger** ("wer haftet") | — |
| **C** | **Consulted** | Fachleute, die um Rat gefragt werden oder beteiligt sind | Bidirektional (Dialog) |
| **I** | **Informed** | Erhält Informationen über Verlauf oder Ergebnis | Unidirektional (Info-Empfang) |

### Wichtige Regel (muss/kann):

| Rolle | Pflicht? | Anzahl pro Aufgabe |
|-------|----------|-------------------|
| **R** | **muss** vorhanden sein | genau **einer** |
| **A** | **muss** vorhanden sein | genau **einer** |
| **C** | kann vorhanden sein | **mehrere** möglich |
| **I** | kann vorhanden sein | **mehrere** möglich |

Jede Aufgabe in einer RACI-Matrix braucht zwingend genau einen R und genau einen A. C und I sind optional und können mehrfach besetzt sein.

**Hinweis zur Schreibweise:** In Folien und handschriftlichen Notizen taucht auch "Consultant" auf (Schreibfehler). Die korrekte Bezeichnung ist **Consulted**. Im allgemeinen Sprachgebrauch wird gelegentlich auch "Consulted" mit "Consulted party" oder verkürzt "Consultant" bezeichnet — gemeint ist aber immer die Rolle der zu befragenden Fachperson.

## Unterschied R vs. A

- **R (Responsible)** = führt die Aufgabe aus. Mehrere Personen können an einer Aufgabe "R" sein (z. B. zwei Techniker installieren gemeinsam), aber in einer klassischen RACI-Matrix ist pro Aufgabe **einer** definiert.
- **A (Accountable)** = trägt die Verantwortung und Konsequenzen. Muss eine einzige, klar benennbare Person sein — keine diffuse Verantwortung.

Der A genehmigt die Arbeit des R. Die Faustregel: "Wer wird gerufen, wenn es schiefgeht?" — das ist der A.

## Consulted vs. Informed

- **C (Consulted)**: Zweiseitiger Austausch. Die Person wird um ihre Einschätzung gefragt, gibt Feedback, und dieses Feedback fließt in die Aufgabe ein.
- **I (Informed)**: Einseitige Information. Die Person wird über das Ergebnis oder den Fortschritt informiert, aber ihr Feedback ändert nichts am Ablauf.

## Beispiel-RACI-Tabelle: Patch-Management

| Aufgabe | IT-Admin | IT-Leitung | Fachabt.-Leiter | CISO | Geschäftsführung |
|---------|----------|------------|-----------------|------|-----------------|
| Patches identifizieren & bewerten | R | A | C | C | I |
| Testumgebung vorbereiten | R | A | — | I | — |
| Genehmigung einholen | C | R | C | A | I |
| Patch in Produktion ausrollen | R | A | I | C | I |
| Dokumentation aktualisieren | R | A | — | I | — |
| Abschlussbericht erstellen | R | A | I | C | I |

*Jede Zeile hat genau einen R und einen A. C und I können fehlen oder mehrfach auftreten.*

## Warum RACI?

Ohne klar definierte Verantwortlichkeiten entstehen in der Praxis:
- Aufgaben, die niemand übernimmt ("wir dachten, der andere macht's")
- Entscheidungen, für die niemand zuständig ist
- Ineffizienz durch zu viele beteiligte Personen
- Fehlende Nachvollziehbarkeit im Audit

Das RACI-Modell schafft Klarheit für alle Beteiligten und ist ein zentrales Werkzeug im Prozessmanagement.

## Prüfungs-Hotspots

- RACI ausschreiben und jede Rolle erklären
- Muss/Kann-Regel: R und A = muss, jeweils einer; C und I = kann, mehrere möglich
- Unterschied Responsible vs. Accountable (operativ vs. haftend)
- Unterschied Consulted vs. Informed (bidirektional vs. unidirektional)
- Eine RACI-Tabelle für ein einfaches Beispiel erstellen oder analysieren können
- Rollenbeschreibungen sind nicht an Personen, sondern an Funktionen geknüpft
