# Verfügbarkeitsberechnung

## Was ist Verfügbarkeit?

Verfügbarkeit (Availability) ist ein Maß dafür, wie lange ein System oder eine Komponente innerhalb eines Zeitraums betriebsbereit ist. Sie wird als Prozentwert angegeben.

```
Verfügbarkeit = (Betriebszeit) / (Betriebszeit + Ausfallzeit) × 100 %
```

**Beispiel**: Ein System läuft 8700 von 8760 Stunden im Jahr.  
Verfügbarkeit = 8700 / 8760 × 100 % ≈ 99,3 %

## Nine-Nines — Verfügbarkeitsklassen

| Verfügbarkeit | Ausfallzeit pro Jahr |
|---------------|----------------------|
| 99 % | ca. 3,65 Tage |
| 99,9 % (drei Neunen) | ca. 8,76 Stunden |
| 99,99 % (vier Neunen) | ca. 52,6 Minuten |
| 99,999 % (fünf Neunen) | ca. 5,26 Minuten |

## Serielle Schaltung (alle Komponenten notwendig)

Wenn Komponenten nacheinander geschaltet sind, muss jede funktionieren. Die Gesamtverfügbarkeit ist das Produkt der Einzelverfügbarkeiten:

```
V_gesamt = V₁ × V₂ × V₃ × ...
```

**Beispiel**: Drei Komponenten mit je 99 % Verfügbarkeit:  
V_gesamt = 0,99 × 0,99 × 0,99 ≈ 0,970 = 97 %

Die Gesamtverfügbarkeit sinkt mit jeder weiteren Komponente.

## Single Point of Failure (SPoF)

Eine Komponente, deren Ausfall den Ausfall des gesamten Systems verursacht, wird als Single Point of Failure bezeichnet. Typische Beispiele: ein einziger Netzwerk-Switch, ein einziger Server, eine einzige Stromleitung.

Gegenmaßnahme: Redundanz — jede kritische Komponente mindestens doppelt ausführen.

## Parallele Schaltung (Redundanz)

Bei parallelen Komponenten fällt das System nur aus, wenn alle gleichzeitig ausfallen:

```
V_gesamt = 1 - (1 - V₁) × (1 - V₂)
```

**Beispiel**: Zwei parallele Komponenten mit je 99 % Verfügbarkeit:  
V_gesamt = 1 - (0,01 × 0,01) = 1 - 0,0001 = 99,99 %

Redundanz erhöht die Verfügbarkeit erheblich.

## Prüfungs-Hotspots

- Formel für serielle und parallele Schaltung kennen und anwenden
- Single Point of Failure erklären und Beispiel nennen
- Verfügbarkeit aus Betriebsstunden berechnen
- "Vier Neunen" interpretieren können (99,99 % ≈ 52 min Ausfall/Jahr)
