# Richtlinien, Verfahren und Prozesse — Hierarchie

In der Informationssicherheit (und insbesondere in ISO 27001) gibt es eine dreistufige Hierarchie von Dokumenten. Die Begriffe werden häufig verwechselt — das Verständnis der Unterschiede ist prüfungsrelevant.

## Die drei Ebenen

### 1. Richtlinie (Policy) — WAS und WARUM

- **Strategische Ebene**, vom Management vorgegeben
- Legt fest, **was** erreicht werden soll und **warum** es wichtig ist
- Gibt Rahmen und Richtung vor, beschreibt aber nicht den konkreten Ablauf
- Gilt für die gesamte Organisation oder einen definierten Bereich
- Wird von der Geschäftsleitung oder dem CISO verantwortet

**Beispiel:** "Passwörter müssen sicher sein und regelmäßig gewechselt werden."

### 2. Verfahren (Procedure) — WIE genau

- **Operative Ebene**, konkrete Schritt-für-Schritt-Anweisung
- Beschreibt **wie** eine Aufgabe durchzuführen ist
- Bezieht sich auf eine spezifische Richtlinie und setzt diese um
- Kann Checklisten, Formulare oder Ablaufdiagramme enthalten

**Beispiel:** "Passwort über das Self-Service-Portal ändern, mindestens 12 Zeichen (Groß-/Kleinbuchstaben, Ziffern, Sonderzeichen), Pflichtänderung alle 90 Tage."

### 3. Prozess (Process) — vernetzte Aktivitäten mit Rollen

- **Ablaufebene**, verbindet mehrere Verfahren und Aktivitäten miteinander
- Beschreibt Input, Output, Aktivitäten und die beteiligten Rollen
- Oft sind mehrere Verfahren in einen übergeordneten Prozess eingebettet

**Beispiel:** "Identity & Access Management"-Prozess, der sowohl das Onboarding-, das Passwortmanagement- als auch das Offboarding-Verfahren umfasst.

## Vergleich in der Übersicht

| Ebene | Frage | Abstraktionsgrad | Verantwortung |
|-------|-------|-----------------|---------------|
| **Richtlinie (Policy)** | Was soll erreicht werden? Warum? | Hoch (strategisch) | Management / CISO |
| **Verfahren (Procedure)** | Wie wird eine Aufgabe ausgeführt? | Mittel (taktisch) | Fachbereich |
| **Prozess (Process)** | Welche vernetzten Aktivitäten führen zum Ziel? | Variabel | Prozessverantwortlicher |

## Beispiel: Passwort-Management

| Ebene | Inhalt |
|-------|--------|
| **Richtlinie** | "Alle Benutzerkonten sind durch starke Passwörter zu schützen und regelmäßig zu wechseln." |
| **Verfahren** | Schritt 1: Im Self-Service-Portal anmelden. Schritt 2: Menüpunkt "Passwort ändern" wählen. Schritt 3: Neues Passwort mit mind. 12 Zeichen setzen. Schritt 4: Änderung bestätigen und protokollieren. |
| **Prozess** | Identity Lifecycle Management: Onboarding (Konto anlegen) → Nutzung (Passwortpflege, Berechtigungsänderungen) → Offboarding (Konto deaktivieren/löschen) |

## Relevanz in ISO 27001

ISO 27001 verwendet diese Begriffe systematisch. Ein ISMS umfasst typischerweise:
- eine **Informationssicherheitsrichtlinie** (übergeordnetes Dokument, Abschnitt 5.2)
- themenspezifische **Richtlinien** (z. B. für Zugangskontrolle, Kryptografie)
- **Verfahren** für die operative Umsetzung
- **Prozesse**, die mehrere Verfahren und Rollen verbinden

Das korrekte Verständnis der Hierarchie ist wichtig, um Audits zu bestehen und Dokumente korrekt zuzuordnen.

## Prüfungs-Hotspots

- Die drei Ebenen nennen und den Unterschied erklären
- Richtlinie = WAS/WARUM; Verfahren = WIE; Prozess = vernetzte Aktivitäten mit Rollen
- Beispiel für jede Ebene nennen können (Passwort-Beispiel)
- ISO 27001 verwendet diese Hierarchie systematisch
- Richtlinie wird vom Management vorgegeben, Verfahren vom Fachbereich
